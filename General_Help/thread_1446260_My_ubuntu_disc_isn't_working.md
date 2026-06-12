---
title: "My ubuntu disc isn't working"
date: 2010-04-03
forum: General Help
---

### Post by JustinZTerrible on 2010-04-03
I downloaded a live disc and installed ubuntu. The following day it wouldn't boot up so I went to deleting the partition. I got ripped off $100 because they had no clue what to do so they wiped my drive and reinstalled just windows instead of just using a recovery disc and typing "fxmbr". My friend borrowed me his ubuntu disc and I purchased another drive so that each OS could have its own drive. Well now neither of our discs work. Mine is a downloaded one his is one he was sent from Ubuntu. Please help, I am downloading another iso right now.

---

### Post by JustinZTerrible on 2010-04-03
I am burning the ISO right now I will be attempting to install it to the new HD

---

### Post by linden940 on 2010-04-03
is your cd the first thing that in the boot up? if you dont know then go to your biso screen and look at the boot order...you want it the cd first!! then your drives then save an try should work

---

### Post by dacoolio on 2010-04-03
I may be misreading this but is your problem with the disks themselves or the installation? If its with the disks, make sure you do an md5 check on the .iso when you download it, and burn it to the CD at the lowest speed to lessen the chance of mistakes. I may be mistaken, but I think there is an option once you boot to the CD to check the disk.

---

### Post by JustinZTerrible on 2010-04-03
on trying the new iso that I burnt I tried installing and it wouldn't recognize any drives. I unplugged the main drive to keep it from interfering with windows 7.. after a few minutes a flashing white ubuntu image comes up for a while then switches to a screen that is black and says it couldn't find a live drive?

---

### Post by JustinZTerrible on 2010-04-03
when I type help a list of commands came up.. mount was one of them.. but if I typed one of the four mount options I didn't know what to mount them to...=(

---

### Post by JustinZTerrible on 2010-04-03
should I try installing through windows? or what should I do? I really like linux I used it for about 3hours when I had it working.. I have 1tb drive for windows and a 160gb drive I was going to use for linux.. please help me out..I am not good at partitioning..

---

### Post by dacoolio on 2010-04-03
I'm sort of lost on where your problem is. Are you able to boot off the LiveCD into a graphical environment? If so, you can partition using GParted as included in the installer.

If its falling back to a command line, try typing "startx" or "xinit" to enter GDM

---

### Post by JustinZTerrible on 2010-04-03
hmm.. well I tried booting without the regular 1tb drive plugged into the board.. cause I don't want it to interfere with my windows 7.. the interface that has  "UBUNTU" then options under it such as try ubuntu without any changes, and install.. I tried both of those.. the graphical interface never comes up after a white ubuntu logo shows up.. and the install option yeilds the same logo but then goes to a black screen and after then it goes to a screen saying it can't find the live drive?

---

### Post by dacoolio on 2010-04-03
I've never experience a "live drive" problem, but occasionally something similar happens where I cannot boot into GDM. I would suggest scrapping that CD and burning a new one. Make sure to check the md5sum of the image you download to ensure that it is correct. Also, make sure you burn the CD at a low speed.

$md5sum image.iso

Check the output against the md5sum supplied by the download site.

---

### Post by JustinZTerrible on 2010-04-03
4th cd.. this is getting aggravating.. I get nothing other than the menu that comes up after booting from disc.. a black screen with a blinking white ubuntu symbol then nothing if I try the first option. If I try installing I get nearly the same result.. please someone help..

---

### Post by JustinZTerrible on 2010-04-03
I am afraid my thread will get knocked to the next page and I'll never get this working.. please anyone.. help

---

### Post by Chronon on 2010-04-04
Are you using 64-bit OS?  I wasn't able to get x86_64 versions of either Ubuntu or Kubuntu 9.10 to boot on my machine (I did check md5 sums on both LiveCDs).  I eventually installed Zenix (an Ubuntu-based remix) and had no problems installing this on my machine.  

It seems that something about my hardware posed problems for the standard install disks and I could never get them to boot or install.  Maybe you can use an Ubuntu based distro that uses the standard repositories in order to install.

---

### Post by JustinZTerrible on 2010-04-04
I am using 32bit ubuntu but 64bit windows? it shouldn't matter if I'm disconnecting the windows drive.

---

### Post by JustinZTerrible on 2010-04-04
I really need help here guys... please.. anyone..

---

### Post by Monotoko on 2010-04-04
Have you tried using another computer and another program to burn your disk? Also try another distrobution of linux and see if that loads up..you can find loads by searching google.

You could also try and boot it from USB stick: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Also make sure whoever installed windows 7 didnt mess up any BIOS settings.

---

### Post by JustinZTerrible on 2010-04-04
What's the difference between ubuntu and kubuntu?

---

### Post by RJ12 on 2010-04-04
> **JustinZTerrible said:**
> What's the difference between ubuntu and kubuntu?

Just the way the interface is and programs (they do the same thing though)

Kubuntu: KDE Desktop Environment
Ubuntu: GNOME Desktop Environment

---

### Post by JustinZTerrible on 2010-04-04
well does anyone think Kubuntu will work in my situation?

---

