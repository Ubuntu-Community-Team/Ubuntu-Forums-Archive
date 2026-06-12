---
title: "ati radeon 9250"
date: 2006-04-10
forum: General Help
---

### Post by htg331 on 2006-04-10
ok i just got these card the other day and i put it in and ubuntu does not want to pull up because of no drivers and then i go to ati website and try and the linux drivers i download and and it is a .run i cant it to RUN right lol or to install what do i need to do??????????????

---

### Post by Zimmer on 2006-04-10
[https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)
Best place  to start... 

and here for more up-to-date info re latest ATI drivers..(personally I use the fglrx from Ubuntu with my 9600 card.

[http://www.ubuntuforums.org/showthread.php?t=75378](http://www.ubuntuforums.org/showthread.php?t=75378)

---

### Post by BoyOfDestiny on 2006-04-10
[QUOTE=htg331]ok i just got these card the other day and i put it in and ubuntu does not want to pull up because of no drivers and then i go to ati website and try and the linux drivers i download and and it is a .run i cant it to RUN right lol or to install what do i need to do??????????????[/QUOTE]

Drivers for 9250 are included (open source 2D and 3D). For breezy to enable DRI for it:

open up a terminal.

sudo gedit /etc/X11/xorg.conf

Search for "ati", change it to "radeon". 
From there reload X, (reboot is always a simple way).

Then you are golden.

If you mean you are having trouble getting into Ubuntu at all, go to recovery mode, and type
dpkg-reconfigure xserver-xorg
Go through the steps.

You can only choose "ati". You can set it to radeon manually. The good news in dapper, with my 9250 I get full acceleration out of the box with "ati", it knows to use the radeon driver. :)

Just to reiterate, you do not need to use fglrx for this card.

---

### Post by klichev on 2006-04-10
I suppose Ubuntu hadn't got it that you have a new video card. For I also have 9250 and it works flawlessly.

---

