# GlassFish

## Первоначальная настройка

Добавить в `.bashrc`:

```bash
export JAVA_HOME=/usr/jdk/jdk1.8.0
export PATH=$JAVA_HOME/bin:$PATH
export PATH=/home/s242585/glassfish4/bin:$PATH
```

Строки выше позволят использовать по умолчанию JDK 8 и Glassfish 4.1.2.
Для применения изменений нужно перезапустить `bash`.

Создать домен:

```bash
asadmin create-domain --domaindir ~/YOUR_DIR --portbase [portbase из таблицы с вариантами]
```

`YOUR_DIR` -- путь к директории где будет находиться домен

## Запуск домена

```bash
asadmin start-domain --domaindir ~/YOUR_DIR
```

При запуске будет выведено подобное сообщение:
```
Waiting for domain to start .....
Successfully started the domain : ...
domain  Location: ...
Log File: ...
Admin Port: [port]
Command start-domain executed successfully.
```

Нужно запомнить admin port для выполнения дальнейших команд.

## Загрузка приложения

Собранный `.war` нужно залить на сервер, затем запустить:

```bash
asadmin deploy --force true --port [admin port] path/to/war.war
```

Параметр `--force true` нужен для того, чтобы перезаписать приложение,
если оно уже было загружено.

