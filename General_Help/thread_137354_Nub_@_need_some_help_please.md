---
title: "Nub @ need some help please"
date: 2006-02-27
forum: General Help
---

### Post by morphineinduced on 2006-02-27
well im new and well its obvious that it doesnt come with anything installed and iv gotten some of my basic things to work like sound but the problem is i cant install anything to my root folder ..... with archive manager , ill go and try and install it into my folder and im taking it that it picks where to place it since its nothing like SuSE and how it installs so i still dont know really what im doing with that but the point i was trying to make was when i go to use archive manager or to extract into a directory it keeps saying i dont have the privelages to do this , so how do i set this up so i dont keep having this problem and how also do i get into there ...... and i do have many more questions but i dont want to over whelm myself with all the answers i would get back for the various things ....... also i am the only one that uses this comp so i dont know if that would help about going about fixing this

---

### Post by shams2 on 2006-02-27
to install any software you must be root for this do:
sudo su
type your password now you are root.

---

### Post by morphineinduced on 2006-02-27
ok so i know type in sudo su but that will only be in terminal ........ isnt there a way to use the archiver program while being in root without having to be in the terminal the whole time ...... because i wont know were to put this dvd playing program

---

### Post by shams2 on 2006-02-28
To run a program using sudo that normally is run as the user, such as gedit, go to Applications --> Run Application and enter gksudo gedit
For users of Kubuntu, use kdesu in replacement for gksudo

---

