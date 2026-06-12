---
title: "Need to recover File"
date: 2006-05-26
forum: General Help
---

### Post by tikig on 2006-05-26
First off I am a noob to Linux. 

That said, I tried to load a legacy driver for my Nvidia card TNT2, followed some crazy directions, didn't work and I dusted the gui. Problem is I had previously saved some open word documents to my desktop and I would like to recover them.

I'm not good with the line editor (learning), so I removed the hard drive, took a spare I have and reloaded the system. My question is this, can I know plug the old hardrive back into the 2nd IDE channel as master, and have access to the desktop files of the old system? Not certain how this works in Linux.

If so where is the desktop stored (which directory)? 

I'm tech savvy, learning linux for the first time. Ubuntu is really cool. Just starting my linux learning curve.

Thanks in advance to all who assist me.

-Tikig

---

### Post by aysiu on 2006-05-26
Plug in the second drive and then post back the output of these terminal commands? ```
sudo fdisk -l
df - h
cat /etc/fstab
``` I know the terminal may be scary if you don't know what you're doing, but I'll walk you through it--it's not as bad as you may think.

**Edit**: I wrote a little guide that will help you:
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by tikig on 2006-05-27
aysiu,

Thanks for creating the tutorial. I think I made some progress not working yet though.. I did edit the file with nano see below. Note: the Gparted app only saw the 120GB drive. The 40Gb is the one with the data I need off the old desktop.

My output from your original request is:

oommoo@oommoo:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14523   116655966   83  Linux
/dev/hda2           14524       14593      562275    5  Extended
/dev/hda5           14524       14593      562243+  82  Linux swap / Solaris

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4795    38515806   83  Linux
/dev/hdc2            4796        4865      562275    5  Extended
/dev/hdc5            4796        4865      562243+  82  Linux swap / Solaris

oommoo@oommoo:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             110G  1.9G  103G   2% /
tmpfs                  94M     0   94M   0% /dev/shm
tmpfs                  94M   13M   82M  14% /lib/modules/2.6.12-10-386/volatile

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc1       /storage        ext3    defaults        0       0

When I go to the storage folder, nothing is in there. What do I do now? Thanks  I appreciate it,

-Mark

---

### Post by aysiu on 2006-05-27
Whoa! You just reminded me I left something crucial out of that tutorial.

After you change the /etc/fstab file you have to issue this command to have that change take effect: ```
sudo mount -a
``` Then you do the *chown* and *chmod* commands after that.

Sorry. I've fixed the tutorial now.

---

### Post by mjziegle on 2006-05-27
Sounds like it's not mounted correctly.

Temporary fix

sudo mkdir /mnt/old_drive
sudo mount /dev/hdc1 /mnt/old_drive

It's an ext3 drive so it won't require any funky options.  This should just work.  Otherwise post the error message.

---

### Post by tikig on 2006-05-27
aysiu,

I could hear the drive spin up as soon as I typed that last command,  and found the files! That was great. Okay last question, I'm going to unpug that old drive now. Do I have to change anything?

How do you remove an internal drive?

-Mark

---

### Post by aysiu on 2006-05-27
Turn off the computer before you remove the drive.

I think that's it.

---

### Post by tikig on 2006-05-27
Thank You.

Gnite

Mark:-D

---

### Post by aysiu on 2006-05-27
Glad it worked out. By the way, I revised the tutorial so that it tells you how to view the second hard drive in GParted.

---

