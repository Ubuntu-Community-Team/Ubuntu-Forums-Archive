---
title: "Changing HD space"
date: 2011-12-30
forum: General Help
---

### Post by africano on 2011-12-30
Hi.....I need to allocate more HD space to my windows 7 boot. Ive got dual boot and only gave 100 gb to my windows 7 install....now I need more space.

Is there anyway of changing this without having to formatt and reinstall anything??

Is it safe?

please help thanks!!

---

### Post by gsgleason on 2011-12-30
1 - make a backup of data
2 - boot to live CD/USB and use 'gparted' to resize your partitions
3 - ????
4 - profit

---

### Post by africano on 2011-12-30
> **gsgleason said:**
> 1 - make a backup of data
2 - boot to live CD/USB and use 'gparted' to resize your partitions
3 - ????
4 - profit

Ive just installed gparted...it finds my HD, and the partitions......the linux partition has arouynd 300 and something gigs and the windows has 100 mb for the OS and around 100 gigs for the C drive.

I can right click on this partition but I cant extend it as the up arrow is greyed out.....I guess some space from somewhere else has to be freed before this?¿

If i right click on the big linux partition I dont have any options of extending or changing the partition.........How do I modify this?

thanks!!

---

### Post by restorator on 2011-12-30
You cant do it from a mounted partition therefore the easiest way is to boot from the ubuntu cd and then run gparted.

---

### Post by africano on 2011-12-30
> **restorator said:**
> You cant do it from a mounted partition therefore the easiest way is to boot from the ubuntu cd and then run gparted.


I dont have the ubuntu cd......can you be specific about what steps I have to do....please?¿!!

thanks!!

---

### Post by xyzzyman on 2011-12-30
Do you have a blank CD/DVD or a spare USB drive 1gb or larger? You will need one to put Ubuntu on and boot from, so you can resize your partitions. Definitely do a backup first of anything you would hate to lose.

---

### Post by chipbuster on 2011-12-30
Back up any data you don't want to lose like xyzzyman said. I prefer just dragging it to a USB drive if there's not too much of it. Putting it into Ubuntu One will work as well, as long as you give it enough time to upload.

Then go here:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

and follow the instructions to make an Ubunutu CD. If you used a CD to install and still have it, that works too. The CD is referred to as a LiveCD because you can run Ubuntu off if it instead of your hard drive.

Insert the CD into your CD/DVD drive, power down your computer, and power it back up. It should show a screen with several options, one of them to "Try without Installing" or to "Run from CD." If it goes directly to your regular screen, let us know. From there, you should get to what looks like a regular Ubuntu system except that its running off of your CD instead of your Hard Drive. That means that the hard drive won't be mounted and you can repartition it!

Note: LiveCDs are SLOWWWWWWWWWWWWWWWWWWWW. If its taking a long time, don't rush it. Maybe grab some popcorn :popcorn:

---

### Post by gsgleason on 2012-01-03
Download the desktop iso then use the usb startup disk creator to make a bootable USB drive (assuming your pc supports boot to usb).  That will be a lot faster and less wasteful than a CD.

---

### Post by africano on 2012-01-09
Okay. just to clear things up.

I have already got a dual boot system up and running. Ive assigned space to my windows 7 install and to my primary linux install.

I want to give more space to my windows install.

Your instructions are to run a live cd (usb) version of ubuntu and through that I will be able to repartition, assign more space to my windows install....

What are the chances of me loosing data? or messing up my files and things on both my windows install and my linux?¿

thanks.

---

### Post by MartijnNL on 2012-01-09
Resizing a partition is always a bit risky. That's why gsgleason advised you to backup your data first.

I'm not sure whether gparted is present on a live cd. You may have to install it first. (While running the live cd/usb).

There's also a live cd/usb from gparted itself: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Mark Phelps on 2012-01-09
> **africano said:**
> What are the chances of me loosing data? or messing up my files and things on both my windows install and my linux?

If you SHRINK Win7 OS partitions using GParted, the chances are pretty good that will corrupt the filesystem and render Win7 unbootble.  But, don't know about GROWING the partition -- that may be OK.

Either way, the FIRST thing you should do BEFORE you mess with the Win7 OS partition is use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will provide you a way to repair the Win7 boot and filesystem -- should you need that later.

It's hard to advise you without seeing what you have on your drive, so open a terminal in Ubuntu and enter "sudo fdisk -lu" (lowercase L, not a one). That will list out the partitions on your drive.

If your drive is already full, then allocating more space to ANY partition is going to first, require removing space from an adjacent partition.  Can't advise you without seeing what you have in place.

---

### Post by africano on 2012-01-09
Thanks - 

This is what I have:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x0007a9c2

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   206723071   103258112    7  HPFS/NTFS/exFAT
/dev/sda3       206723072   879116287   336196608   83  Linux
/dev/sda4       879118334   976771071    48826369    5  Extendida
/dev/sda5       879118336   976771071    48826368   82  Linux swap / Solaris
africano@Africano:~$ 

So can you please help me with specific instractions?

How I should do it to give more space to my windows boot as I now have to work with big files on my windows boot and Im running out of space.

Oh and how do I back up my windows 7.

thanks!

---

