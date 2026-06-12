---
title: "Boot Windows from USB Seagate FreeAgent"
date: 2010-06-09
forum: General Help
---

### Post by sinch on 2010-06-09
Hello,

I am newbie to Linux. I have bought a Seagate FreeAgent and installed Ubuntu Lucid on it(booting from USB). Works fine. Alhougth, I want to also use Windows to boot from the same disk via USB. 

I have install Windows (or copied the files to NTFS partition) and now I need to set up grub to have a chance to choose. How can I do this?

I tried:

sudo grub-install /dev/sda

but it not works :(

On my laptop, I also have another disk which I cannot even touch(firm's laptop)

Many thanks for help.
Kind regards,
sinch

---

### Post by C.S.Cameron on 2010-06-09
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)

Tells how to install XP to USB.

It is very slow.

An option that works well for me is to do a full install of Ubuntu to flash drive and then run Windows in Vbox.

I recall that Vbox also works with a persistent, (usb-creator / UNetbootin), flash drive.

edit:
NimbleX is a small, (200MB), file system that comes with Vbox.

---

### Post by sinch on 2010-06-09
Thanks for your reply.

Unfortunately, the link provided does not work. Also, I am not trying to run both systems from USB Flash Drive but from 500gb seagate mobile drive connected via USB.

I have both system on it(two separate partitions) just don't know how to configure grub.

Thanks,
sinch

---

### Post by michaelaye on 2010-06-09
i dont know what version of windows u want on ur external but this will install win vista/7/2008.

[http://www.boot-land.net/forums/index.php?showtopic=10126](http://www.boot-land.net/forums/index.php?showtopic=10126)

u will need to get the 3 files that are not provided and this installer need to be run from a windows envroment (u can use vbox; i dont know if wine will work)
ps. i havent tried it yet so i cant tell u how well it works but it seems to work pretty well, also it only works for external hdds and not flash drives.

pss. its also recommned that u format and create the partitions ur self and then i think u should b able to install ubuntu side by side after u install windows
**disclaimer: i am not responisble for any and all damage that may result in doing this, use at ur own risk**

---

### Post by sinch on 2010-06-10
ok, i will try to clarify my situation.

I've got a my company's laptop at home. It has a Primary Disk in it, which is encrypted and I cannot access it from other systems.

I have an USB Hard Disk on which I would like to install both Windows XP and Ubuntu Lucid. I have installed Lucid, works perfect, no problems (booting from USB).

I want to add Windows XP to it? How? Windows installer see Primary Laptop's drive and even if I choose to install on USB Drive it writes some things to Primary Drive.

My idea was just to copy all of the files from Windows XP to USB drive and then setup Ubuntu's Grub to have choose and start XP.

Probably I should not look for solving the problem here but on some XP forum. Thanks anyway.

---

### Post by michaelaye on 2010-06-10
hmmm.... as far as i know u can't "officially" install windows on a usb  external hdd so installing like normal will not work but i was able to  find something that might help u. now this guide is old and maybe out  dated and not work, i cant connect to the real website to see if there  is an updated version
here is the guide
[http://webcache.googleusercontent.com/search?q=cache:AlxKNrbMLakJ:www.ngine.de/article/id/8+install+win+xp+to+external+hdd&cd=2&hl=en&ct=clnk&gl=us](http://webcache.googleusercontent.com/search?q=cache:AlxKNrbMLakJ:www.ngine.de/article/id/8+install+win+xp+to+external+hdd&cd=2&hl=en&ct=clnk&gl=us)

and here is the website its on (i cant connect to it) 
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)

i dont know if just copying all the files will work, but ur welcome to  try
u will need to edit grub2 to include a win xp boot entry
here are some guides that might help
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

i'm sorry i cant really help anymore then this cuz i'm still kinda new  at linux my self
ps. i would recommend that u install windows first then ubuntu
best of luck to u

---

### Post by C.S.Cameron on 2010-06-11
I understand that there is a torrent out there named xp2usb that has had the xp iso already hacked.

---

### Post by dcstar on 2010-06-12
> **sinch said:**
> Hello,

I am newbie to Linux. I have bought a Seagate FreeAgent and installed Ubuntu Lucid on it(booting from USB). Works fine. Alhougth, I want to also use Windows to boot from the same disk via USB. 

I have install Windows (or copied the files to NTFS partition) and now I need to set up grub to have a chance to choose. How can I do this?
........

```
sudo update-grub
```

---

