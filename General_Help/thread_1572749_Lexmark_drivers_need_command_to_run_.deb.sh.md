---
title: "Lexmark drivers: need command to run .deb.sh"
date: 2010-09-11
forum: General Help
---

### Post by RSASKA on 2010-09-11
I have Ubuntu 10.04 installed on a Virtual Machine. Would like to install drivers for Lexmark X6650. I download file

lexmark-08z-series-driver-1.0-1.i386.deb.sh

When I double-click, there is an option to run in terminal. I run in terminal. Then it asks for administrator password. I enter administrator password


It says "Wrong Password"

How can this be a wrong password.

A) I created the password
B) I used this password for other administrative tasks

This must be a problem with Lexmark!

Please tell me how to manually install the lexmark drivers from my terminal, i.e. once I navigate to the directory, what command should I type in?

---

### Post by cgroza on 2010-09-11
A deb.sh extension? Is it a deb or a sh script?

---

### Post by RSASKA on 2010-09-12
> **cgroza said:**
> A deb.sh extension? Is it a deb or a sh script?


How to determine if it's a deb or sh script?

I downloaded it from the following url:


[http://support.lexmark.com/index?page=content&productCode=LEXMARK_X6650&actp=PRODUCT&id=DR20523&segment=SUPPORT&userlocale=EN_US&locale=en](http://support.lexmark.com/index?page=content&productCode=LEXMARK_X6650&actp=PRODUCT&id=DR20523&segment=SUPPORT&userlocale=EN_US&locale=en)


**File Information**

   Title:   Linux driver for Debian Package Manager based distros
  File Name   lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz   



Please advise

---

### Post by jerome1232 on 2010-09-12
I faintly recall something about lexmark requiring the root account actually be unlocked. They are to lazy to have their script try sudo.


Edit: I was wrong downloaded it and tested it, you just need to run the script as root.


ie save it to your desktop then pop open a terminal anddddddddd

```
cd Desktop
sudo ./lexm(now hit tab twice fast and it'll auto complete the name)
```

---

### Post by RSASKA on 2010-09-12
> **jerome1232 said:**
> I faintly recall something about lexmark requiring the root account actually be unlocked. They are to lazy to have their script try sudo.


Edit: I was wrong downloaded it and tested it, you just need to run the script as root.


ie save it to your desktop then pop open a terminal anddddddddd

```
cd Desktop
sudo ./lexm(now hit tab twice fast and it'll auto complete the name)
```

You saved the day!!!

---

