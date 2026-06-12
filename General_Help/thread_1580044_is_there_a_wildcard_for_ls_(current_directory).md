---
title: "is there a wildcard for ls (current directory)?"
date: 2010-09-22
forum: General Help
---

### Post by UncleBoarder on 2010-09-22
in /mnt I have three directories... backup  shared  temp

If I do a ls b* I thought I would get a listing of all files and directories that begin with 'b'... I thought I would get "backup".

Instead I got "home"... which is a directory under "backup".

How do I get a list of files and directories that match a character string, but ONLY of the current directory... non-recursive.

---

### Post by TeoBigusGeekus on 2010-09-22
Try with du:
```
du -h --max-depth=1 b*
```

---

### Post by UncleBoarder on 2010-09-22
Nope... that took it's time as it scanned my hard drive and gradually gave me...

[FONT=Fixedsys]root@ubuntu:/media# du -h --max-depth=1 b*
28K    backup/.Trash-1000
13K    backup/backup
1.6G    backup/c
32G    backup/Documents
1.8G    backup/drive C
1.2G    backup/drive C (old)
21K    backup/etc
95M    backup/home
3.3G    backup/Jimmy Short
582M    backup/Jimmy's Music
783M    backup/Laptop
du: cannot access `backup/Temp D/Apps/TurboTax/32bit/ttax.dll': Input/output error
42G    backup/Temp D
48G    backup/Windows
130G    backup
[/FONT]

---

### Post by WorMzy on 2010-09-22
You can do it by piping into grep:

```
ls | grep '^[B|b]'
```

Someone'll probably be able to give you a more efficient answer though.

---

### Post by slooksterpsv on 2010-09-22
ls -d B* or ls -d b*

---

