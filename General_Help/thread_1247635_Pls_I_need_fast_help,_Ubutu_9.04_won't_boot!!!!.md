---
title: "Pls I need fast help, Ubutu 9.04 won't boot!!!!"
date: 2009-08-23
forum: General Help
---

### Post by Struki on 2009-08-23
Cut the story short, I tempered with filesystem drive in pysdm and probably screwd up boot options or premissions for it, and now ubuntu won't boot. It is related to some sound issues but I figure adding a line in the alsa-base.conf file can't be the reason the whole system won't boot, anyway I figure I need to set back the settings for my filesystem drive to deafults, but the problem is I don't have pysdm in ubuntu liveCD sartup, so is there a way to reset the settings without pysdm?

P.S. I'm realy in tight spot with time here so if any1 could help fast, I'll buy him a beer! thnx

---

### Post by P4man on 2009-08-23
I dont know the first thing about pysdm, but perhaps you can install it from the livecd to access your drives and solve the issue? Its not because its a cd that you can't install anything, it will just be gone the next time you boot the live cd;

---

### Post by bchurchill on 2009-08-23
Well, um, I don't need any beer.  But:

If it's really the /etc/modprobe.d/alsa-base.conf messing the whole thing up you can boot into recovery mode and change it.  If you can't even boot into recovery mode you can use the live cd and mount your hard drive with something like

sudo mkdir /media/sda
sudo mount /dev/sda_ /media/sda

where you change the /dev/sda_ to whatever device your partition is.

sudo fdisk -l

can help you out if you don't know what the device is.

If you don't have a backup of the alsa-base.conf file, you should be able to find a working version of the file in the same place when you boot the livecd that you can copy into your file system.


And if that doesn't work, be way more specific and give us the errors that you're seeing.

---

### Post by Struki on 2009-08-23
@P4man:
This is what I get when I try to install pysdm on livecd:
root@ubuntu:~# sudo apt-get install pysdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pysdm


@[bchurchill]("http://ubuntuforums.org/member.php?u=870534")
I'm 90% sure its not alsa-base but I'll try to copy it from live cd I'll post the erors if I dont make it and btw i can't run recovery mode either

---

### Post by P4man on 2009-08-23
> **Struki said:**
> @P4man:
This is what I get when I try to install pysdm on livecd:
root@ubuntu:~# sudo apt-get install pysdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pysdm


You have to enable the universe repositories first

---

### Post by P4man on 2009-08-23
well, I just had a look at pysdm, it looks just like a gui to fstab or am missing something  ?
Why dont you copy/paste the contents of fstab ? I assume when you boot the live cd, you can mount your disk and access it?

---

### Post by Struki on 2009-08-23
I messed up file premissions all over the place and files , and I installed pysdm on live cd but it didn't help i tried alsa/base file, and some other ideas but i think its a dead issue by now, so baiscly I did a backup and now im just gonna reinstall ubunutu, so thnx for the effort anyway

---

