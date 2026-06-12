---
title: "Help with 9.1 fsck exit status 8"
date: 2010-06-23
forum: General Help
---

### Post by paolol61 on 2010-06-23
Hi, i got this error today, at boot and was not able to fix it .
i try the
fsck /dev/sda2
no fix
-------------------------
*Checking file systems...
145
fsck 1.41.4 (27-Jan-2009)
fsck.ext3: Unable to resolve 'UUID=2c482e50-8c52-48d4-a314-a23c234bd4d6'
fsck died with exit status 8

----------------------
thx for any help

---

### Post by dino99 on 2010-06-23
you have a huge error: unable to resolve uuid= ....

so you need to know about the real uuids: sudo blkid

now compare with the ones into fstab: sudo gedit /etc/fstab
(copy/paste the good uuid given by blkid to change the wrong, if any)

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo grub-mkconfig
sudo update-grub

reboot: sudo shutdown -r now  (will force a fsck on next boot)

---

### Post by paolol61 on 2010-06-23
Did I need to start from a cd ?
thx

---

### Post by CharlesA on 2010-06-23
Is sda2 your OS partition? If it's not and you are able to boot the machine, you shouldn't need to boot off a liveCD.

Just compare the UUID for /dev/sda2 in fstab and by using blkid.

---

### Post by paolol61 on 2010-06-27
ok today I had some time to try the repair.
Blkid 
is not showing the sda5 mentioned on /etc/fstab as the missing location
sda2 is the '/' install path and sda5 is the '/home' path

I will try now to boot from a get more info.
thx for the help.

From the CD i see the partition but is named as sda4 and is flagged as unknow

---

