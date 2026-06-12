---
title: "Unrepairable Grub error 15?"
date: 2010-03-17
forum: General Help
---

### Post by Lockheed on 2010-03-17
Once clonezilla finished restoring my linux partition, it displayed a message there was an error while restoring grub (which it should not touch in the first place). 
After reboot, Error 15 welcomed me, so I booted livecd and tried repairing groub with the usual
```
sudo grub
root (hd0.5)
setup (hd0)
quit
```
only after reboot exactly the same problem occurred. I tried 2 difference ubuntu live cds (9.04 and 9.10) to no avail.

The only way I can get into my system is by using Suepergrub CD.

---

### Post by Lockheed on 2010-03-18
I'd really like some help with that since google and forum search are of no use in this case.

---

### Post by lordskid on 2010-03-18
use your 9.10 it uses grub2 so the commands to use would be different.

---

### Post by Lockheed on 2010-03-18
Well, I have since returned to 9.04 using clonezilla and my boot partition is ok / but the problem persists.

---

### Post by lordskid on 2010-03-18
did you try reinstalling grub? or removing it then installing a different bootloader?

---

### Post by Lockheed on 2010-03-18
I did reinstall grub in synaptic, if that's what you are asking. I did not try other boot loaders as I am only comfortable with Grub.

---

### Post by lordskid on 2010-03-18
try to mount your ubuntu partion
then bind /dev to your mounted partition.

then chroot to that partition
and do the reinstall
do an update grub

see if that works. It always works for me in grub2. I don't have much experience with grub legacy

---

### Post by Lockheed on 2010-03-18
Well, I am writing this post from my ubuntu, except it is booted using Supergrub disk.
Do you think it is a solution to upgrade to grub2? If so, should I use
```
sudo aptitude install grub-pc
```which seems to be very complicated (manually typing in UUID)
or```
sudo aptitude install grub2
```where I read I have to type/edit nothing.

---

### Post by lordskid on 2010-03-18
just install grub-pc and grub-common

edit: do remove grub first.

---

### Post by Lockheed on 2010-03-18
What is the difference between regular and "single-user" option in grub2 boot menu?

---

