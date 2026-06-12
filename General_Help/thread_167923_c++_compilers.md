---
title: "c++ compilers"
date: 2006-04-29
forum: General Help
---

### Post by hanamachi on 2006-04-29
anyone of any good programs for linux (ununtu) that i can use to run c++ programs, the one it came with anjuta ide doesn't seem to work


thanks

---

### Post by xenmax on 2006-04-29
Not sure if you are looking for a purely GUI solution, but if you dont mind command line, this should help.
```
sudo apt-get install build-essential
```should get you started.
You can also refer to [https://wiki.ubuntu.com/InstallingCompilers]("https://wiki.ubuntu.com/InstallingCompilers")

Then, do ```
g++ <filename>
``` which will create an executable called a.out in current directory. To run it,
do ```
./a.out
``` If you need more info, type ```
man g++
```

---

### Post by hanamachi on 2006-04-29
i did it but don't know what it does?

---

### Post by xenmax on 2006-04-29
[quote=hanamachi]i did it but don't know what it does?[/quote]
Can you please be a bit more clear? What did you do?

---

