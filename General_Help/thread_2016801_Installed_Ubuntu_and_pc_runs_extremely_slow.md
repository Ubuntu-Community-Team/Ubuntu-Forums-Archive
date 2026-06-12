---
title: "Installed Ubuntu and pc runs extremely slow"
date: 2012-07-04
forum: General Help
---

### Post by africanlion on 2012-07-04
Hey guys
Newbie here who has decided to take the plunge after being fed up with Windows Vista. Literally my first day with ubuntu :guitar:

However since installing it i notice my pc runs extremely slowly. Infact its running even slower than my laptop which is like 5 years older than this pc

A friend has suggested that maybe my pc isnt powerful/fast enough to run the latest Ubuntu. Could that be the case?

I am running a Dell Dimension 5000. Pentium 4 processor, 80 gb hard drive

My RAM is 418MB :(

Thanks in advance

---

### Post by Zookey500 on 2012-07-04
Hi,
If I remember correctly there are two versions of ubuntu, a high spec (1ghz, 1gb RAM) and a low spec (lower than above). You should have the lower spec one, if you only have 418mb of RAM. However, I am really surprised that you could install vista on that PC.

I can't find that alternative version of ubuntu, but i'll post a link when I find it. 


Best regards,
Matthew

---

### Post by Zookey500 on 2012-07-04
I have found the link, although it is the newest version.....
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

unless you would prefer to look at older versions of the OS.


[http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+alternate&ie=utf-8&oe=utf-8&gl=uk](http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+alternate&ie=utf-8&oe=utf-8&gl=uk)


Best regards,
Matthew

---

### Post by ajgreeny on 2012-07-04
Your friend is more or less correct, that machine will never run ubuntu 12.04 and unity well, as it does not reach the minimum spec required.  Even a min spec machine will run painfully slowly.
[https://help.ubuntu.com/12.04/installation-guide/amd64/minimum-hardware-reqts.html](https://help.ubuntu.com/12.04/installation-guide/amd64/minimum-hardware-reqts.html)

Try Xubuntu or Lubuntu instead and you should have more luck with a faster running OS.

---

### Post by lrcaballero on 2012-07-04
If you have no luck with Ubuntu 12.04 try via live cd Lubuntu 12.04 which is a more lighter OS for older systems.

[http://lubuntu.net/tags/lubuntu-1204](http://lubuntu.net/tags/lubuntu-1204)

Welcome to Ubuntu/Linux world you are in good hands!

---

### Post by africanlion on 2012-07-05
Thanks guys for your responses. However my knowledge of Ubuntu and computers in general is not great so given the various suggestions eg using lubuntu and the one suggested by Zookey500, which do you suggest i follow

I want to be able to get the best out of the software given my somewhat dated PC.


Would adding extra RAM to 1GB make much of a difference

Thanks

---

### Post by ajgreeny on 2012-07-05
> **africanlion said:**
> Thanks guys for your responses. However my knowledge of Ubuntu and computers in general is not great so given the various suggestions eg using lubuntu and the one suggested by Zookey500, which do you suggest i follow

I want to be able to get the best out of the software given my somewhat dated PC.


Would adding extra RAM to 1GB make much of a difference

Thanks
You would certainly see a noticeable difference, but I think Ubuntu with unity would still run slowly. I would still recommend Xubuntu or Lubuntu.

---

### Post by holycow131415 on 2012-07-05
RAM is very cheap. Upgrade it and still switch to xubuntu or lubuntu for excellent speed. also if you are seeing 418 mb of ram, then your RAM looks like it is dying as that is a very weird number for RAM. So run the memory check that you see on grub to check it.

---

### Post by ajgreeny on 2012-07-05
The strange reported figure for ram is probably because of an integrated video card using some of 512MB ram, or something of that sort.

It may still be worth running memtest86+ from the grub menu, just to double check.  Set it running and leave it for several hours or overnight, and then look for error messages at the bottom of the screen before you manually stop it running (it keeps going till you manually stop it).

---

