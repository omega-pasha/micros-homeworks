# Домашнее задание к занятию "Микросервисы: подходы"

Вы работаете в крупной компанию, которая строит систему на основе микросервисной архитектуры.
Вам как DevOps специалисту необходимо выдвинуть предложение по организации инфраструктуры, для разработки и эксплуатации.


## Задача 1: Обеспечить разработку

Предложите решение для обеспечения процесса разработки: хранение исходного кода, непрерывная интеграция и непрерывная поставка. 
Решение может состоять из одного или нескольких программных продуктов и должно описывать способы и принципы их взаимодействия.

Решение должно соответствовать следующим требованиям:
- Облачная система;
- Система контроля версий Git;
- Репозиторий на каждый сервис;
- Запуск сборки по событию из системы контроля версий;
- Запуск сборки по кнопке с указанием параметров;
- Возможность привязать настройки к каждой сборке;
- Возможность создания шаблонов для различных конфигураций сборок;
- Возможность безопасного хранения секретных данных: пароли, ключи доступа;
- Несколько конфигураций для сборки из одного репозитория;
- Кастомные шаги при сборке;
- Собственные докер образы для сборки проектов;
- Возможность развернуть агентов сборки на собственных серверах;
- Возможность параллельного запуска нескольких сборок;
- Возможность параллельного запуска тестов;

Обоснуйте свой выбор.

## Ответ

Для обеспечения процесса разработки, рекомендуется использовать для храния исходного кода GitLab, а для непрерывной интеграции и доставки - Gitlab CI/CD.

Основные причины использования GitLab и GitLab CI/CD:

* Gitlab имеет удобный и понятный веб-интерфейс
* GitLab CI/CD легко интегрируется с Git-репозиторием и имеет интуитивно понятный интерфейс, который делает настройку и использование простым.
* GitLab CI/CD позволяет создавать, тестировать и поставлять код автоматически при каждом изменении в репозитории, что уменьшает время и усилия, затрачиваемые на ручное тестирование и поставку кода.
* Gitlab имеет средства управления правами доступа. GitLab позволяет настраивать права доступа к проектам и репозиториям, контролируя, кто может просматривать, изменять или удалять данные. Это улучшает безопасность и защищает данные от несанкционированного доступа.
* В GitLab есть Container Registry, в котором можно хранить собственные докер образы для сборки проектов.
* GitLab CI/CD имеет множество инструментов для безопасного хранения секретных данных, включая переменные окружения и файлы конфигурации.
* GitLab CI/CD имеет возможность развернуть агенты сборки на собственных серверах, что позволяет гибко настраивать среду для сборки и тестирования проектов.
* GitLab CI/CD позволяет параллельный запуск нескольких сборок и тестов, что ускоряет процесс разработки.


В целом, GitLab CI/CD позволяет создавать и поддерживать сложные проекты с множеством конфигураций, безопасно хранить секретные данные, и быстро и гибко настраивать сборку и тестирование проекта.

## Задача 2: Логи

Предложите решение для обеспечения сбора и анализа логов сервисов в микросервисной архитектуре.
Решение может состоять из одного или нескольких программных продуктов и должно описывать способы и принципы их взаимодействия.

Решение должно соответствовать следующим требованиям:
- Сбор логов в центральное хранилище со всех хостов обслуживающих систему;
- Минимальные требования к приложениям, сбор логов из stdout;
- Гарантированная доставка логов до центрального хранилища;
- Обеспечение поиска и фильтрации по записям логов;
- Обеспечение пользовательского интерфейса с возможностью предоставления доступа разработчикам для поиска по записям логов;
- Возможность дать ссылку на сохраненный поиск по записям логов;

Обоснуйте свой выбор.

## Ответ

Для решения задачи по сбору и анализу логов сервисов в микросервисной архитектуре можно использовать ELK-стек (Elasticsearch, Logstash, Kibana).

* Elasticsearch является распределенным поисковым и аналитическим движком, который обеспечивает быстрый и удобный поиск и агрегацию данных. Он позволяет хранить, индексировать и искать большие объемы данных, в том числе логи сервисов.

