---
title: "changing boot partition"
date: 2011-06-18
forum: General Help
---

### Post by jal on 2011-06-18
Many moon ago I installed maverick. I did this by creating a new partition, and installing the root on that, and then pointed /home to the previous home partition. This worked very well (except for having to re-install lots of apps).

Now I wish to re-claim the space used by the partition which contained the 'old' os. However this partition was the original natty install, and it is still marked as the 'boot' partition.

I suspect that if I remove the old partition then the system will not boot up.

My questions are these: can I simply use gpart to flip the boot flags for the partition? Do I need to re-configure grub2 if I do this? Is there a MBR which needs to be moved?

Any advice appreciated.

---

### Post by mikewhatever on 2011-06-18
In what way is the partition marked as a boot partition? Is it just the boot flag, or is it shown as /boot?

---

### Post by oldfred on 2011-06-18
If it is just the boot flag, grub or grub2 does not use it. Windows has to have a boot flag on a primary partition and Lilo uses a boot flag on any partition. But a few BIOS require a boot flag on a primary partition (must assume Windows) and give a boot error before loading any boot code. So I always recommend a boot flag on a primary partition even with grub.

You can use gparted, Disk Utility or command line. You should only have one boot flag per drive.

set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda

You can easily reinstall new versions of all installed apps.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

But you should houseclean before and even edit list to remove obsolete apps. I found I was still installing python2.5. Natty changes from OpenOffice to LibreOffice, so you proably would not want to reinstall OO.

---

### Post by jal on 2011-06-19
> **mikewhatever said:**
> In what way is the partition marked as a boot partition? Is it just the boot flag, or is it shown as /boot?

just the boot flag, partition is not mounted

 ```
 
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7649    61438976   83  Linux
/dev/sda2           29646       30402     6073344   82  Linux swap / Solaris
/dev/sda3           15299       29645   115242277+  83  Linux
/dev/sda4   *        7650       15298    61440592+  83  Linux

```

I see oldfred saying that grub doesn't need this.

thanks.

---

### Post by jal on 2011-06-19
Thank you oldfred. Just what I needed to know.

and the tip on using dpkg was a real bonus, that will save hours of work next time.

---

