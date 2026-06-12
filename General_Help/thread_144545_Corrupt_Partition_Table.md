---
title: "Corrupt Partition Table?"
date: 2006-03-14
forum: General Help
---

### Post by thexaspect on 2006-03-14
HELP! My Kubuntu 5.10 desktop just crapped on itself! I noticed that my Samba share wasn't loading from my laptop, so i kvm'ed over to my desktop and attempted to restart samba, which failed. weird. so me being a more windows-centric user said, hey, maybe reboot? shrug. yeah, now nothing. it goes through grub, starts loading kubuntu, with the little blue and black screen, gets to init, and says /etc/init/ missing. so i try to boot from cd, reload the base system and get an uncorrupted version of init.d, but no go, because the partition table is jacked up. the partition table should read 
hda1 /
hda2 /swap
but instead reads 
sda1 /etc/media
sda2 /swap
wtf? I dont have scsi, it's all ide. I have approx 120 gigs worth of important files on there that I really need to get off. I tried to rename the partition back to /, which i had to do before about 2 weeks ago and it worked fine, but it wouldnt let me write the partition table. anyone?

---

### Post by jselfridge on 2006-03-14
this is your desktop computer? 
Insert your ubuntu cd, and type resque at the boot prompt.
rescue mode shoud find your system, the chroot to where ever your system was mounted, then goto your /boot/grub directory an vi grub.list.
Look at your kernel commands, and make sure that if there is a root statement in your kernel parameters that it points to the right place.
post your results, any information will help figure out what specific problem you have.

---

### Post by thexaspect on 2006-03-14
Ok, I assume you meant "rescue" at the prompt, which i did. and yes, my desktop, which also functions as my file server for my laptop. i have no idea how to do the chroot command, i'm a bit new at this, when i just type "chroot, it says: "Busybox v1.00-pre10 ...etcetc... multi call binary", and then:
"Usage: chroot NEWROOT [COMMAND...]
it wont let me just cd to /boot/grub, but when i typed "chroot /" it didnt give me any errors, just no visible output.

---

### Post by thexaspect on 2006-03-14
also after the "chroot /" i tried to cd into /boot/grub and it said:
"cd: 1: can't cd to /boot/grub

---

