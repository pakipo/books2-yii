# books2-yii

Приложение библиотеки на Yii 2 Advanced. Рядом должен лежать `books2-infra`: он поднимает nginx, PHP и MySQL и монтирует этот каталог в контейнер.

Входные точки:

- `frontend` — публичный сайт, пока заглушка Yii. Позже сюда встанет SPA, сборка в `frontend/dist`.
- `backend` — админка.
- `api` — JSON для фронта. Корень отвечает `{"status":"ok"}`.
- `common` — общие модели.
- `console` — миграции и команды `php yii`.

Локальная база в окружении Development: хост `mysql`, база `books`, пользователь `books`, пароль `books`. Эти значения копируются командой `php init` в `*-local.php`, которые в git не входят.

## Первый запуск внутри контейнера

```bash
cd /var/www/books-yii
composer install
php init --env=Development --overwrite=All
php yii migrate
```

Сайты после этого: `http://books.local`, `http://api.books.local`, `http://admin.books.local`.
