---
title: "Unable to install kubuntu-desktop from cdrom"
date: 2006-06-16
forum: General Help
---

### Post by nastya on 2006-06-16
Hello,

I've searched the forums to find away around my problem, but to no avail. I run Ubuntu 6.06 and I have added my kubuntu cdrom to my apt sources with sudo apt-cdrom add. However, after running sudo apt-get update and sudo apt-get install kubuntu-desktop, I cannot install it from the cdrom. Instead, apt-get tried to download the packages from the internet. As I am on 56k and cannot be connected for long periods of time, this poses a problem for me. Does anyone have any ideas as to why this might be happening? The same thing also happened when I tried to install Xubuntu-desktop using an Xubuntu dapper cdrom.

Here is my soures.list

deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted multiverse universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted multiverse universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

---

### Post by patwack on 2006-06-16
it could be because there is a newer version available online than on the cd

try commenting out all the other repos and then try again

---

### Post by nastya on 2006-06-17
Tried that, but it just took away the option of installing kubuntu-desktop completely after I updated that list.

---

### Post by Vlatko on 2006-10-04
have you managed to resolve this? i'd like to install kubuntu desktop via the install cd, rather than having to download all the files. 

how can i install it via the install/live cd?

---

