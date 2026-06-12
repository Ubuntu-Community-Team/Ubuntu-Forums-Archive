---
title: "Natty spontaneously reboots"
date: 2011-05-20
forum: General Help
---

### Post by BenM on 2011-05-20
In the week since I upgraded to Natty, my system has spontaneously and randomly rebooted three times. Once when opening a document, one time when clicking a link and another time when I wasn't doing anything. This never happened with earlier releases, so I have no idea what to do. Can anyone help me diagnose/fix what might be happening.

Toshiba Satellite A305 
Intel Core2 Duo (64 bit)
3964 Megabytes Installed Memory
Intel 4 Series Express Integrated Graphics card

This problem is a show stopper for me, so help would really be appreciated.

---

### Post by BenM on 2011-05-20
Anyone? It just happened again. When it was exiting I got messages about CUPS and Timidity, but they went by to fast for me to write them down. Also, I think it's just x rebooting. I don't get kicked all the way back to GRUB.

---

### Post by Larkspur on 2011-05-20
My screen has flickered once or twice, and I've been logged out once.  I think you might be right about it being X or maybe Compiz crashing so hard that it knocks out X for a second or two.

---

### Post by BenM on 2011-05-28
I did a fresh install hoping that might clear things up. No such luck. Can anyone advise on how to see if something is wrong with X or any other alternatives? I can't continue to have random reboots.

---

### Post by linuxinstalledfromhdd on 2011-05-28
I'm using a one year old Toshiba Satellite. Same specs as yours, pretty much.  I installed 32-bit Ubuntu 10.10, and used this walkthrough.. 

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Also I installed the PAE kernel so I could use all of my ram sticks, since the 64-bit version of Ubuntu was too wild and unstable on my laptop.   

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

And I used Ubuntu-Tweak to install the xorg-edgers repository and updated my video drivers. 

Also I used the Firefox Flash Aid plugin to get the Adobe Flash Plugin just right. 

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

Highly recommended. :) 

Goodluck

---

### Post by BenM on 2011-05-29
Hi, thanks for the answer **linuxinstalledfromhdd**. I was just wondering what you were seeing that made you make the change. Was it just limited to problems in Natty? I've been dual booting this laptop (64 bit version) for two years and didn't see the kinds of things before that I have since upgrading.

---

