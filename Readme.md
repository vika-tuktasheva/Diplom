<h1 align="center">Документация</h1>

* #### [План автоматизации тестирования](https://github.com/vika-tuktasheva/diplom/blob/main/docs/plan.md)
* #### [Отчет по итогам автоматизированного тестирования ](https://github.com/vika-tuktasheva/diplom/blob/main/docs/report.md)

<h1 align="center">Процедура запуска авто-тестов</h1>

## Подготовка среды перед тестированием:

**1.** Запустить Docker Desktop

**2.** В терминале запустить контейнеры с помощью команды:

    docker-compose up -d

**3.** Запустить целевой веб-сервис командой:

     для mySQL: 
    java "-Dspring.datasource.url=jdbc:mysql://localhost:3306/app" -jar artifacts/aqa-shop.jar

     для postgresgl:
     java "-Dspring.datasource.url=jdbc:postgresql://localhost:5432/app" -jar artifacts/aqa-shop.jar

# Процедура запуска авто-тестов:

**1.** Во втором терминале запустить тесты:

    для mySQL:
    ./gradlew clean test "-Ddb.url=jdbc:mysql://localhost:3306/app"

    для postgresgl: 
    ./gradlew clean test "-Ddb.url=jdbc:postgresql://localhost:5432/app"

**2.** Создать отчёт Allure и открыть в браузере:

    ./gradlew allureServe

# Действия после завершения авто-тестов:

**1.** Для завершения работы allureServe выполнить команду:

    Ctrl+C

**2.** Для остановки работы контейнеров выполнить команду:

    docker-compose down