---
title: "Installed Ubuntu, Won't run after login"
date: 2009-09-15
forum: General Help
---

### Post by xrobertx on 2009-09-15
Hey everyone

I installed Ubuntu on my netbook which was running XP. I used a program to do it, I can't really remember the name because it's on the netbook which is all messed up right now.

Anyway, after I enter my username and password I get this message 

" 2 failures since last login, Last was __________ 2009 on tty1.
robert@ubuntu:~$ "




I cannot get passed this point, Is there something I am missing?
Thanks for your help guys and gals

---

### Post by xrobertx on 2009-09-16
bump

---

### Post by linux_tech on 2009-09-16
If you are not able to login you can reset your password
This explains how 
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by xrobertx on 2009-09-16
Thanks for the reply


The screen is black with white text and shows a bunch of items with [ ok ] next to them. Then the last one is enter username, then password, and from their I am getting that "robert@ubuntu:~$ " thing. If I  hit any letters or numbers that "robert@ubuntu:~$" thing keeps coming!

I can't get passed this.

---

### Post by ChumleyEX on 2009-09-16
Try typing 

startx


If that doesn't work, which version of ubuntu did you install? If it't the server you may not have the GUI installed.

---

### Post by 3rdalbum on 2009-09-16
If you used the server disc, then there's no GUI; you might want to obtain a normal Desktop CD and use that to install Ubuntu.

If you did use the normal Ubuntu Desktop CD, then try typing:

```
sudo gdm
```

But normally you should be sent to the graphical login screen and then on to your desktop.

---

### Post by ChumleyEX on 2009-09-16
If you have server, you can type 

```
sudo apt-get install ubuntu-desktop
```

to install the gui.

---

### Post by xrobertx on 2009-09-16
> **ChumleyEX said:**
> If you have server, you can type 

```
sudo apt-get install ubuntu-desktop
```

to install the gui.

It appears that the OS is reinstalling itself after entering this command. Going to take about 18 more minutes. Is this what was supposed to be accomplished with this command?


Thanks for everyones assistance

---

### Post by ChumleyEX on 2009-09-16
No thats installing the desktop portion not the entire OS. I'm assuming all the other commands that were mentioned didn't work?

---

### Post by xrobertx on 2009-09-16
> **ChumleyEX said:**
> No thats installing the desktop portion not the entire OS. I'm assuming all the other commands that were mentioned didn't work?

Now the screen reads as follows:

Processing triggers for libc6...
Idconfig deferred processing now taking place
Processing triggers for python-support...
Processing triggers for initramfs-tools...
ypdate-initramfs: Generating /boot/initrd.img-2.6.28-15-generic
robert@ubuntu:~$ * Stopping anac (h) ronistic cron anacron

---

### Post by ChumleyEX on 2009-09-16
what happens if you type 

startx 

or 

sudo gdm

---

### Post by xrobertx on 2009-09-16
I've got the system booting normally now, but I am unable to download updates.

I am getting this message:

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.9-4ubuntu6.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.9-4ubuntu6.1_i386.deb)

The internet will not work connected to the LAN line, only wireless.

No sound and the internet is extremely slow

---

