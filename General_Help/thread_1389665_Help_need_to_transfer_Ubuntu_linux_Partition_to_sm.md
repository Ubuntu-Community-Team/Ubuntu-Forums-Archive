---
title: "Help need to transfer Ubuntu linux Partition to smaller HDD"
date: 2010-01-24
forum: General Help
---

### Post by PCGuru1836 on 2010-01-24
I have been running Ubuntu for a while now and I need to reinstall windows but Ubuntu is on my largest drive and I need that for windows.
So Ubuntu currently is only using 10GB and 12GB swap on my 320GB SATA drive but I have a 40GB HDD as the CH2 master and I want to know if i can shrink the master partition then copy it to the 40GB along with the swap and then reinstall Windows on my 320GB drive, and I want to do this but GRUB2 or Windows Boot loader needs to show both OS's as I plan to use both.
So is this possible or do I have to wipe Linux and install windows then start all over again on Linux?(I have Ubuntu so heavily customized and my documents and stuff are on it so I cant lose that linux install)
Also Ubuntu never works right when i go to install Inside windows option it crashes after I reboot the PC once to apply new drivers.

---

### Post by PCGuru1836 on 2010-01-24
How about this:
Can i just put Windows 7 on the 40GB HDD without losing the ability to boot linux?
And can i shrink the Linux partition by 100GB so Windows and Linux can share it for Programs/Document?

---

### Post by umechanism on 2010-01-24
I know you can resize a partition using various disc manager tools that are out there for download but moving the partition's image from one drive to the next is risky.  I've imaged drives before and stored the copy elsewhere.  I've later blown away the image on the hard drive only to replace it with my copied image but it was back from whence it came...not a different HDD...which is what you are wanting to do.

Why not just resize your partition giving 1/2 to Ubuntu and 1/2 to Windows?

---

### Post by PCGuru1836 on 2010-01-25
Well i could do that but if i install windows on the same hdd will the windows boot manager show both Windows and Ubuntu?

---

### Post by PCGuru1836 on 2010-01-25
I need help as I need windows on my PC ASAP.

---

### Post by Rrasyrogenees on 2010-01-25
what i did when i had windows dual booted was to give the partitions enough room (resizing your ubuntu partion), downloaded windows, then after it was done used my ubuntu disc to get back to my grub and make windows a part of the grub bootup.  if you do not know how to do that then ask again... but that is the simplified version of my answer.


check out this thread,,, (for dual booting with ubuntu installed first)
[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by J V on 2010-01-25
wtf are you doing with a 12 gig swap? How about taking off 10 gigs or so and seeing how you do then...

---

### Post by PCGuru1836 on 2010-01-25
The Linux setup made the 12GB swap IDK why...
I only have 6GB of ram.

---

### Post by PCGuru1836 on 2010-01-25
OK but how can I resize a partition in linux and install windows and put GRUB back on from the live CD so GRUB loads instead of Windows boot Manager and it has to show both OS(I'm a noob to Ubuntu)

---

### Post by PCGuru1836 on 2010-01-26
please everyone I need help.:(

---

### Post by umechanism on 2010-01-26
Google around this forum for "Grub" or some form of that.  You can most easily search by going to google.com com and typing this string:  "grub site:ubuntuforums.org" or "use windows with grub site:ubuntuforums.org" or "<your search text here> site:ubuntuforums.org". 

A quick search found this:  [http://ubuntuforums.org/showthread.php?t=1050353](http://ubuntuforums.org/showthread.php?t=1050353)

Also, it is not required that Linux be installed first in order to dual-boot with Windows.  I had XP installed first, added Ubuntu in a dual-boot mode, and use Grub to control which one I boot into.  In your case, Linux is installed and you want to add Windows so your Grub is already written.  I would imagine that Windows will write over this grub menu when it installs but I've never done it that way so I'm not 100% sure.  Be sure to back up the grub menu before doing anything.

To edit or resize your partitions, I recommend SystemRescueCD.  It has all the tools you need.  Go here, read and read some more, then download the disc.  [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Search then search some more.  You'll find the answer.

---

### Post by PCGuru1836 on 2010-01-26
...............

---

### Post by louieb on 2010-01-26
No problem - boot a live CD - fire up Gparted - shrink the Linux partition - shrink the swap partition - 
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") 

copy both to the smaller drive 
[Gparted Documentation - Copying]("http://gparted.sourceforge.net/larry/move/move.htm") 

Install grub on the smaller drive. - [Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by PCGuru1836 on 2010-01-27
okay i think i now what to do now so i'm gonna shrink the 298GB Linux partition by 120GB for windows and install it.
This shouldn't wipe out Ubuntu will it? Or will it just wipe GRUB2 and I have to reinstall it?

---

### Post by kdaemon on 2010-01-27
> **J V said:**
> wtf are you doing with a 12 gig swap? How about taking off 10 gigs or so and seeing how you do then...
Maybe he has 4Gg RAM and used the old X3 RAM capacity for swap space

---

### Post by kdaemon on 2010-01-27
It wont kill your Ubuntu install but you will have to re-install Grub. The easiest thing to do is just not bother with Windows, if you really really  need it then virtualise it.

---

### Post by Jackzor on 2010-01-27
Installing windows will NOT erase Ubuntu. But it will erase grub. So what you will need to do is AFTER you dual boot windows you will need to use the Ubuntu live cd and reinstall grub.

---

### Post by PCGuru1836 on 2010-01-27
Actually I have 6GB of DDr2 800 Dual channel ram.

---

### Post by PCGuru1836 on 2010-01-27
> **kdaemon said:**
> It wont kill your Ubuntu install but you will have to re-install Grub. The easiest thing to do is just not bother with Windows, if you really really  need it then virtualise it.
I need Windows because VM's are to slow for Music Mixing and other things i can only do on Windows.(I Know there's Music Mixing programs for Ubuntu but I paid for some Windows only programs)
Most of my PC games are Windows only too.

---

### Post by louieb on 2010-01-28
**Swap space** - just my experience - if you **hibernate** the PC  you will need ram x 1.1.  With 6GB ram 6.6GB swap will work. 
Otherwise 1/2GB swap is usually plenty. 

**Installing widows** Create a partition - make sure its a **primary partition** - format it NTFS (or leave it unformatted) - turn on its boot flag.   When installing windows choose the custom option - that will let you tell the win installer which partition to install in.

Reinstall the Grub boot loader.

---

### Post by alwayshere on 2010-01-28
gparted live cd to edit patitions 

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

or maybe clonzilla live cd to do a backup copy

---

### Post by PCGuru1836 on 2010-01-28
GRUB still boots but at the end of the Win7 install it says "Failed to configure Windows to work on this computer's hardware".
I had Win7 before.

---

### Post by PCGuru1836 on 2010-01-28
Should I try Vista then run an upgrade install?(Yes I have both discs)

---

