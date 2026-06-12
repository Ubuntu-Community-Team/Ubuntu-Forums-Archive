---
title: "Not Booting"
date: 2012-03-25
forum: General Help
---

### Post by Ubun2to on 2012-03-25
Today, I ejected a CD via the hardware-not by right clicking and ejecting. The annoying thing is that when I do this, I have to eject a second time to get it to realize a new disk has been inserted (if any Ubuntu devs are reading this-please fix this problem).
Anyway, I put in a new disk, and realized I needed to refresh it, so I went to right click and eject it, but it locked up. I tried to shut down, but that didn't work either. I had to crash it, and now, after I press what kernel I want to load (generic, recovery, older version), it just sits there and does nothing. No joke.
I've let it sit for over 45 minutes and it has done nothing.
Please help me. And, if this helps, I'm using Ubuntu 11.10.

---

### Post by oldfred on 2012-03-25
Abnormal shutdowns often cause file corruption and you need to run e2fsck to repair files.

 #From liveCD so everything is unmounted,swap off if necessary, change example with sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

If forcing a shut down remember the elephants first:)

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by imachavel on 2012-03-25
if you don't swap off before running fsck and unmount, it can cause serious file damage to run it while the OS is mounted right? As far as I know, this can be done at grub as well(if grub loads), by selecting terminal mode, then running appropriate commands to unmount the file system, and also knowing the appropriate command to run fsck

as for the disk not popping out, that is a hardware mainboard bios error, not an OS issue. When the pc boots, first POST loads, then the bios is read, then a boot device is found(usually the hdd), then the operating file system loads and mounts. I'd imagine the kernel you want to run is recovery.

so force slow shutdown(not halt shutdown) is 

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken 

right? Have to remember alt + print screen(sysrq) and raising skinny elephants is boring

---

### Post by Ubun2to on 2012-03-26
> **imachavel said:**
> 
as for the disk not popping out, that is a hardware mainboard bios error, not an OS issue. When the pc boots, first POST loads, then the bios is read, then a boot device is found(usually the hdd), then the operating file system loads and mounts. I'd imagine the kernel you want to run is recovery.

You don't understand. I can either press the eject button on the computer (on the side of the computer with the USB ports and the power button), or I can right click on the DVD drive icon and eject it. I have to right click and eject for Ubuntu to realize I have put in a new disk.
> **oldfred said:**
> Abnormal shutdowns often cause file corruption and you need to run e2fsck to repair files.

 #From liveCD so everything is unmounted,swap off if necessary, change example with sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

If forcing a shut down remember the elephants first:)

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
Sounds a lot like Windows 98-crash it and it corrupts files (like it gets revenge :twisted:). Anyway, there should be a forces shut down button. Would using Oracle VM VirtualBox make Ubuntu shut down smoother? (It can send the shut down signal or do the virtual equivalent of what I did, press the power button.)
So, where do I run e2fsck? Do I boot from the DVD I burned the ISO on and open terminal to run that? Or do I boot to Ubuntu and do something?

---

### Post by oldfred on 2012-03-26
Any system with power interrupted in the middle of writing a file will have file corruption, normal shutdown prevents that.

You can use any liveCD, DVD or USB. What is important is that system is not mounted which may then cause even more damage as you would be trying to rewrite files in use.

---

### Post by Ubun2to on 2012-03-26
> **oldfred said:**
> Any system with power interrupted in the middle of writing a file will have file corruption, normal shutdown prevents that.

You can use any liveCD, DVD or USB. What is important is that system is not mounted which may then cause even more damage as you would be trying to rewrite files in use.

I booted on my DVD, opened terminal, did what you said, and it said it was an invalid location.
Do I need to somehow boot into terminal (without the GUI)?

---

### Post by oldfred on 2012-03-26
My post shows /dev/sdb1 just as an example. You need to see what partitions are Linux formated with ext2, ext3 or ext4 formats and run the command with each of those.

to see Linux formated partitions.
If you know they are all ext type:
```
sudo fdisk -lu
```
or to also see format (and UUID)
```
sudo blkid
```

---

### Post by Ubun2to on 2012-03-27
> **oldfred said:**
> My post shows /dev/sdb1 just as an example. You need to see what partitions are Linux formated with ext2, ext3 or ext4 formats and run the command with each of those.

to see Linux formated partitions.
If you know they are all ext type:
```
sudo fdisk -lu
```
or to also see format (and UUID)
```
sudo blkid
```

I know virtually nothing about Ubuntu-I can diagnose and fix just about any problem with Windows, but with Ubuntu, I can just navigate around and use terminal (when needed).
I don't really understand what you mean.

---

### Post by oldfred on 2012-03-27
Linux uses drives like sda, sdb, sdc and partition in a drive like sda1, sda2, sda3 etc. Windows confuses drives & partitions by calling all of them drives. A d: drive in Windows may be the second partition on the first drive or the first partition on a second drive or anything else.

So you have to run the commands on the partition on the drive that may have the issue. My example was sdb1 or the first partition on the second drive. You probably do not have a second drive, so that was why it gave an error.

Just use terminal to post list of your drives & partitions using the commands I gave, then I can tell you which partition(s) to run e2fsck on.

---

