---
title: "Codes for terminal?"
date: 2011-02-10
forum: General Help
---

### Post by Rexxer59 on 2011-02-10
I'm new to ubuntu linux and I hear using terminal is faster than using the system program to download and install software. Where can i find these codes to install?

---

### Post by vat with tux on 2011-02-10
Whatever u have heard can be true but i have never marked this.

As far as i'm knowing Generally command for installing software from terminal is of the form:

> sudo apt-get install <name of the software> 

---

### Post by elliotn on 2011-02-10
if u have an android phone, there is apps in the market that have Linux commands

---

### Post by Vaphell on 2011-02-10
also```
apt-cache search <keyword>
``` to find packages related to the <keyword>. Handy if the package name differs from the app name - you find out the name and can go with ```
sudo apt-get install <package(s)>
```

---

### Post by oldos2er on 2011-02-10
[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto) also (in terminal) **man apt-get** and **man aptitude**

Aptitude is not installed by default in 10.10, but you can use **sudo apt-get install aptitude** to get it.

---

