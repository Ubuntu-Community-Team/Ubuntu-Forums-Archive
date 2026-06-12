---
title: "Problem in authentification"
date: 2010-03-03
forum: General Help
---

### Post by necer_cheniki on 2010-03-03
Hello,
 
I am new in Ubuntu . First why I have to authenticate each time I want to change some settings or execute some terminal instructions ? am not the administrator user ?
Then I installed Oracle on my system , but when I click to "Go to database Home Page " witch send open the following address "http://127.0.0.1/apex" I can't find the page.
I tried to configure Oracle by terminal instruction , exactly the following command :
```
/etc/init.d/oracle-xe configure
```
this message appeared :
```
You must be root to run the configure script.  Login as root and then run the 
configure script.

```

Help me to solve this problem.

---

### Post by doas777 on 2010-03-03
this should help:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

you are an admin, which means you can explicitly run stuff as root, but you have to tell it that you want to, and that you are sure you want to do what you say you do.  

basically when you run a cli command as admin, put the word "sudo" in front of the command, or if it is a graphical app, use 'gksu'. both will prompt you for YOUR password (not root's as root has no usable password by default on an ubuntu system).

---

### Post by necer_cheniki on 2010-03-03
Thank you , it works fine now.

---

