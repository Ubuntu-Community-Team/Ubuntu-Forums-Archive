---
title: "Boot directory got deleted some how?"
date: 2010-02-10
forum: General Help
---

### Post by demonic_crow on 2010-02-10
Some how I manage to remove the boot directory and not sure how I manage to do it.  I was going through alot of trouble with this anyway.  Is it possible to get it back to running again without reinstalling everything?

---

### Post by n0dix on 2010-02-10
A big problem, here. :(

---

### Post by demonic_crow on 2010-02-10
kinda afraid of that, at least I can use a liveCD to get what stuff I do have on it but will take awhile to copy it all.  Thats why I wanted to see if I was screwed.

---

### Post by falconindy on 2010-02-10
Sure can. Your /boot consists of installed kernel images and bootloader related nonsense. Kernels can be re-installed, bootloader nonsense can be regenerated.

Step 1: boot off a liveCD and open a command prompt. We're going to create a chroot from a terminal.

Step 2: Assuming that you don't have /boot on a separate partition and / is /dev/sda1...
```
mkdir /host
mount /dev/sda1 /host
for fs in dev proc sys; do mount --bind /$fs /host/$fs; done
chroot /host /bin/bash
```
Step 3: You're now in an environment that should behave an awful lot like your normal setup. This means we can use the package manager and other utilties...
```
mkdir -p /boot/grub
apt-get install linux-image
update-grub
```
Step 4: Get out of the chroot and reboot! Ctrl-D will log out of the chroot and return you to the liveCD environment. To be safe, you'll want to manually unmount the structure we created:
```
umount /host/{dev,proc,sys,}
```

Reboot!

Note: This is untested and may kick your dog. If this seems to be over your head, you should just reinstall.

---

### Post by demonic_crow on 2010-02-10
When I run this command:
for fs in dev proc sys; do mount --bind /$fs /host/$fs; done

I get this
bash: syntax error near unexpected token `do'

---

### Post by falconindy on 2010-02-10
Double check your typing. What I provided works (copy/paste) in ZSH, Bash, and Dash.

---

