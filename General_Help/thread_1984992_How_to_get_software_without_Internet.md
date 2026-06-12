---
title: "How to get software without Internet"
date: 2012-05-22
forum: General Help
---

### Post by Time Traveler on 2012-05-22
Briefly, no internet at my home.  I'd like to download a package (Calibre for example) and bring the archive home and install it on a desktop. 

Any tips?

---

### Post by scouser73 on 2012-05-22
Go to somewhere that has Internet access, download the software to a flash drive, go home and install it on your pc.

---

### Post by pootan on 2012-05-22
[https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection](https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection)  Might be what you're looking for.   I've used the Synaptic package download script successfully but I can't vouch for the other methods.

---

### Post by cortman on 2012-05-22
There are a number of different ways to do this. There's [Keryx]("http://keryxproject.org/"), which looks really good but I've no experience with, and also [Wassail]("https://sourceforge.net/projects/wassail/"), a really simple VB program I wrote for downloading packages from Synaptic scripts. There's links to offline installation etc. info in my signature.

---

### Post by gordintoronto on 2012-05-22
The obvious way to do this is with packages.ubuntu.com. It will tell you about required dependencies. If you open a terminal and run:
dpkg --get-selections "*" > Desktop/applications

it will tell you what packages you have installed. Copy it to a flash drive and view it when you are using packages.ubuntu.com

---

