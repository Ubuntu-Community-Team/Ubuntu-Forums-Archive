---
title: "Suggestions, advice and pointers: Reinstall, backup &amp; restore dual boot."
date: 2012-05-08
forum: General Help
---

### Post by magusta on 2012-05-08
Hi there,

I currently have a single boot ubuntu 11.04 system on a 2tb disk - very basic. however, i wish to back it up, wipe the disk, repartition, install w7, then reinstall 11.04 and restore my distro as is. 

i know how to wipe, repart, reinstall. what should I backup and restore to achieve a dual boot system? advice very welcome

---

### Post by magusta on 2012-05-08
or resize the 2tb, create ntffs part, install w7 killing grub. boot livecd - fix grub?

---

### Post by sudodus on 2012-05-08
I would backup the personal files, documents, photos, video clips etc, and then start with a clean disk:

- make partitions
- install Windows
- test *ubuntu 12.04 live booted from a CD or USB drive
- install the *ubuntu flavour, that you like after testing

Decide whether you want to make a completely clean install, and only copy back your personal files, or if you would like to make a separate /home partition! There are tips about that in several threads here at the Ubuntu Forums.

Why do I suggest 12.04? Because 11.04 end of life is October 2012 (less than 6 months to go), while 12.04 is an LTS version with several years to go (except Lubuntu).

---

### Post by oldfred on 2012-05-08
I agree with sudodus.

But if you want full image backup:

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

I prefer clean installs but you do have to backup /home, maybe system settings in /etc if you hand customized any. If you have installed lots of applications you can export a list and reinstall.
My backup plan is a new clean install and restore from my backups.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

Another alternative, just install the new version.
With 2TB, do you have lots of room? I install Ubuntu in 25GB / (root) partitions with data in separate partitions. Then I can install the new version, make sure it works and copy over anything I forgot and then fully convert. I was going to delete the old one's but I have enough room that so far I still have every install since 9.10 and a few others for testing. So many now it is not easy to manage.

Windows can be installed to any primary partition sda1 thru sda4, so it does not have to be sda1. It needs to be formated NTFS with the boot flag. If just installed to unallocated space it will try to use two primary partitions, one a hidden 100MB boot/repair partition.

---

### Post by magusta on 2012-05-09
i bow in the long shadow that is your magnificence...thanking you !

---

