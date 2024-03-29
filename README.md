# Памятка по git

---

## Начало

---

### Первый шаг

- создаем папку, где будет храниться проект

- открываем git bash и с помощью команды cd "наша папка" заходим в проект

- инициализируем и коммитим с помощью команд:

```bash
cd "наша папка"

git init

git add .

git commit -m "Информативное сообщение о коммите"
```

---

### Второй шаг

- теперь нужно создать SSH ключ для приватности нашего репозитория, обычно он хранится  
в домашней директории. Для создания нашего ключа выполним следующие команды в git bash:

```bash
ssh-keygen -t ed25519 -C "почта@почта.ru"

cat ~/.ssh/id_ed25519.pub | clip
```

- создали и скопировали в буфер обмена SSH-ключ

- далее заходим в settings в правом верхнем угла, нажав на свой профиль на сайте github

- выбираем вкладку SSH and GPG keys и добавляем новый ключ, нажав на кнопку New SSH key

---

### Третий шаг

- создаем удаленный репозиторий на сайте github, лучше назвать одним и тем же именем,  
что и сама папка, созданная на первом шаге

- теперь свяжем удаленный репозиторий с локальным с помощью следующих команд:

```bash
git remote add origin git@github.com:ronnyscale/gitknowledge.git

git remote -v
```

- проверим второй командой связан ли удаленный репозиторий с локальным. Должно вывестись два  
сообщения, окончивающиеся на fetch и push

---

### Четвертый шаг

- Далее, вожделенно "пушим" на удаленный репозиторий наши файлы командой:

```bash
git push -u origin master/main
```

- "-u origib master/main" - пишем один раз и далее при последующих "пушах" просто "git push"

---

## О файлах в папке .git

## HEAD

- Файл хранит в себе hash-код последнего добавленного коммита


## Медиум

### Команды

- git log - выводит инфу о коммитах
- git log --oneline - выводит краткую информацию о коммитах (помогает разобраться, если много коммитов)
- статусы файлов:
1. modified + git add = staged
2. untracked - новый файл
3. tracked - отслеживаемый файл

### Схема


```mermaid
graph LR;
	untracked        -- "git add"    --> staged;
	staged    	 -- "git commit" --> tracked/commited;
	modified  	 -- "git add"    --> staged;
	tracked/commited -- "изменение"  --> modified
```

