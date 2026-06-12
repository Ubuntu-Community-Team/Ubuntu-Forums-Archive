---
title: "Problems after upgrade"
date: 2012-01-30
forum: General Help
---

### Post by lamar328 on 2012-01-30
I was upgrading to Ubuntu 11.10 and my computer went into hibernation. As I booted up the computer the installation continued, but with a ton of installation errors on the update terminal screen. I closed the update and went to start the update from fresh to get all of the files that had been previously missed. The first issues i've had is that my password for verification was not recognized. I decided to restart my computer. BAD IDEA. 

I get the purpleish screen with the Uubuntu logo, then immediately a black screen with white text checking that different hardware components are [ OK ].

This is where i get stuck. The last line of text:

[    23.814145] ieee80211 phy0: wl_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)

Nothing happens after this. 


**[COLOR="Red"][SIZE="2"]TO SUM THIS ALL UP[/SIZE][/COLOR]**

Updated to 11.10. Did not get the full update and restarted my computer. Ubuntu does not load to desktop now.

---

### Post by LinuxFan999 on 2012-01-30
Did you try to upgrade with the CD or the update manager?

---

### Post by lamar328 on 2012-01-30
> **LinuxFan999 said:**
> Did you try to upgrade with the CD or the update manager?

I updated using the update manager. I'm using an HP Mini, so there is no CD drive. 

I'm using a friends computer at the moment, so i'm open to uploading Ubuntu from a pendrive, but I'd need to know how to backup everything I have on my computer already.   

I'd rather not go that route though.

---

### Post by JC Cheloven on 2012-01-30
I don't realize where exactly the boot process hungs, but, are you able to log-in at terminal? Be it booting in secure mode from grub, or pressing Ctrl-Alt-F1 at some point... this could give us a start point.

> 
I'm using a friends computer at the moment, so i'm open to uploading Ubuntu from a pendrive, but I'd need to know how to backup everything I have on my computer already. 
If you have to reinstall (or want to do so for the shake of simplicity), your data will be more than likely accesible from a live session, so you can backup before installing.

---

### Post by LinuxFan999 on 2012-01-30
Upgrading Ubuntu through the update manager is not recommended at all. I highly recommend doing a clean install from a flash drive (since your net book has no CD drive). While running from the flash drive, you can back up your data to external storage (just move the files over).  After backing up your data, you can run the installer from the flash drive.

---

### Post by lamar328 on 2012-01-30
> **JC Cheloven said:**
> I don't realize where exactly the boot process hungs, but, are you able to log-in at terminal? Be it booting in secure mode from grub, or pressing Ctrl-Alt-F1 at some point... this could give us a start point.


If you have to reinstall (or want to do so for the shake of simplicity), your data will be more than likely accesible from a live session, so you can backup before installing.

I cannot get to terminal at the moment. The only options I have during boot-up are:
F9
F10
F12


Could you briefly explain the live session?

---

### Post by lamar328 on 2012-01-30
> **LinuxFan999 said:**
> Upgrading Ubuntu through the update manager is not recommended at all. I highly recommend doing a clean install from a flash drive (since your net book has no CD drive). While running from the flash drive, you can back up your data to external storage (just move the files over).  After backing up your data, you can run the installer from the flash drive.

I'll for sure keep that in mind for next time! As I had just asked from the previous poster, can I run the installer from my flash drive but still get a chance to back up everything on my computer without having access to my desktop?

---

### Post by lamar328 on 2012-01-30
Not sure if this will make any difference, but I've gotten to a stage on my screen where I get this:

Ubuntu 11.10 gavin-laptop tty1

gavin-laptop login:
Password:


I just press "enter" when prompted for my login, and then when I try my usual password, it is not recognized. Not sure if this is a related issue or not to this post...

---

### Post by LinuxFan999 on 2012-01-30
> **lamar328 said:**
> Not sure if this will make any difference, but I've gotten to a stage on my screen where I get this:

Ubuntu 11.10 gavin-laptop tty1

gavin-laptop login:
Password:


I just press "enter" when prompted for my login, and then when I try my usual password, it is not recognized. Not sure if this is a related issue or not to this post...
You need to type your user name where it says "gavin-laptop login". If you don't, you cannot log in.

---

### Post by lamar328 on 2012-01-30
> **LinuxFan999 said:**
> You need to type your user name where it says "gavin-laptop login". If you don't, you cannot log in.

haha ye I tried that shortly after making that last post. Now i'm at the stage where I want to instal Ubuntu from a flash drive, but still backup everything on an external hard drive. I need to do this all through the startup terminal because I don't have access to my desktop.


**To not have overlapping posts, I've summed up what I want to do here : [http://ubuntuforums.org/showthread.php?p=11652709#post11652709](http://ubuntuforums.org/showthread.php?p=11652709#post11652709)**

---

### Post by JC Cheloven on 2012-02-01
> **lamar328 said:**
> Not sure if this will make any difference, but I've gotten to a stage on my screen where I get this:

Ubuntu 11.10 gavin-laptop tty1

gavin-laptop login:
Password:

I just press "enter" when prompted for my login, and then when I try my usual password, it is not recognized. Not sure if this is a related issue or not to this post...
OK, this is the point I meant: you have acces to terminal mode. As the other poster said you have to type your username, then your password. Then we could try something... but I see you have decided to reinstall, so that no longer applies.

You will start a live session, booting from your pendrive, before installing. From that live session you can access your internal hard disk and move your sensible data to an external media, before installing.

Cheers

---

### Post by lamar328 on 2012-02-02
Thanks a ton for everyones help. What I ended up doing was reinstalling Ubuntu using > sudo apt-get install gnome-shell

got me to a usable desktop, and from there I could perform updates and figure the rest out. Lost nothing! So stoked :)

---

