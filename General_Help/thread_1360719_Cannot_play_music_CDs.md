---
title: "Cannot play music CDs"
date: 2009-12-21
forum: General Help
---

### Post by TWO on 2009-12-21
Hello.

I'm currently using Kubuntu Karmic Koala on a Dell Inspiron 1300, with all the latest updates applied as of 21 December 2009, and have found that I can neither view the contents of an audio CD in Dolphin, nor play the contents in any multimedia program such as VLC or Amarok.

I am using an external CD/DVD drive (Freecom), but I know it isn't a hardware issue since the drive is able to identify DVD Video within Linux and works with audio CDs within Windows. (The internal cd/dvd drive no longer works.)

To repeat the steps, I simply insert an Audio CD.

The Device Notifier recognises that a disc has been inserted, simply listing the disc as "volume," however when trying to browse the medium with Dolphin, I'm presented with the "Can not read" error. 

If I attempt to play the CD with Amarok via the actions menu, Amarok simply doesn't start. Attempting to play the disc via VLC is also unfruitful. 

Incidentally, both K3B and SoundKonverter recognise that there are files on the disc.

Could anyone suggest a solution?

lsusb:

```

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 062a:0000 Creative Labs Optical mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 07ab:fcdf Freecom Technologies
Bus 001 Device 002: ID 05dc:a768 Lexar Media, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```cat /etc/fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2080ffe4-9dc8-4b81-aad7-9cecdfe8712e /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e385c272-650b-4efe-b7f0-5b4933e18cc5 none            swap    sw              0       0


```If you require any more details, please let me know.

Thanks in advance
TWO

---

### Post by Mark76 on 2009-12-21
Have you tried Decibel Audio Player?

It works for me.

---

### Post by OldGrantonian on 2009-12-21
Try the "Multimedia & Video" forum:
[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)
.

---

### Post by TWO on 2009-12-23
> **Mark76 said:**
> Have you tried Decibel Audio Player?

It works for me.

Hey. It's not so much that my preferred programs don't work with it but more to do with the fact that even Dolphin is not recognising music CDs.

> **OldGrantonian said:**
> Try the "Multimedia & Video" forum:
[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)
.

Any chance this thread could be moved to that category?

---

### Post by Mark76 on 2009-12-23
> **TWO said:**
> Hey. It's not so much that my preferred programs don't work with it but more to do with the fact that even Dolphin is not recognising music CDs.

I have the same problem with my FM of choice. I think it's a Linux thing rather than a specific fault of Dolphin.

---

### Post by TWO on 2009-12-28
OK. 

So I have installed ubuntu-desktop, and I am able to view/play music CDs with Nautilus and Rhythmbox and yet still unable to see the CD/play them under Kubuntu.

VLC is able to play the CD under Ubuntu, but not without jumping.

Has anyone else experienced this?

---

### Post by SlappyPappy on 2010-01-02
Playing CDs is a mess in Kubuntu.

I can't get it to play any CDs regardless of the program.

You'd think this would be one of the simplest aspects of an OS but apparently it's a big problem. 

I too can't get Dolphin to recognize audio CDs, it simply sees them as having no data on them 0 kb. 

When is Kubuntu going to get fixed? I'm hoping in the next release.

---

### Post by TWO on 2010-01-10
> **SlappyPappy said:**
> Playing CDs is a mess in Kubuntu.

I can't get it to play any CDs regardless of the program.

You'd think this would be one of the simplest aspects of an OS but apparently it's a big problem. 

I too can't get Dolphin to recognize audio CDs, it simply sees them as having no data on them 0 kb. 

When is Kubuntu going to get fixed? I'm hoping in the next release.

I'd make do with GNOME for now. Something has gone drastically wrong with KDE and/or Kubuntu for this release. I can't even get Amarok to play mp3 files under a GNOME system. Bizarre! 

In the meantime, I do recommend that people try out the latest edition of Songbird, because it is truly magnificent! :-D

[http://www.getdeb.net/install/songbird/1.4.3-1~getdeb1](http://www.getdeb.net/install/songbird/1.4.3-1~getdeb1)

(You will need the **apturl **package installed for that link to work mind!)

---

### Post by BubbaBlues on 2010-01-18
It isn't a Kubuntu thing, it's a kde4 thing. It sucks.  I stopped using pclos only because of this very reason. The are changing to kde4 and audio cd's and dvd's won't play. I came back to Ubuntu with gnome and everything works great.  So I installed Kubuntu on my other system and it's the same old crap. Can't play audio cd.s.   I love Ubuntu and I love gnome because like they say, "it just works".

---

### Post by llamabr on 2010-01-18
I'd guess that kde is mounting the disk as data.  with an audio cd you don't want it to mount.  Rather, the software will play the tracks on the cd via a different interface.

so, check df to see if it's mounted.  If so, unmount it, and then see if your player will play it.

---

### Post by wandalalakers on 2010-05-20
This problem still exists in kubuntu 10.04.
I'm kinda disappointed because I use LTS versions.
So, I just switched from kubuntu 8.04 to 10.04 and assumed playing a CD would work.
I can't load a music cd on /dev/sr0 either.
I can't even get amarok to play a mp3.
I was going to donate to kde.org but if playing an audio cd in amarok or opening an audio cd in dolphin, doesn't work, why do it?
It's a known bug in a dual drive system dolphin won't open an audio cd in /dev/sr0.

---

