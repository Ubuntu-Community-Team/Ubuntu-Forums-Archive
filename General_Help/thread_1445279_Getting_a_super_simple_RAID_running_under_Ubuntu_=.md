---
title: "Getting a super simple RAID running under Ubuntu = impossible?"
date: 2010-04-02
forum: General Help
---

### Post by tackle on 2010-04-02
My computer is a small box running Ubuntu 9.10 with a Compact Flash card as main OS drive, and two identical 500GB drives that I want to setup as a mirrored drive for important backup files etc.

The two 500gb drives were installed after installing the OS. After that I've created a new partition table on both drives and formatted them as ext2.

I've used mdadm to create a new RAID1 array called /dev/md0
I've managed to format this "md0" using fdisk, and that is as far as I can get.

What more do you have to do to setup a RAID? Both the 500GB drives show up as individual drives viewing inside gparted; /dev/sdb1 and /dev/sdc1. When just browsing the file system they don't show up. Instead there's a "Mass storage drive" which gives an error dialog "Could not mount the file" when trying to enter.

I've tried typing "mount /dev/md0" in the terminal without success. Only get the error "mount: could not find /dev/md0 in /etc/fstab or /etc/mtab".
I've also tried using gparted to set the RAID drive flags without any difference at all.

I installed Ubuntu 9.04 first and upgraded to 9.10 (since you can't install 9.10 directly on a CF card), so I don't have the disk utility program to try and create a RAID with, should that somehow work.
What else can I do? Do I have to resort to buying a hardware RAID interface PCI card?

---

### Post by sigurnjak on 2010-04-02
You could try Palimpsest Disk Utility 2.28.0 ,(disk utility ) select drive and from file choose new and create raid array . I did not try it yet but it looks simple way of doing it .

---

### Post by tackle on 2010-04-02
Turns out my OS might be 9.04 after all.
I can't install Palimpsest either way it seems.

Have you seen any download site for it? I've tried dozens of apt-get package names without result

---

### Post by sigurnjak on 2010-04-02
Try this :
[http://www.webupd8.org/2009/08/how-to-install-palimpsest-disk-utility.html](http://www.webupd8.org/2009/08/how-to-install-palimpsest-disk-utility.html)

---

