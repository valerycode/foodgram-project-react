![foodgram](https://github.com/valerycode/foodgram-project-react/actions/workflows/foodgram_workflow.yml/badge.svg)

https://www.foodgram.tk/
# Описание проекта
Продуктовый помощник - сервис, где пользователи могут публиковать рецепты, подписываться на публикации других пользователей, добавлять понравившиеся рецепты в список «Избранное», а перед походом в магазин скачивать сводный список продуктов, необходимых для приготовления одного или нескольких выбранных блюд.
### Технологии
- [Django REST Framework](https://www.django-rest-framework.org/) - is a powerful and flexible toolkit for building Web APIs.
- [Python](https://www.python.org/) - is an interpreted high-level general-purpose programming language.
- [Django Framework](https://www.djangoproject.com/) - is a high-level Python Web framework that encourages rapid development and clean, pragmatic design.
- [PostgeSQL](https://www.postgresql.org/) - is an open source object-relational database system that uses and extends the SQL language combined with many features.
- [Docker](https://www.docker.com/) - is a set of platform as a service (PaaS) products that use OS-level virtualization to deliver software in packages (containers).
- [Gunicorn](https://gunicorn.org/) - is a Python WSGI HTTP Server for UNIX.
- [Nginx](https://nginx.org/) - is a web server that can also be used as a reverse proxy, load balancer, mail proxy and HTTP cache.
### Как развернуть проект (на сервере)
 - сделать fork проекта в свой аккаунт

[![](https://img.shields.io/badge/my%20project-fork!-informational?style=for-the-badge&logo=appveyor)](https://github.com/valerycode/foodgram-project-react/fork)
- добавить свои данные для переменных в secrets:
```
EMAIL_HOST
EMAIL_PORT
EMAIL_USER
EMAIL_PASSWORD
SECRET_KEY
SITE_ID
DB_ENGINE
DB_NAME
POSTGRES_USER
POSTGRES_PASSWORD
DB_HOST
DB_PORT
```

- скачать репозиторий, перейти в директорию с проектом

```git clone git@github.com:ваш-логин/foodgram-project-react.git```

```cd /<путь-до-директории>/```

- создать виртуальное окружение, активировать его

```python3 -m venv venv```

```. venv/bin/activate```

- установить зависимости

```python -m pip install -r requirements.txt```

- сделать пуш с любым изменением в проекте

```git push```

- подключение сертификатов Let’s Encrypt на сайт

```chmod +x init-letsencrypt.sh```

```sudo ./init-letsencrypt.sh```


- загрузка тестой базы на сайт(без картинок)

```sudo docker-compose exec web bash```

```python3 manage.py shell```

выполнить в открывшемся терминале:

```
>>> from django.contrib.contenttypes.models import ContentType

>>> ContentType.objects.all().delete()

>>> quit()
```


```python manage.py loaddata dump.json ```

- после установки сертификатов и загрузки тестовой базы:

```sudo docker-compose up -d --build```

### После каждого обновления кода в GitHub будет осуществляться:
1. Проверка кода на соответствие стандарту PEP8 (с помощью пакета flake8).
2. Сборка и доставка докер-образов на Docker Hub.

### Данные суперпользователя:
логин - admin
пароль - G6jsn245hNJZKS125

### Как развернуть проект (локально)
- отредактировать docker-compose.yaml
```
web:
  image: <DOCKER_USERNAME>/<DOCKER_REPO>:latest
--->

web:
  build: .
```

- собрать образ, запустить

```sudo docker build -t <задать название образа> .```

```sudo docker-compose up```

- применить миграции для приложения

```sudo docker-compose exec web python manage.py migrate --noinput```

- создать суперпользователя

```sudo docker-compose exec web python manage.py createsuperuser```

- собираем статические данные

```sudo docker-compose exec web python manage.py collectstatic --no-input```
