---
title: "Trying to move to new HD"
date: 2011-10-02
forum: General Help
---

### Post by AlexBooton on 2011-10-02
Hi,

I've got U11.04 running on a 400gb drive; and want to move it to a 2tb drive.

Both drives are running on the system.  /dev/sda is the old 400gb drive; and /dev/sdb is 2tb.  I'm booting from /dev/sda.

I thought I could use GParted to do the move.

But GParted won't let me operate on the new drive.  It says it has to be unmounted but won't unmount by itself.  It says "Most likely other partitions are also mounted on these mount points."

So how do I unmount this drive so that I can operate on it?  How do I find those other partitions?

Thanks

---

### Post by oldfred on 2011-10-02
Post screenshot from gparted of new drive and/or 
```
sudo fdisk -lu
```

Many suggest one of these:
Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

I prefer a clean install. That automatically housecleans all histroy. You avoid issues of duplicate UUIDs and reinstalling grub2''s boot loader. You then can copy some or all of /home into your new /home and reinstall apps from a list.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by AlexBooton on 2011-10-02
Hi,

I think I'll try one of your alternative suggestions.  

I'm looking at the Clonezilla page you referred to; but don't see anything about moving to a larger drive AND expanding the original partition to fill the new drive.

Do you know if it does this?

I'd prefer to NOT do a clean install b/c I've configured the system to my liking.  I'd just as soon not have to do it again.

Thanks!


Here's the detail you asked for.  Please note: In my original post I said the 2tb drive was /dev/sdb.  In actuality it's /dev/sdc because I've got a USB stick in the PC.

```
Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000eed8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   773296127   386647040   83  Linux
/dev/sda2       773298174   781422591     4062209    5  Extended
/dev/sda5       773298176   781422591     4062208   82  Linux swap / Solaris

Disk /dev/sdb: 3999 MB, 3999268864 bytes
82 heads, 18 sectors/track, 5292 cylinders, total 7811072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7811071     3901504    c  W95 FAT32 (LBA)

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000eed8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   773296127   386647040   83  Linux
/dev/sdc2       773298174   781422591     4062209    5  Extended
/dev/sdc3      3898904576  3907028991     4062208   82  Linux swap / Solaris

```

---

### Post by oldfred on 2011-10-02
I have not used clonezilla, as I prefer the clean install. If you copy /home that has all your user settings.

If you copy partition over, then you can use gparted to resize. But if moving a lot of data can be a slow process.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by kio_http on 2011-10-02
You could do a clean install then copy your home folder. Or you could do a dd copy on the new drive.

If you want you can also install ubiquity on the Ubuntu installation on the old drive and use it to clone your ubuntu install on the new drive.

---

### Post by AlexBooton on 2011-10-02
Hi,

Thanks to both of you for your assistance.

I tried and gave up on Clonezilla.  It got about half way through the operation and then failed.  I tried twice and then figured it just wasn't worth it.  

It may work, and probably does, if you know how to use it but I was unwilling to take the time.

So I'm in the process of doing a clean install.  

Unfortunately, it's not as simple as copying the home directory.  I've installed software and made some configuration changes which may be troublesome to try to reproduce accurately.

Copying /etc might help but won't install the software I've added.  Is copying /etc a bad idea?  What do you think?

After the install I'll look into ubiquity.  I'm unaware of this package; but if it allows me to make a clean copy onto the new/larger partition; I'll be a very happy camper.

Thanks again

---

### Post by AlexBooton on 2011-10-02
OK,

I now have both drives running.  The old drive is the one I booted from; the new/larger drive is mounted as /media/<a looong string>.

I think the long string is the disk serial number; but that's not important.

Now, can I just copy all the directories and files, excluding a few dirctories:
/media
/boot
/cdrom
/dev
/lost+found
/mnt
/opt
/proc
and maybe a few others?

If memory serves, I think I've seen examples of a simple command (maybe using cp or dd?) to do just this.

Any thoughts?

Thanks

---

### Post by oldfred on 2011-10-02
If it is exactly the same version and both are up to date, it may work. Generally I suggest just copying /home and only the settings in /etc that you have manually modified. But that is for a new install.

Do you have the .debs or other apps you installed. If from the repository the instructions I ran will let you reinstall all the Ubuntu apps.

Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>

But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,

---

