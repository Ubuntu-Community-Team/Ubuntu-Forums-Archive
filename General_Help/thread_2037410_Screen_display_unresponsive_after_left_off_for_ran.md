---
title: "Screen display unresponsive after left off for random time"
date: 2012-08-04
forum: General Help
---

### Post by trepid666 on 2012-08-04
Hi there, I'm hoping someone can help me out.

As the title states, if i close my laptop lid or lock the screen or even just leave the display to timeout on its own, the next time i go to use the computer i either get a black screen with my mouse pointer visible or i get my background wallpaper with no panel or anything on it.

I am forced to hard reboot.

Any ideas?
Thanks

*edit
I am running ubuntu 12.04 unity 64bit

---

### Post by gordintoronto on 2012-08-04
Brand and model of computer? What video adapter? (Run lspci, find the line which includes "VGA".)

---

### Post by trepid666 on 2012-08-05
Its an Acer Aspire 5750 with the Sandybridge integrated video card. Intel Core i5 2nd Gen

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

---

### Post by trepid666 on 2012-08-10
anyone?

---

### Post by gordintoronto on 2012-08-11
You could try the solution in this page:
[https://help.ubuntu.com/community/Asus_U36JC#Suspend.2BAC8-Resume-1](https://help.ubuntu.com/community/Asus_U36JC#Suspend.2BAC8-Resume-1) 

It's for a different Asus computer, maybe worth a go.

---

### Post by trepid666 on 2012-08-17
> **gordintoronto said:**
> You could try the solution in this page:
[https://help.ubuntu.com/community/Asus_U36JC#Suspend.2BAC8-Resume-1](https://help.ubuntu.com/community/Asus_U36JC#Suspend.2BAC8-Resume-1) 

It's for a different Asus computer, maybe worth a go.


But I dont have an Asus, i have an ACER

---

### Post by trepid666 on 2012-08-17
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

im gonna give this a go

---

### Post by kirenpillay on 2012-09-28
I'm running into the same issue. The screen widgets become unresponsive once I come out of the screen locked state. 

Running Ubuntu 12.04, on an HP Probook 6540b. Intel Graphics card.

Rebooting the system solves the problem.

---

