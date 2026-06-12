---
title: "boot help"
date: 2011-09-28
forum: General Help
---

### Post by tgarbez on 2011-09-28
i just wiped windows 7 and installed ubuntu 11.04. it was working great but it froze so i did a battery pull and rest the comput now when it boots it starts grub when i select to load ubuntu it goes to a black screen with a white cuser then sometimes it will load the purple boot screen that says ubuntu but freezes and wont do anything. what do i do to fix

---

### Post by heyandy889 on 2011-09-28
Hey, dude. Did you install from a CD or live USB drive? I would try booting into the "Try Ubuntu" mode, opening a terminal with Ctrl-Alt-T, and running
```
sudo update-grub2
```
That will help in case something with grub was corrupted.
Otherwise, reinstalling would definitely do the trick. Unfortunately, I don't have a less-drastic fix at my fingertips.
Rock on!

---

### Post by oldfred on 2011-09-28
Welcome to the forums.

Any sort of abnormal shutdown may damage file system, whether Linux or Windows. Then you have to run file checks.

#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

To shutdown safely:
Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
Another
sudo init 0

Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term singal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system

---

