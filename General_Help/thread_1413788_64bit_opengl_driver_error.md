---
title: "64bit opengl driver error"
date: 2010-02-22
forum: General Help
---

### Post by whogivesaskit on 2010-02-22
**on Ubuntu 9.10 Karmic 64bit**

Well i red the bug report for 9.10, searched the forum and as far as i could tell i couldnt find an answer for this

whenever i try to use a program that uses opengl im guessing i have to run the terminal command            export LIBGL_DRIVERS_PATH=/usr/lib32/dri

and then run the program i want to

such as for euphro

if i just run wine euphro.exe then i get an error with make sure ure open gl drivers are installed correctly or something

but if i run

export LIBGL_DRIVERS_PATH=/usr/lib32/dri

first then wine euphro.exe it runs perfectly

thank you in advance, i know using that command makes it work but i was wondering if theres a fix so i dont have to do that :)

i have the package installed ubuntu17

any help would be appreciated :)

---

### Post by Yellow Pasque on 2010-02-22
You can put the export command in your ~/.bashrc file or you can prefix it to the command-line field of any program launchers you want to use with it.

---

### Post by whogivesaskit on 2010-02-22
could you please explain how i would do that?

becacuse i tried and it dosent work :(

---

### Post by Yellow Pasque on 2010-02-22
```
gedit ~/.bashrc
```
Copy/paste that command to the end of the file. Save it. It won;t take effect until the next time you log in.

---

### Post by whogivesaskit on 2010-02-23
Thank you :)

Mark as Solved and just a question

how do you do the prefix for the launchers?

---

### Post by Yellow Pasque on 2010-02-23
When you create a custom launcher (on the desktop or in a panel), there will be a field for the command to run. Just put that before the command, like:
```
LIBGL_DRIVERS_PATH=/usr/lib32/dri wine youphro
```

---

### Post by whogivesaskit on 2010-02-23
i did put that

and it says no file or directory found when i open and put

LIBGL_DRIVERS_PATH=/usr/lib32/dri wine euphro

---

### Post by Yellow Pasque on 2010-02-23
well, maybe you need an "env" keyword. Here's an example that I use to launch foobar2000 (a Windows program):
```
env WINEPREFIX="/home/user/.wine" wine "C:\Program Files\foobar2000\foobar2000.exe"
```

---

### Post by whogivesaskit on 2010-02-23
that worked to launch it but not to load the 32bit library

that export does

---

