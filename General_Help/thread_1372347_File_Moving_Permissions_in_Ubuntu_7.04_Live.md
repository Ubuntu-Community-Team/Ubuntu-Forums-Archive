---
title: "File Moving Permissions in Ubuntu 7.04 Live"
date: 2010-01-04
forum: General Help
---

### Post by Panramos on 2010-01-04
Hello,

I'm using Ubuntu 7.04 on a live boot right now so I can move from files from a hard drive  on a computer that won't boot. This is my work computer, which contains about three years worth of accounting and inventory information that I absolutely must recover from the drive.

The computer runs one SATA drive, and has no ports for additional drives. Otherwise I have two USB drives connected and an IDE connected through a USB adapter. (The SATA drive will not work through the adapter for some reason). I have absolutely no access to another computer with SATA support.

All the drives mount on 7.04, and I can view the files on the SATA drive - which leads me to believe the drive isn't completely dead. So i'm hoping to move the files I need over to one of the USB drives.

However, i'm getting flags when I move files. -Without- installing Linux, is there a way for me to grant myself permissions to move/copy/delete files on my hard drives?

Otherwise, is there a simple way (that won't compromise the data on the drive) for me to re-do the partitions the SATA drive so I can install linux?

---

### Post by snowpine on 2010-01-04
Hi Panramos, try:

```
gksu nautilus
```

This will launch a file browser with root priviledges (very dangerous... be careful!) so you can copy the files to an external drive for backup.

Ubuntu 7.04 is very old (almost 3 years) and unsupported; have you tried using the current version (9.10)? Maybe it has better SATA support.

Whatever you do, don't install Linux, modify partitions, or any other irrecoverable action until you have a backup copy of your 3 years of hard work. Good luck!

---

### Post by Panramos on 2010-01-04
I use 9.10 at home, but i'm used to having it installed. I haven't run an Ubuntu Live CD since 7.04 came out. I tried running Jaunty Live on this computer, however it would just sit unresponsive if I clicked "Try Ubuntu without any change to your computer". So i'm assuming that I don't have the resources to run it on here - Hence the old install.

Nautilus popped up right away, however the disks are still listed as "write-only disks", attempting to change this in the permissions tab just tells me that the action can't be performed because they are write-only disks.

---

### Post by snowpine on 2010-01-04
Can't really help you with Ubuntu 7.04 (never used it personally).

To summarize: you can view the files you want to recover, but 'gksu nautilus' is not letting you copy them to the external drive. Is that accurate? (Please note I said "copy" not "delete" or "move"!!! I also said nothing about "changing permissions" so I'm not sure why you did that.)

If the above is accurate, you've successfully recovered the files and no data has been lost. There are many ways to back up the recovered data (external hard drive, USB flash drive, burn to CD/DVD, copy over network, email to yourself) so don't panic.

If that's not the case, then I'm afraid I don't understand the question. :)

---

### Post by Panramos on 2010-01-04
gksu nautilus brought up nautilus, however - I still couldn't copy/move/delete files (in nautilus) due to write permissions. So I tried to set the permissions in nautilus, it recognized me as root, but I still couldn't change the permissions. Considering my mounted drives are all coming up as write-protected (including externals) I can't even copy files over. There is a lot of information on here, so i'd like to avoid burning it all onto CDs, as it would take forever. If this is my only option, so be it. But if there's a quick way to allow me to just drop these files onto an external drive (in terminal or whatever). That would be ideal.

I do appreciate the help though, this is the furthest i've got on this thing in a week. Freesbie, Knoppix, random other linux installations and even Windows wouldn't recognize the drives. So i'm at least to a point where I can get it done (even if I have to use CD-r's)

---

### Post by snowpine on 2010-01-04
Hopefully you can get the external drive recognized so you don't have to burn a stack of CDs. :) Sorry I couldn't be of more assistance; I've never encountered problems writing to an external drive with the current Ubuntu release.

---

### Post by bodhi.zazen on 2010-01-04
What file system are you using ? With FAT and NTFS you set permissions when you mount the partition.

---

### Post by Panramos on 2010-01-04
The current layout of my drives is~

SATA - NTFS
IDE(USB) - NTFS
USB1 - FAT32?
USB2 - FAT32

---

### Post by bodhi.zazen on 2010-01-04
> **Panramos said:**
> The current layout of my drives is~

SATA - NTFS
IDE(USB) - NTFS
USB1 - FAT32?
USB2 - FAT32

See this link for how to mount and fstab.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Panramos on 2010-01-04
7.04 is mounting everything automatically. It won't recognize standard unmount commands, so I can't reset the drives. I've tried downloading a few programs to get it to work, but Synaptic isn't finding the files from the server. I'm not having much luck on the terminal side either.

I decided then to cut my losses and just burn the information onto CD's. Only to find that there is no CD burner on the computer. (Which, considering how recent the machine is - was very surprising to me)

So i've decided to attack this from a different angle.

Will a **live **cd of Ubuntu 8.04 mount my drives as read/write?

---

### Post by bodhi.zazen on 2010-01-04
> **Panramos said:**
> Will a **live **cd of Ubuntu 8.04 mount my drives as read/write?

Any version of Ubuntu should do this for you. Perhaps it would help if you were to describe your problem better. What have you done and what error messages are you getting?

---

### Post by jamesisin on 2010-01-04
Is there any data on your USB drives where you intend to backup your old information?  If not, you could merely format that drive (with ext3) to accept your data.

Caution: do not accidentally format over your data.

---

### Post by Panramos on 2010-01-05
> Perhaps it would help if you were to describe your problem better. What have you done and what error messages are you getting?

In the GUI, I get write permission errors whenever I try to move files, paste files or delete files. I also get them when I attempt to set drive permissions in the GUI.

In terminal, it flat out doesn't recognize the unmount command, and 7.04 mounts my drives automatically. So in GUI I can't set permissions or move files. In terminal, I can't unmount the drives to reset permissions. This is a live boot, so i'm unsure if the commands are even supported in terminal.

Basically. I have a computer with an internal SATA drive running WinXP Pro that will not boot. I need to recover a handful of files off it. The files are still present, and seemingly intact (as I can view them in ubuntu). The SATA drive mounts, however, I can't slave it as a USB to a windows installation. And so far on the knoppix, freesbie and ubuntu live discs i've tried, i've been unable to mount the drive as Read/Write (or any drive for that matter). All of these live discs are fairly old (with the exception of ubuntu 7.04, the others are at least 6 years old)

I need to mount at least one USB drive as read/write.


> you could merely format that drive (with ext3) to accept your data

If Ubuntu 8.04 doesn't work, I will definitely try this. I can't believe I overlooked it. Thanks.

---

### Post by bodhi.zazen on 2010-01-05
> **Panramos said:**
> In the GUI, I get write permission errors whenever I try to move files, paste files or delete files.

This is not normal behavior. If you get these errors running as root, and across operating systems, then I assume there is a problem with the usb device or partition.

Do you have an entry for your partitions in /etc/fstab? perhaps if you were to post the contents of /etc/fstab ...

> I also get them when I attempt to set drive permissions in the GUI.

I have already answered this question. To reiterate, you can not do this with FAT or NTFS partitions. You have to unmount the partition and re-mount it.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

> In terminal, it flat out doesn't recognize the unmount command, and 7.04 mounts my drives automatically. So in GUI I can't set permissions or move files. In terminal, I can't unmount the drives to reset permissions. This is a live boot, so i'm unsure if the commands are even supported in terminal.

You can not unmount a partition that is in use. Close any applications that are looking at the contents of the drive (nautilus) and cd / , then unmount.

If it does not unmount, this again suggests a problem with the partition.

Simply re-iterating that you are having a problem, continuing to attempt to change permissinos of a FAT or NTFS partition without either editing fstab or re-mounting the partition, without giving us additional information such as fstab , commands you have used, and/or any error messages makes it difficult to help you further.

I suspect that you are not following the directions I gave you because you are having problems with multiple partitions. However it is possible you have a hardware problem .

If all else fails, you can re-format the disk or check your FAT or NTFS partitions in windows.

---

### Post by Panramos on 2010-01-05
I attempted to follow your directions as closely as I could, however using the older version - I couldn't download pysdm, ntfs 3g, or anything really. I'll be the first to admit that my knowledge of terminal is pretty weak, so maybe along the line I got some commands wrong. However, the important functions (such as unmount) weren't working at all. I was being told by terminal that unmount was an unrecognized command, the computer had just been started with 7.04 live boot, and I had nothing but terminal open. I won't even pretend to know why this was happening.

I realize I should've gave readouts of flags and my fstab file. I'm used to windows not doing what I want it to, not linux. If I need to ask a question again, i'll make sure to be more specific about my problems. Thank you for being patient with me.

Anyway! The problem was resolved by merely switching to 8.04. The drives mounted read/write by default and i'm currently backing up my files. Now the only thing I need help with is a clever way to destroy this computer when i'm finished. But I guess that's not really an ubuntu question~

---

### Post by bodhi.zazen on 2010-01-05
In reading your last post , the problem is syntax.

It is umount (one n) NOT unmount (two n's).

This is why you should try to copy-past output from your commands, so we can confirm the syntax and, unlike windows, the error messages are actually helpful =)

If you have problems following, that is fine, just tell us what you did not understand or where you get stuck. Such explanations help us to help you.

---

