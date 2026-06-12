---
title: "problems with ubuntu 9.10, please help!"
date: 2010-02-18
forum: General Help
---

### Post by thephlood on 2010-02-18
hi.

i have been trying to install TOR on my computer (im running ubuntu 9.10) , and when i type:

'sudo deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) karmic main'

i get this message:

'sudo: deb: command not found'

anyone have any ideas about what might be causing this?

---

### Post by Rocky_Reid on 2010-02-18
I am by no means any sort of expert however did you try sudo apt-get then the link? I have never tried or heard of sudo deb before. I am not saying it incorrect I just never ran in to a situation I used that particular command.

---

### Post by lindsay7 on 2010-02-18
looks like you need to add this to your software sources

Go to system/administration/software source

hit "add"  and type or paste the line you are putting into the terminal (deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) karmic main).  Then close and it will update.


[ATTACH]147426[/ATTACH]


After this go to the terminal and type sudo apt-get update.

---

### Post by thephlood on 2010-02-18
> **lindsay7 said:**
> looks like you need to add this to your software sources

Go to system/administration/software source

hit "add"  and type or paste the line you are putting into the terminal (deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) karmic main).  Then close and it will update.


[ATTACH]147426[/ATTACH]


thanks! i think that did the trick!:D:D:D:D

---

