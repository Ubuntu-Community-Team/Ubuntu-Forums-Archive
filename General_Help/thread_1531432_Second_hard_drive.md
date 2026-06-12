---
title: "Second hard drive"
date: 2010-07-15
forum: General Help
---

### Post by dlrocket89 on 2010-07-15
Hi all,

Just rebuilt my main computer, now have a 40GB SSHD and a 1 TB "standard" HD.  OS and whatnot is installed on the 40GB, the 1TB is sitting there unformated.  I need directions to do the following (or, directions to get to directions for the following):

1) need to format the 1TB HD
2) need to get a link to that created in the K-menu "Favorites" section (running Lucid Kubuntu BTW)
3) need to find and install some software to auto-backup selected directories from the 40GB drive to the 1TB drive...any recommendations?

Output from -sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e005d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4661    37431296   83  Linux
/dev/sda2            4661        4866     1648641    5  Extended
/dev/sda5            4661        4866     1648640   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table




Obviously, /dev/sdb needs to be formatted.  Please help, and thanks in advance!!!!

---

### Post by CharlesA on 2010-07-15
I don't know if Kubuntu has gparted, but you can create the file system from there.

---

### Post by cariboo on 2010-07-15
Like CharlesA suggested install gparted and use it to partition and format the drive. The drive should show up in the file manager, where you can add it to Favourites.

I personally use grsync for backups, but you can use rsync, and create a cron job.

---

### Post by CharlesA on 2010-07-15
+1 to rsync.

grsync is just a graphical frontend to it.

---

### Post by dlrocket89 on 2010-07-15
Got it, thanks everyone!

I'm starting to know how to use ubuntu (kubuntu in my case) better, most of the time I don't know what the software that I need is called.  Thanks again!

---

### Post by oldfred on 2010-07-16
If you are doing a new install and want to reinstall the latest versions of all your applications:

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,

---

