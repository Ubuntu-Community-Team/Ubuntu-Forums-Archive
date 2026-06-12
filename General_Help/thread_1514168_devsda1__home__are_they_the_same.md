---
title: "/dev/sda1  /home  are they the same?"
date: 2010-06-20
forum: General Help
---

### Post by medphys on 2010-06-20
Hi all,

I am confused as to the /dev/sda1 partition where all data is stored on my computer and /home which I do not have but it seems to me that they are the same.  If you do a clean install and do not use /dev/sda1 isn't that the same as /home?

Thanks for the insight.

---

### Post by wilee-nilee on 2010-06-20
If you don't build a partition for home separately it is in the main partition. Using sda1 doesn't really mean anything here as you haven't shown us your set up run this in a terminal and post it.

sudo fdisk -l 

l=a small case L

---

### Post by medphys on 2010-06-20
Here is the data from fdisk.

sudo fdisk -l 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42c742c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

---

### Post by jerome1232 on 2010-06-20
So sda1 is mounted as /, meaning it's your root partition and you have everything on it, including everything under /home.

---

### Post by medphys on 2010-06-20
Thanks for the help.  How do I find /home or do I have to create it?

---

### Post by mgnut57 on 2010-06-20
> **medphys said:**
> Here is the data from fdisk.

sudo fdisk -l 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42c742c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris


The results of 
df 
might be more informative. Or:
cat /etc/mtab

---

### Post by jerome1232 on 2010-06-21
> **medphys said:**
> Thanks for the help.  How do I find /home or do I have to create it?

I'm not really sure what your talking about, /home is where all user directories and files are placed, /home/<youruser> is where all of your specific users files are placed. It exists by default.

If you click Places->Home Folder you will be looking at /home/<youruser>.

---

### Post by ronnielsen1 on 2010-06-21
[B]/dev/sda1 is the 1st partition of the 1st hard drive
/dev/sda2 would be the 2nd partition of the 1st hard drive
/dev/sda3 would be the 3rd  partition of the 1st hard drive

/dev/sdb1 would be the 1st partition of the 2nd hard drive
/dev/sdb2 would be the 2nd partition of the 2nd hard drive etc.,
etc.,

In linux everything starts with / (as opposed to C:\)
Everything that follows starts with /

Home is always at /home/username (unless you are using a live cd or accessing a partition that is not the one you're currently using - like a windows partition and then things fall under /mnt or /media)

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

 
[/B]> /home - Linux is a multi-user environment so each user is also  assigned a
specific directory which is accessible only to them and  the system
administrator. These are the user home directories, which  can be found
under /home/username. This directory also contains the  user specific
settings for programs like IRC, X etc.
/lib -  This contains all the shared libraries that are required by system
programs.  Windows equivalent to a shared library would be a DLL file.
/lost+found  - Linux should always go through a proper shutdown. Sometimes
your  system might crash or a power failure might take the machine down.
Either  way, at the next boot, a lengthy filesystem check using fsck will
be  done. Fsck will go through the system and try to recover any corrupt
files  that it finds. The result of this recovery operation will be placed
in  this directory. The files recovered are not likely to be complete or
make  much sense but there always is a chance that something worthwhile is
recovered.
/mnt  - This is a generic mount point under which you mount your filesystems
or  devices. Mounting is the process by which you make a filesystem
available  to the system. After mounting your files will be accessible
under  the mount-point. This directory usually contains mount points or
sub-directories  where you mount your floppy and your CD. You can also
create  additional mount-points here if you want. There is no limitation to
creating  a mount-point anywhere on your system but convention says that
you  do not litter your file system with mount-points.


---

### Post by medphys on 2010-06-21
Thanks everyone for the answers.  I understand it better now.  If I upgrade (a clean install) I would have to do it manually and not upgrade my home directory which resides on /dev/sda1, Is that correct?

---

### Post by Ozymandias_117 on 2010-06-21
With how you have it set up right now, you can't upgrade without overwriting your /home. You would need to manually create a new partition for /home and copy your data to it, then manually partition during install and set the new partition as /home and tell it not to reformat.

---

### Post by warfacegod on 2010-06-21
> **Ozymandias_117 said:**
> With how you have it set up right now, you can't upgrade without overwriting your /home. You would need to manually create a new partition for /home and copy your data to it, then manually partition during install and set the new partition as /home and tell it not to reformat.

I don't think an actual ***Upgrade*** install would overwrite the /home folder unless there was some catastrophic failure. With an Upgrade, that's entirely possible. A fresh install most certainly would overwrite the folder though. Having a separate /home partition is an excellent idea.

---

### Post by medphys on 2010-06-21
Guys,

Thanks for the help.  I know what I need to do now and I understand it a lot better.

---

