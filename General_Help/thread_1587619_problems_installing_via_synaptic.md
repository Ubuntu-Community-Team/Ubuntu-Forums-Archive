---
title: "problems installing via synaptic"
date: 2010-10-03
forum: General Help
---

### Post by jorik42 on 2010-10-03
Hey all;
So, i'm having a problem installing programs via synaptic.  supposing I issue the command:
     sudo apt-get install <program>
(and assuming the program is in the repositories), I get an error like follows:

update-initramfs: failed for /boot/initrd.img-2.6.32-24-generic

I have no idea what this means, and googling has not turned up anything appreciably helpful.  It does this for anything I try to install via synaptic, both the command line or gui versions.  Anyone have any suggestions?  The full error output is below:



jorik42@jorik42-laptop:~$ sudo apt-get install vim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vim is already the newest version.
The following packages were automatically installed and are no longer required:
  exim4-daemon-light linux-headers-2.6.32-21-generic klipper ksysguard libparted0 kwrite linux-headers-2.6.32-21 libkwineffects1 exim4-config kinfocenter
  bsd-mailx exim4 exim4-base kappfinder plasma-desktop systemsettings kdepasswd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 74 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up initramfs-tools (0.92bubuntu78) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.32-24-generic (2.6.32-24.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
cp: missing destination file operand after `/tmp/tmp.KHpgnSqIER/sbin/'
Try `cp --help' for more information.
------------------
Error has occured!
update-initramfs: failed for /boot/initrd.img-2.6.32-24-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.32-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
cp: missing destination file operand after `/tmp/tmp.Zplsm3B8Pm/sbin/'
Try `cp --help' for more information.
------------------
Error has occured!
update-initramfs: failed for /boot/initrd.img-2.6.32-24-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.32-24-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dcstar on 2010-10-04
> **jorik42 said:**
> Hey all;
So, i'm having a problem installing programs via synaptic.  supposing I issue the command:
     sudo apt-get install <program>
(and assuming the program is in the repositories), I get an error like follows:

update-initramfs: failed for /boot/initrd.img-2.6.32-24-generic
.........

[LIST=1]
[*]Do you have sufficient disk space?
[*]Use Synaptic to reinstall that linux-image package.
[/LIST]

---

