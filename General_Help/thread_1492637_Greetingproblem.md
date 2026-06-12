---
title: "Greeting/problem"
date: 2010-05-24
forum: General Help
---

### Post by thyregrut on 2010-05-24
Hello!

First of all, I am a new Ubuntu user. I am loving it! A friend of mine has used Ubuntu for awhile now and kept suggesting it to me. I've had few problems, and most could be fixed.

Anyway, I apologize in advance for not putting this in the right place(if it's in the wrong place), and for this question dealing with Windows. I understand if it can't or won't be answered.

As most of you probably know, Windows has some things you can only do in windows, or else it's really hard to do a work around(at least to me anyway). I partitioned my hard drive and wanted to have Ubuntu on one partition and Windows XP on the other. I partitioned it with Gpart on a Puppy live USB and everything went great. I lost no information and things were good. They were good until I put in three different windows xp installation discs and all of them stopped working.

They load all of the files and then when windows tries to start the installation, it gives me the BoD, or the stop: 0X0000007B error. It says it has a problem with the hard drive and needs to shut down for safety. I can never get past this point.

I would appreciate any and all help! If you can direct me elsewhere, I also appreciate, and I will understand if you can't answer this or don't want to help!

:)
Thanks!
Thyregrut

---

### Post by -humanaut- on 2010-05-24
Can you open a terminal and type: cat /etc/fstab

I'd like to see how your drives are partitioned why didn't you use ubiquity to partition the drives?

---

### Post by thyregrut on 2010-05-25
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e7ce6b66-2b5e-40c3-b88b-5841b94fd24e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3643a441-b4a2-4658-97fa-9dc6dda0a60a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


*I am a noob. Sorry, but that is all I can say to that question. Is it better or something?

---

### Post by -humanaut- on 2010-05-25
What I'd recommend honestly is using ubiquity (the installer from Ubuntu) and reinstalling there really isn't a need to use Puppy and Gparted to partition your drives (which can cause problems when you don't know what you're doing) Follow the installation routine on Lucid Lynx that should remedy your situation.

---

### Post by thyregrut on 2010-05-25
Unfortunatey I reinstalled ubuntu LTS and the windows installation process still failed. During the process I assigned swap space to one side of the hard drive and had ubuntu  go to another part. I mounted it on / at the time, ext4, and it was classified as primary. Both it and swap were classisfied as primary...


updated cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=59fd0223-d614-4a1f-af98-21de3386d428 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=596b8ffd-f591-4535-8af2-c8474e96a9aa none            swap    sw              0       0

---

### Post by -humanaut- on 2010-05-25
Seems like your windows error is rather common. I'm not too familiar with windows fixes but heres a link [http://support.microsoft.com/kb/324103](http://support.microsoft.com/kb/324103) I hope this helps you're disk or harddrive maybe faulty.

---

### Post by thyregrut on 2010-05-26
Thank you for your help Humanaut!

---

