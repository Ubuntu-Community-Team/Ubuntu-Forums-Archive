---
title: "uninstalling things"
date: 2010-08-30
forum: General Help
---

### Post by f6e9a on 2010-08-30
ok i have been using ubuntu 10.04 for about a month and i really like it its not like the windows crap.

but i would like to know how to uninstall things through the terminal like uninstalling packages or software i dont want or need i dont want to do it through the ubuntu software center because i want to learn commands and things about ubuntu as quick as i can.

any  help will be appreciated :D

---

### Post by zpletan on 2010-08-30
```
man apt-get
```

---

### Post by uRock on 2010-08-30
Just be sure to look at what dependencies are going to be removed with your **apt-get remove** command. If you see **ubuntu-desktop** in the mix, then do _not_ enter yes when it asks if you want to remove the software.

---

### Post by borth92 on 2010-08-30
sudo apt-get autoremove

that gets rid of it completely

---

### Post by f6e9a on 2010-08-30
now i am confused which one do i use autoremove or remove

---

### Post by andrewthomas on 2010-08-30
> **borth92 said:**
> sudo apt-get autoremove


  ```
     autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.

```So you could do an autoremove first, then do an apt-get remove. **But be sure to pay attention to all the dependencies that it wants to remove with it**

---

### Post by bodhi.zazen on 2010-08-31
First, IMHO, it is much easier to start with a minimal system and build up then it is to remove things from a default ubuntu desktop install.

Second, IMHO, there are better distros to start minimal with, ie packages have less dependencies in Arch or Debian then Ubuntu.

Third, if you do not know what it is, research the package before you remove it ;)

---

