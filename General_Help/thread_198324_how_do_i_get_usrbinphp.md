---
title: "how do i get /usr/bin/php"
date: 2006-06-17
forum: General Help
---

### Post by deathbyswiftwind on 2006-06-17
Hey as the title says what do i need to install to get /usr/bin/php i am trying to run a program that will let me sync my philips gogear mp3 player. The only problem is I installed everything listed as a dependency but when I try and run it I get this error

```
rob@ubuntu:~/Desktop$ cd gogear_mgr-0.01
rob@ubuntu:~/Desktop/gogear_mgr-0.01$ ./gogear_mgr
bash: ./gogear_mgr: /usr/bin/php: bad interpreter: No such file or directory
```

After checking in /usr/bin i dont have php but I did install php4,php4-cgi,and some other php-sqlite like the readme says to.

Please someone help me save my poor mp3 player from microsoft :(

---

### Post by loell on 2006-06-17
install php by,

sudo apt-get install php4

---

### Post by scxtt on 2006-06-17
since you said you installed php4, do this from a terminal:

[indent]$:> whereis php[/indent]and make sure it's located @ /usr/bin/php ...

---

