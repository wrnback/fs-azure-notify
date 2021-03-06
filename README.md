# fs-azure-notify

Небольшой скрипт для отслеживания активных запросов на вытягивания команды в Azure DevOps.

## Как это работает?
В указанное время скрипт соберёт все активные запросов на вытягивания команды и отправит их на Disсord Webhook.

## Пример сообщения
![image](https://user-images.githubusercontent.com/48364828/114230430-8fb1c800-9992-11eb-9f66-9ce4b7d35f60.png)

Сообщение можно разделить на части:
- `[p]/[d]` - тип запроса на вытягивания, публичный (public) или черновик (draft)
- `[Иванов Иван Иванович]` - создатель
- `[2/4]` - количество рецензентов, что одобрили запрос на вытягивание / всего рецензентов
- последняя часть сообщения отвечает за заголовок

При нажатии запрос на вытягивание открывается в Azure DevOps

## Требования
- python 3.8+

## Установка и запуск
```
pip install -r requirements.txt
python start.py
```

## Пояснение к config.json
[Пример](https://github.com/wrnback/fs-azure-notify/blob/master/config.json)
- `despatch` - список времени для отправки
- `proxies` - http, https прокси
- `azure.token` - маркер для подключения к Azure REST API. Как его получить смотри [здесь](https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=preview-page)
- `azure.host` - хост с Azure REST API
- `azure.rganization` - организация
- `azure.project` - проект
- `azure.team` - команда чьи запрос на вытягивание вам нужно отслеживать
- `azure.exclude_teams` - список команд, члены которых будут исключены из целевой команды (azure.team)
- `azure.repositories` - список репозиториев для отслеживания
- `webhook` - вебхук Discord
