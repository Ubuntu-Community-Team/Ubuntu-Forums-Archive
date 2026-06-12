---
title: "Restore Root Partition"
date: 2010-08-31
forum: General Help
---

### Post by monkeysinacan on 2010-08-31
So I messed up some files in my root partition and now my ethernet wont work.
When I installed Ubuntu on my system I made my Root and Data two different partitions just in case something like this happened. I'm trying to find a guide for how to restore my entire root partition to its original setup but cant find one.
Can anyone point me in the right direction? Thanks!:)

---

### Post by andrewthomas on 2010-08-31
When you refer to a data partition, I take it that you mean your /home partition?

---

### Post by monkeysinacan on 2010-08-31
> **andrewthomas said:**
> When you refer to a data partition, I take it that you mean your /home partition?

Yes I do. I actually have it listed as home on my computer but I heard it called data before so I just said that because I thought it would be clearer.

---

### Post by Nytram on 2010-08-31
If you have all your data on a separate partition, couldn't you just reinstall Ubuntu? Just make sure not to format your home in the installer.

---

### Post by oldfred on 2010-08-31
Mnay times reinstall may be quicker if you have separate /home and good backups of all your data.

You can chroot into your install from a liveCD and then run commands to repair. Chroot should give you internet so you can update.

kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh? Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's - change sda5 to correct partition, copy as one line:
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

# new for lucid & karmic 
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

Then once chrooted into your system:
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

Plus any additional commands required to fix your specific issue.

---

### Post by monkeysinacan on 2010-09-01
> **Nytram said:**
> If you have all your data on a separate partition, couldn't you just reinstall Ubuntu? Just make sure not to format your home in the installer.

Thanks! That worked great! It was very easy. Just made sure to tell the installer to use the right partitions for the right things and to make sure not to check the "format partition" box for /home

---

