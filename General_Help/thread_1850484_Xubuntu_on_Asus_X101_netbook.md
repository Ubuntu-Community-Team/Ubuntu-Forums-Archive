---
title: "Xubuntu on Asus X101 netbook"
date: 2011-09-26
forum: General Help
---

### Post by primvirlaux on 2011-09-26
Hey.

I'm new to the forum, sorry if my question is in the wrong category (wasn't sure whether to post there, in 'hardware' or 'installation')

My question is: I bought the new Asus X101 netbook, and I thought about installing xubuntu on it, but I'm not sure if it's a good idea.

Tthe X101 should have enought RAM (1GB), but the problem is the very small HDD: it only has a 8GB SSD.

Can someone help me out here? I'm wondering if it actually makes sense to install xubuntu on such a small disk... is there a way to customize the installation and reduce the installation size. If so, should I use the standard installer or the alternative installer (what's the difference?).

Any help is appreciated!

---

### Post by Topsiho on 2011-09-26
I have Ubuntu (10.04) on my netbook (Acer Aspire One), 512Kb RAM, and an SSD of 8 GB, Atom processor of 1.6GHz.
It works well, but only just, and contrary to my habit I have no separate partition for /home on it. 7 GB for /, and 1 GB swap.

It runs well, but every now and then the screen greys, and the system freezes for a few (or more) seconds, and then the computer continues. I love it.

If you run Xubuntu or Lubuntu on yours, and run lighter programs, (e.g. Abiword, in stead of OpenOffice or LibreOffice), your computer will probably run far better than this. Anyway: you could try it. If your expectations are not unrealistically high, then you'll not be disappointed :)
The reason that I don't run [X,L]ubuntu on my netbook is that I am quite exhilarated that a full swing Ubuntu runs so well on this little machine. Just part of the fun ... If I need speed I use my desktop, which just flies.

Topsiho

---

### Post by primvirlaux on 2011-09-27
Thanks for the reply, Topsiho. I guess xubuntu should run even faster then. But can someone who uses xubuntu give some more technical details, i.e. how much space does a typical xubuntu installation take? I was a bit surprised I couldn't find that information on the xubuntu webpage.

---

### Post by keithpeter on 2011-09-27
> **primvirlaux said:**
> Thanks for the reply, Topsiho. I guess xubuntu should run even faster then. But can someone who uses xubuntu give some more technical details, i.e. how much space does a typical xubuntu installation take? I was a bit surprised I couldn't find that information on the xubuntu webpage.

Hello primvirlaux

I've got a beta install of xubuntu 11.10 on an Asus 1000 netbook, the one with an 8Gb ssd and a second 32Gb ssd. I use the 8Gb for / and the bigger one for swap and home. I have 1Gb of ram,

I've got 3331 blocks (not sure if these are GiB or Gb) in use at present, but that includes stock Xubuntu plus libreoffice and some other bits and pieces. You can knock half a gig off the 3331 for libreoffice alone.

In the past, I have installed without any swap, and I got the 'grey out' mentioned sometimes, usually with firefox, but it always seemed to work. I started putting a swap partition back on for hibernating to disk. The ssd seems to be holding up.

There are some tricks for ssd storage on the bhodi linux wiki, but I haven't tried these under 11.10 yet. Used them with 10.04 and saw some benefit.

[http://www.bodhilinux.com/wiki/doku.php?id=ssd_disk_-_run_bodhi_from](http://www.bodhilinux.com/wiki/doku.php?id=ssd_disk_-_run_bodhi_from)

```
keith@EeePC:~$ df -m
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda1                 7575      3331      3859  47% /
udev                       490         1       490   1% /dev
tmpfs                      199         1       198   1% /run
none                         5         0         5   0% /run/lock
none                       497         1       497   1% /run/shm
/dev/sdb1                28166      3673     23063  14% /home
```

There was some discussion some time back about a minimum partition size below which the installer would complain. It was a bit higher than Xubuntu actually needs

---

### Post by primvirlaux on 2011-09-27
Thanks, keithpeter, this helps a lot. Which installer should I use? I can either download the 'Desktop CD' installer or the 'Alternate install CD'?

---

### Post by keithpeter on 2011-09-27
> **primvirlaux said:**
> Thanks, keithpeter, this helps a lot. Which installer should I use? I can either download the 'Desktop CD' installer or the 'Alternate install CD'?

I just used the desktop installer as I use a usb stick to boot off. I actually burned a Xubuntu beta cd, booted another computer from that, then used the live usb creator to transfer the iso to the usb stick, then booted the Asus from that, ran a live session, and checked all the hardware worked. Then installed from the live session.

Anyone think this will be a bad idea with just the 8Gb?

PS: what is the keyboard like on that ASUS? The EeePC 1000 is a bit bendy for my taste

---

### Post by primvirlaux on 2011-09-29
Tried to run a live session yesterday and it didn't work. (xubuntu-11.04-alternate-i386, put on a USB with unetbootin). I'll try again tonight, perhaps something is missing on the USB. When starting the X101 from the USB, I'm asked about region/keyboard layout, then the process gets stuck when it looks for a network card.. I don't need a connection to the Internet to run a live session or install the OS, right?

>  PS: what is the keyboard like on that ASUS? The EeePC 1000 is a bit bendy for my taste
The keyboard is okay, I think, doesn't bend much. THe keys are small, but I can reliably hit them. Sure, nothing for writing long documents, but enough for emails/notes. A bigger problem is the touchpad: the touchpad buttons are really loud, too loud to use comfortably in a library. Guess I'll have to get used to using touchpad tap as left click...

---

### Post by 2F4U on 2011-09-29
You need an internet connection if you select the check boxes for updates and non-free software such as MP3 support and flash player.

---

### Post by primvirlaux on 2011-09-29
Okay, it worked. I was able to run a live session of Xubuntu using the Desktop installer, and it worked perfectly. In the end however I decided to install Lubuntu; they were both comparably responsive, but I I just liked the look of Lubuntu a bit better. I hope it wasn't a mistake, though: for some reason, after I installed Lubuntu, whenever I open the 'keyboard and mouse preferences' window it crashes after I change something, which didn't happen during the Xubuntu live session.

---

### Post by frenchrh on 2011-10-01
Hi All,  Maybe we can make this our Ubunut on Asus X101 thread.  

I'm running Kubuntu 11.10 beta 2 on the Asus X101, quite successfully.  Using 2Gb Ram (upgraded from 1Gb it comes with) and with 16 Gb microUSB drives for people to store their files on.

Love the computer.  I plan to setup 9 of these for my group.

A question I have is how to set it up.

So 2 questions.
      1. If I set these up on 11.10 beta2, can I just do a sudo apt-get dist-upgrade to get the full on release copy of Kubuntu 11.10 when it comes out?

      2.  So 2Gb Ram, and root partition on the 8 Gb SSD, 
          2a) should I make a 2 Gb Swap on the SSD?
          2b) should I have home partition on the 16 Gb microSD card?
       I have home partition on the microSD card, and get peridoic, can't write to config file to a hidden directory over there.
       So maybe I need to keep home on the SSD, and just put a link for Documents in the microSD card.

        2c) Could I put swap partition on the microSD card?
        2d) If I don't use a Swap partition, then I can't have the X101 automatically hibernate if its battery is going to run out. So that seems dangerous.   I like the auto-hibernate setting.

---

