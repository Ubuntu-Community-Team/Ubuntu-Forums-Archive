---
title: "parted shows &quot;custom logging function&quot;"
date: 2010-05-01
forum: General Help
---

### Post by skitching on 2010-05-01
I've been using parted regularly with lucid lynx betas without problems.

But just recently I have started seeing two problems:

(1) the "--script" option doesn't appear to work any more.

(2) When I run parted commands (other than "p") manually, I get this output:

custom logging function 0xb9237008 registered
selinux=0
calling: settle
custom logging function 0xb8d04008 registered
selinux=0
calling: settle


Can someone confirm this?

I am using parted because I am experimenting with testing grub2 under qemu. The commands I am running are:

 qemu-img create raw.img 4G
 sudo mknod disk b 7 200
 sudo chown $USER disk
 sudo losetup disk raw.img
 cat partcmds.txt | parted --script disk

File partcmds.txt contains:
  mklabel msdos
  mkpart primary ext2 65536s 100%

A variant of this was working a while ago, but no longer works; the parted script now just appears to be ignored. And as mentioned above, when I test things interactively (ie I run "parted disk" and enter the commands in partcmds.txt manually) they *work*, but the odd output appears.

If someone can confirm this happens for them too, then I'll raise a bugreport.

Thanks, Simon

---

