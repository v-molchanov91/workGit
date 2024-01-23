# Шпаргалака по работе с Git
### Оглавление
1. Основные команды в командной строке
2. Создание репозитория локально
3. Регистрация в GitHub
4. Создать ключ SSH
5. Связать локальный и удаленный репозтзарий

###### *Основные команды в командной строке*
| Команды | Описание |
| ------- |:--------:|
| pwd     | Показать текущую директорию |
| cd      | Перемещение по папкам|
| touch   | Создание файла |
| cat     | Просмотр содержимого |
| vim     | Редактирование файла |
| mv      | Перемещение файлов |
| mkdir   | Создание дироктории |
| rm      | Удаление файла |
| rmdir   | Удаление диретории|
| cp      | Скопировать файл |

###### Создание репозитория локально  

Создайте в домашней директории  новые папки mkdir dev/new_project<br>
Перейдите в созданую папку и выполните команду git init<br>
Репозиторий создан можете создавать тут файлы и добавлять их в отслеживание гитом с помощью команды git add --all (вместо all можно использовать имя нужного файла<br>
Далее выполнить команду git commit -m "описание измененини" 

###### Регитрация в GitHub
Перейдите на github.com и пройдите регистрацию<br>

###### Создание ключа

Далее в консоли создайте ssh ключ командой ssh-keygen -t ed25519 -C "почта к которой привязан эккаунт"<br>
Проверить создание ключей ls -a ~/.ssh<br>
Скопировать содержимое ключа в буфер clip < ~/.ssh/id_ed25519.pub<br>

###### Связать локальную репу и удаленную

Перейти на github.com и создать там ключ добавив скопированный ключ<br>
После проверить правильность ключа ssh -T git@github.com<br>
Связать репозитарии локальный и удаленный git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git
Проверить что все связано с помощью подробного вывода git remote -v

###### Хеш
В git каждому коммиту присваевается хеш набор цифр и букв
Хеш — идентификатор коммита
Хеширование (от англ. hash, «рубить», «крошить», «мешанина») — это способ преобразовать набор данных и получить их «отпечаток» (англ. fingerprint).
Обычно хеш — это короткая (
40
40 символов в случае SHA-1) строка, которая состоит из цифр
0—9 и латинских букв
A—F (неважно, заглавных или строчных). Она обладает следующими важными свойствами:
если хеш получить дважды для одного и того же набора входных данных, то результат будет гарантированно одинаковый;
если хоть что-то в исходных данных поменяется (хотя бы один символ), то хеш тоже изменится (причём сильно).

*Все хеши и таблицу хеш → информация о коммите Git сохраняет в служебные файлы. Они находятся в скрытой папке .git в репозитории проекта.*


###### Элементы описания коммита
После вызова git log появляется список коммитов<br>

Разберём элементы, из которых состоит описание:
1. строка из цифр и латинских букв после слова commit — это хеш коммита;
2. Author — имя автора и его электронная почта;
3. Date — дата и время создания коммита;
4. в конце находится сообщение коммита.


Получить сокращённый лог — git log --oneline

###### HEAD — всему голова

При вызове команды git log вы также могли заметить надпись (HEAD -> master)<br>
Файл HEAD (англ. «голова», «головной») — один из служебных файлов папки .git. Он указывает на коммит, который сделан последним (то есть на самый новый).<br>
Внутри HEAD — ссылка на служебный файл: refs/heads/master (или refs/heads/main в зависимости от названия ветки). Если заглянуть в этот файл, можно увидеть хеш последнего коммита
