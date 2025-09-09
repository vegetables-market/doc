Spring Boot: 3.5.4
Java: 21
Kotlin: 1.9.25
Tailwind CSS: 4.1.12
TypeScript: 5.9.2
その他はpackage.jsonを参照...

plugins {
	kotlin("jvm") version "2.2.10"
	kotlin("plugin.spring") version "2.2.10"
	id("org.springframework.boot") version "3.5.4"
	id("io.spring.dependency-management") version "1.1.7"
}

group = "com.example"
version = "0.0.1-SNAPSHOT"
description = "myapp"

java {
	toolchain {
		languageVersion = JavaLanguageVersion.of(21)
	}
}

repositories {
	mavenCentral()
}

dependencies {
	implementation("org.springframework.boot:spring-boot-starter-thymeleaf")
    implementation ("nz.net.ultraq.thymeleaf:thymeleaf-layout-dialect")
	implementation("org.springframework.boot:spring-boot-starter-web")
	implementation("com.fasterxml.jackson.module:jackson-module-kotlin")
	implementation("org.jetbrains.kotlin:kotlin-reflect")
	developmentOnly("org.springframework.boot:spring-boot-devtools")
	testImplementation("org.springframework.boot:spring-boot-starter-test")
	testImplementation("org.jetbrains.kotlin:kotlin-test-junit5")
	testRuntimeOnly("org.junit.platform:junit-platform-launcher")


kotlin {
	compilerOptions {
		freeCompilerArgs.addAll("-Xjsr305=strict")
    // Security crypto (BCrypt)
    implementation("org.springframework.security:spring-security-crypto")

    // TOTP / QR 生成用ライブラリ
    implementation("com.eatthepath:otp-java:1.0.0")
    implementation("commons-codec:commons-codec:1.15")
    implementation("com.google.zxing:core:3.5.0")
    implementation("com.google.zxing:javase:3.5.0")
}
	}
}

tasks.withType<Test> {
	useJUnitPlatform()
}


{
  "name": "myapp",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build:css": "postcss ./src/main/resources/static/css/input.css -o ./src/main/resources/static/css/output.css",
    "build:ts": "tsc",
    "build": "npm run build:css && npm run build:ts",
    "watch:css": "postcss ./src/main/resources/static/css/input.css -o ./src/main/resources/static/css/output.css --watch",
    "watch:ts": "tsc --watch",
    "watch": "npm-run-all --parallel watch:css watch:ts",
    "format": "prettier --write .",
    "check-format": "prettier --check .",
    "lint": "eslint . --ext .ts"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "type": "module",
  "devDependencies": {
    "@tailwindcss/postcss": "^4.1.12",
    "@typescript-eslint/eslint-plugin": "^8.40.0",
    "autoprefixer": "^10.4.21",
    "eslint": "^9.33.0",
    "eslint-config-prettier": "^10.1.8",
    "npm-run-all": "^4.1.5",
    "postcss": "^8.5.6",
    "postcss-cli": "^11.0.1",
    "prettier": "^3.6.2",
    "prettier-plugin-tailwindcss": "^0.6.14",
    "tailwindcss": "^4.1.12",
    "typescript": "^5.9.2"
  }
}
