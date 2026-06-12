---
title: "Won't Mount After Kernel Upgrade"
date: 2011-06-27
forum: General Help
---

### Post by cg2916 on 2011-06-27
I upgraded from 2.6.38 to 2.6.39. I booted up my laptop and it gave me this:

```

Cannot change data mode on remount
mount: / not mounted already or bad option
mountall: mount / [301] terminated with status 32
mountall: filesystem could not be mounted: /
An error occurred while mounting /
```

Please help! Thanks!

---

### Post by garvinrick4 on 2011-06-27
Does it boot with the 2.6.38 kernel

---

### Post by cg2916 on 2011-06-27
> **garvinrick4 said:**
> Does it boot with the 2.6.38 kernel

Nope.

---

### Post by garvinrick4 on 2011-06-27
Put in a Ubuntu install Cd and choose try Ubuntu:
Open a terminal (ctrl/alt/t) and run this below:
Find your install sda #
```
sudo fdisk -l 
```(lower case L)
Pick out the linux install such as sda1 or sda5 whatever it is:
I will use sda5 for this code you change to whatever yours is.
```
sudo e2fsck /dev/sda5
```Now reboot and see if that fixes your system:
If your previous kernel did not boot then it is more than kernel problem so we
are running "fsck" to see if will repair your install:
## Can only run fsck on a file system that is not mounted.

---

### Post by cg2916 on 2011-06-27
> **garvinrick4 said:**
> Put in a Ubuntu install Cd and choose try Ubuntu:
Open a terminal (ctrl/alt/t) and run this below:
Find your install sda #
```
sudo fdisk -l 
```(lower case L)
Pick out the linux install such as sda1 or sda5 whatever it is:
I will use sda5 for this code you change to whatever yours is.
```
sudo e2fsck /dev/sda5
```Now reboot and see if that fixes your system:
If your previous kernel did not boot then it is more than kernel problem so we
are running "fsck" to see if will repair your install:
## Can only run fsck on a file system that is not mounted.

It didn't work. I ran it in recovery mode and it said "Root filesystem check failed". I ran it and it just said that it's clean. I rebooted and it's still messed up.

---

### Post by garvinrick4 on 2011-06-27
In your live cd run these in a terminal copy and paste one at a time:
Change sda# to your own I am using sda5 for this: Get internet working in live CD.
If apt-get update gives errors internet not working.

sudo mount /dev/sda5 /mnt
 for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done  
 sudo cp /etc/resolv.conf  /mnt/etc/resolv.conf
 sudo chroot /mnt
 dpkg --configure -a
apt-get update
 apt-get upgrade
dpkg --configure -a
apt-get -f install
exit
 for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
 sudo umount /mnt
 sudo reboot

---

### Post by cg2916 on 2011-07-04
> **garvinrick4 said:**
> In your live cd run these in a terminal copy and paste one at a time:
Change sda# to your own I am using sda5 for this: Get internet working in live CD.
If apt-get update gives errors internet not working.

sudo mount /dev/sda5 /mnt
 for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done  
 sudo cp /etc/resolv.conf  /mnt/etc/resolv.conf
 sudo chroot /mnt
 dpkg --configure -a
apt-get update
 apt-get upgrade
dpkg --configure -a
apt-get -f install
exit
 for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
 sudo umount /mnt
 sudo reboot

When I do the first script, it gives me:

> mount: /dev/sda2 already mounted or busy
mount: according to mtab, /dev/sda2 is mounted on /

---

### Post by garvinrick4 on 2011-07-04
> mount: /dev/sda2 already mounted or busy
mount: according to mtab, /dev/sda2 is mounted on / 			 		

Nothing should be mounted in Live CD unless you tell it to or are you trying this from recovery mode? Use a Live CD or another install of same architecture. 32 or 64 bit

> It didn't work. I ran it in recovery mode and it said "Root filesystem check failed"
Should only run when not mounted, just from Live CD or another install of same architecture 32 or 64 bit.

---

### Post by cg2916 on 2011-07-04
> **garvinrick4 said:**
> Nothing should be mounted in Live CD unless you tell it to or are you trying this from recovery mode? Use a Live CD or another install of same architecture. 32 or 64 bit


Should only run when not mounted, just from Live CD or another install of same architecture 32 or 64 bit.

Sda2 is my Linux partition, not my Live CD/

---

### Post by cg2916 on 2011-07-05
I still don't have an answer that works.

---

