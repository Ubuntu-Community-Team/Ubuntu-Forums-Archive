---
title: "Need help getting to single user mode 10.04 LTS"
date: 2010-07-16
forum: General Help
---

### Post by lumix on 2010-07-16
There is a recovery mode available on the 10.04 LTS grub menu, but it still asks for a password.

I don't have this any more (long story, and besides, it makes me mad to think about it), so what to do now?

Already tried many howto's on editing the grub commands, but they always refer to a "boot" grub command that doesn't exist in any of my grub configs.

I should add that this boots on an LVM setup.

I could really use some help.

---

### Post by gdonwallace on 2010-07-16
First thing first.  What it is that you are trying to do?

Provide us with some more detail on what you are trying to accomplish, and we will be more than happy to provide answers for you.

---

### Post by lumix on 2010-07-16
Again, I'm trying to get to single user mode.  At present, I happen to be in need of a root password reset, but in general I'd like to know how to get into single user mode.

---

### Post by kornfan71 on 2010-07-16
Resetting the root password isn't too hard.
Grab a LiveCD (any distro works), go to a terminal.
Determine which partition your Ubuntu installation is on (for example /dev/sda1...use the command "fdisk -l" for a list of partitions).
After locating your partition, do this: (Use your partition here)
```
mount /dev/sda1 /mnt
```
Then, do this:
```
chroot /mnt
passwd root
```Then type in your desired password for the root account.

---

### Post by ajgreeny on 2010-07-16
You should also be able to get into recovery mode by hitting "E" when you get the grub menu, navigating to the kernel line and deleting the words "quiet splash" and replacing them with "single", then Ctrl+X to boot.

If you have already tried this, my apologies.  However, there should be no password request when you run recovery mode normally, so maybe setting a root password, which you appear to have done, has changed all that.

---

### Post by lumix on 2010-07-19
Greeny: what a jerk I am: apparently didn't get around to mentioning that this is a server installation.  So, no "splash" entry in Grub.  But will "single" still work?  Must it precede or follow any other commands in particular? 

Korn, that's a great tip...got to try that tonight.

---

