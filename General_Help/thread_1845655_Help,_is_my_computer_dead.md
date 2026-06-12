---
title: "Help, is my computer dead?"
date: 2011-09-17
forum: General Help
---

### Post by guine on 2011-09-17
So I was just using my computer and all of the sudden it wouldn't let me launch any programs, the closest I could get was something saying my system monitor was starting up but that would just go away after a couple of seconds.  So I decided to reboot my computer and when I clicked on restart an empty window with restart on the top would pop up for a couple of seconds and then disappear.  I decided to just do a hard shutdown and when I start it back up I get:

```
mount: mounting /dev/disk/by-uuid/2cd/by-uuid/2cd71898-bb09-404d-b0be-67171081ea40 on /root failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init= bootarg.


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help for a list of built-in commands.

(initramfs)
```

When I enter 'help' I get

```
Built-in commands:
_ _ _ _ _ _ _ _ _ _
. : [ alias break cd chdir command continue echo eval exec exit export false getopts hash help let local printf pwd read readonly return set shift source test times trap true type ulimit umask unalias unset wait [ [[ ash awk basename cat chmod chroot chvt clear cmp cp cut deallocvt df du dumpkmap echo egrep env expr false fbset fdfluch fgrep find grep gunzip gzip hostname ifconfig ip kill ln loadfont loadkmap ls mkdir mkfifo mknod mkswap mktemp more mount mv openvt pidof printf ps pwd readlink reset rm rmdir sed setkeycodes sh sleep sort stat static-sh stty sync tail tee test touch tr true tty umount uname uniq wc wget yes zcat
```

And if I try to boot up with an ubuntu cd it just goes to the dell boot screen at the very beginning and then stops there and doesn't even give me the chance to boot from a live cd.  Any idea what is going on?  Thanks

---

### Post by TeoBigusGeekus on 2011-09-17
Can't you get into the bios (or boot options) to tell it to boot from the cd?

---

### Post by guine on 2011-09-17
I can get into bios when I don't have a cd in and it shows my cdrom as my second boot option.  But once I put the boot cd in it just stops at the dell screen that comes up at the beginning and won't let me into bios.

---

### Post by no2498 on 2011-09-18
on my dell i had to turn off everything but the cd player 
hard drive and all but the cd player in the bios

---

### Post by guine on 2011-09-18
> **no2498 said:**
> on my dell i had to turn off everything but the cd player 
hard drive and all but the cd player in the bios

I gave that a try and it didn't have any effect although I've been able to boot off a cd without changing the bios in the past.

---

### Post by WorMzy on 2011-09-18
It's possible (however likely) that the motherboard is borked. There's only so much advice we can offer, and 99% of it depends on you being able to access a working Linux environment (e.g. LiveCD/USB). If you can't even manage to boot into a live environment, then all I can think to suggest is contacting your PC's manufacturer and asking them for help.

Could be that your bios has a problem which can be fixed by updating it (a risky process which could leave your motherboard absolutely useless).

If you have the spare parts available to you, or aren't opposed to splashing some cash, then try swapping out the motherboard and see if that fixes things.

---

### Post by guine on 2011-09-18
Guess I'll have to see if dell tech support can help(shudders), its an old computer so I was kinda guessing its probably hardware dying.

---

