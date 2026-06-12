---
title: "GParted missing partition table + somewhat-related help with upgrade"
date: 2012-03-01
forum: General Help
---

### Post by /bee/ on 2012-03-01
GParted missing partition table:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=aed83e83-ccc6-4ecb-9ceb-e6e9a6b77aa1 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=8628f6bc-10dc-4387-bdae-78d13104b289 /home           ext3    defaults,user_xattr        0       2
# /media/Maxtor was on /dev/sdb1 during installation
UUID=3A388D2E388CEA69 /media/Maxtor   ntfs    defaults,umask=007,gid=46 0       0
# /media/MyBook was on /dev/sdc1 during installation
UUID=CE0C0B8F0C0B71AF /media/MyBook   ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda2 during installation
UUID=2c1b2ae0-b3e0-4133-88fc-00c0938a7df5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
**Solved** this issue with the wonders of fdisk mxfw and a reboot.  (I checked grub/fstab first to be sure UUID was being used and not /dev/sda1...)

**Help with upgrade:**
I'm trying to also wrap my head around how/if I can do a fresh install 12.04 without losing my apps/files in my home folder.  

I'm assuming that I've correctly split my partitions (/, /home, linux-swap) to allow me to perform a fresh install while still maintaining my information.  Do I need to do anything special to be sure the install process does not overwrite my home contents?  Is there going to be enough of a change from 11.10 - 12.04 that would make it more wise to backup everything and do an install from scratch?

---

### Post by oldfred on 2012-03-01
All your configurations are in /home, but the apps themselves are not. You can export a list it doing a clean install. If upgrading then you do not have to do anything.

But good backups are always important, no matter how you upgrade. I prefer to have an extra 25GB / (root) partition and do a clean install to that just to test that my system works ok. My portable does not have much HD space, so I use a larger flash drive with a full install to test.

---

### Post by /bee/ on 2012-03-01
Will this work between 11.10 and 12.04?

```
dpkg --get-selections > installed-software
dpkg --set-selections < installed-software
dselect
```

Or might that break a few apps?

---

### Post by oldfred on 2012-03-01
I have not done it on 12.04 yet, but have on every install before. It just is that you may install some older apps that are not current anymore.

In one of my older installs I was still installing python2.5. Also when they changed from OpenOffice to Libre I had to edit list not to install OO.

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

