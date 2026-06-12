---
title: "dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct..."
date: 2010-05-28
forum: General Help
---

### Post by connellc on 2010-05-28
re: "dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

I have already tried to run sudo apt-get update and sudo apt-get upgrade, to no avail.

I have already tried to run aptitude to install dpkg again. I still get "dpkg was interrupted, you must manually run 'sudo dpkg --configure -a'  to correct the problem."

I am running Ubuntu 9.10 - the Karmic Koala 

Via Synaptic, I was trying to install  lmms (the Linux Multimedia Studio) and a few other miscellaneous files. 

I  have an AMD 64-bit processor, and I am running the 64-bit version of Karmic.

Have run the 'sudo dpkg --configure..." command in a terminal.

The results of that command are as follows (in quotes):

"sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-306-ec2
ERROR lilo fails for new /boot/initrd.img-2.6.31-306-ec2:

Warning: LBA32 addressing assumed
Fatal: open /vmlinuz: No such file or directory
dpkg: subprocess installed post-installation script returned error exit status 1"

---------------------------------
I cannot remember what else I was installing via Synaptic.

---

### Post by connellc on 2010-05-29
I tried to downgrade to the previous initrd.img file and downgrade intramfs-tools using aptitude but I am still getting unresolved issues:

connellc@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for connellc: 
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-305-ec2
ERROR lilo fails for new /boot/initrd.img-2.6.31-305-ec2:

Warning: LBA32 addressing assumed
Fatal: open /vmlinuz: No such file or directory
dpkg: subprocess installed post-installation script returned error exit status 1
connellc@ubuntu:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-305-ec2
ERROR lilo fails for new /boot/initrd.img-2.6.31-305-ec2:

Warning: LBA32 addressing assumed
Fatal: open /vmlinuz: No such file or directory
dpkg: subprocess installed post-installation script returned error exit status 1

Any other suggestions?

(I am running a 64-bit AMD version of Karmic and, because of the architecture, I had found that there should be no size limitations on the size of these *.img files.)

---

### Post by connellc on 2010-05-29
Compiled linux-image-2.6.31.21 just now. LILO didn't fail this time. It looks like I was able to get into Synaptic. Will restart computer as suggested.

---

### Post by dino99 on 2010-05-29
i never compile anything, to much work for nothing IMO

grub is the default loader not lilo

---

### Post by sarahsoriao on 2010-10-03
> **connellc said:**
> re: "dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

I have already tried to run sudo apt-get update and sudo apt-get upgrade, to no avail.

I have already tried to run aptitude to install dpkg again. I still get "dpkg was interrupted, you must manually run 'sudo dpkg --configure -a'  to correct the problem."

I am running Ubuntu 9.10 - the Karmic Koala 

Via Synaptic, I was trying to install  lmms (the Linux Multimedia Studio) and a few other miscellaneous files. 

I  have an AMD 64-bit processor, and I am running the 64-bit version of Karmic.

Have run the 'sudo dpkg --configure..." command in a terminal.

The results of that command are as follows (in quotes):

"sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-306-ec2
ERROR lilo fails for new /boot/initrd.img-2.6.31-306-ec2:

Warning: LBA32 addressing assumed
Fatal: open /vmlinuz: No such file or directory
dpkg: subprocess installed post-installation script returned error exit status 1"

---------------------------------
I cannot remember what else I was installing via Synaptic.


i have the same problem..

---