* Logstash – это система сбора и обработки логов. Он обеспечивает возможность сбора и агрегации логов со всех хостов обслуживающих систему, а также гарантированную доставку логов до центрального хранилища. Logstash умеет принимать логи из различных источников, обрабатывать их и отправлять в Elasticsearch.

* Kibana – это веб-интерфейс для Elasticsearch, который обеспечивает удобный доступ к данным и инструменты для их анализа и визуализации. С помощью Kibana можно выполнять поиск и фильтрацию по записям логов, а также создавать пользовательские дашборды для мониторинга состояния сервисов и отслеживания проблем.

Для минимальных требований к приложениям можно использовать стандартный вывод в stdout, который может быть легко обработан и перенаправлен в Logstash.

Также в ELK-стеке имеется возможность сохранения ссылок на запросы и сохраненные поиски, что позволяет быстро обмениваться информацией между разработчиками.


## Задача 3: Мониторинг

Предложите решение для обеспечения сбора и анализа состояния хостов и сервисов в микросервисной архитектуре.
Решение может состоять из одного или нескольких программных продуктов и должно описывать способы и принципы их взаимодействия.

Решение должно соответствовать следующим требованиям:
- Сбор метрик со всех хостов, обслуживающих систему;
- Сбор метрик состояния ресурсов хостов: CPU, RAM, HDD, Network;
- Сбор метрик потребляемых ресурсов для каждого сервиса: CPU, RAM, HDD, Network;
- Сбор метрик, специфичных для каждого сервиса;
- Пользовательский интерфейс с возможностью делать запросы и агрегировать информацию;
- Пользовательский интерфейс с возможность настраивать различные панели для отслеживания состояния системы;

Обоснуйте свой выбор.

## Ответ

Для решения задачи сбора и анализа состояния хостов и сервисов в микросервисной архитектуре можно использовать систему мониторинга Prometheus в сочетании с графическим интерфейсом Grafana.

Prometheus - это система мониторинга с открытым исходным кодом, разработанная для сбора и хранения метрик с различных источников. Она имеет модель сбора данных на основе pull-запросов, что означает, что агенты на хостах отправляют метрики на сервер Prometheus, который хранит и агрегирует их. Prometheus предоставляет широкие возможности для сбора метрик, включая метрики состояния ресурсов хостов и метрики потребляемых ресурсов для каждого сервиса. Он также поддерживает сбор метрик, специфичных для каждого сервиса.

Grafana - это графический интерфейс для визуализации данных из различных источников, включая Prometheus. Он позволяет настраивать пользовательские дашборды и панели для отображения метрик и настройки уведомлений на основе условий. Grafana имеет простой и интуитивно понятный интерфейс, который позволяет пользователю быстро и легко исследовать данные и получать визуальное представление о состоянии системы.

Сочетание Prometheus и Grafana предоставляет все необходимые функции для сбора и анализа метрик состояния хостов и сервисов в микросервисной архитектуре. Prometheus обеспечивает сбор метрик, а Grafana - интерактивный пользовательский интерфейс для анализа и визуализации данных.

## Задача 4: Логи * (необязательная)

Продолжить работу по задаче API Gateway: сервисы используемые в задаче пишут логи в stdout. 

Добавить в систему сервисы для сбора логов Vector + ElasticSearch + Kibana со всех сервисов обеспечивающих работу API.

### Результат выполнения: 

docker compose файл запустив который можно перейти по адресу http://localhost:8081 по которому доступна Kibana.
Логин в Kibana должен быть admin пароль qwerty123456


## Задача 5: Мониторинг * (необязательная)

Продолжить работу по задаче API Gateway: сервисы используемые в задаче предоставляют набор метрик в формате prometheus:

- Сервис security по адресу /metrics
- Сервис uploader по адресу /metrics
- Сервис storage (minio) по адресу /minio/v2/metrics/cluster

Добавить в систему сервисы для сбора метрик (Prometheus и Grafana) со всех сервисов обеспечивающих работу API.
Построить в Graphana dashboard показывающий распределение запросов по сервисам.

### Результат выполнения: 

docker compose файл запустив который можно перейти по адресу http://localhost:8081 по которому доступна Grafana с настроенным Dashboard.
Логин в Grafana должен быть admin пароль qwerty123456

---

### Как оформить ДЗ?

Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.

---
