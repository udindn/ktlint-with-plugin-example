**instalasi**

Buka build.gradle.kts proyek root Anda dan tambahkan plugin dari [jeremymailen/kotlinter-gradle](https://github.com/jeremymailen/kotlinter-gradle)

```
plugins {
    id("org.jmailen.kotlinter") version "2.1.1"
}
```

kemudian atur aturan Ktlint

```
kotlinter {
        ignoreFailures = false
        indentSize = 4
        continuationIndentSize = 4
        reporters = ['json']
        experimentalRules = false
        fileBatchSize = 30
    }
```

tambahkan ini juga sehingga Ktlint dapat memeriksa semua sub proyek

```
allprojects {
    repositories {
        google()
        jcenter()
        maven { url 'https://jitpack.io' }
    }
    apply plugin: "org.jmailen.kotlinter"
}
```

untuk lebih detail, Anda bisa lihat di bawah ini

```
buildscript {
    ext.kotlin_version = '1.3.50'
    repositories {
        google()
        jcenter()
        
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.5.3'
        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files
    }
}

plugins {
    id("org.jmailen.kotlinter") version "2.1.1"
}

allprojects {
    repositories {
        google()
        jcenter()
        maven { url 'https://jitpack.io' }
    }
    apply plugin: "org.jmailen.kotlinter"

    kotlinter {
        ignoreFailures = false
        indentSize = 4
        continuationIndentSize = 4
        reporters = ['json']
        experimentalRules = false
        fileBatchSize = 30
    }
}

task clean(type: Delete) {
    delete rootProject.buildDir
}
```

Untuk dokumentasi lengkap kustomisasi aturan, editconfig dan lain-lain, lihat di [github jeremymailen/kotlinter-gradle](https://github.com/jeremymailen/kotlinter-gradle)
