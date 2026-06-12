---
title: "Xubuntu / Grub boot problems"
date: 2010-06-16
forum: General Help
---

### Post by gabble on 2010-06-16
Hi,

I've just tried a fresh install of xubuntu on an old machine, using the alternate installation CD.

Now it won't boot - just gets to a 'grub rescue' command prompt:

> error : unknown file system
grub rescue>

I've tried reinstalling GRUB from the alternate installation CD rescue mode, which hasn't helped, so I'm at a dead end now - GRUB reinstalls, but then I just get the same problem.

I've seen similar problems online, which people have solved by resintalling GRUB from a liveCD. unfortunately, my computer does not have enough RAM for the liveCD (I'm using the alternate install CD).

Any help would be greatly appreciated! I'm really keen to switch to ubuntu.

---

### Post by arrange on 2010-06-16
First check if the filesystem is OK (it should be possible to open a console from the Alternate): ```
fsck -f /dev/sda1
```(change *sda1* appropriately)

---

### Post by gabble on 2010-06-16
Thanks for taking the time to help!

> it should be possible to open a console from the Alternate


I don't know how to do that (you're dealing with a bit of a noob here).

From the alterate install CD, there is a 'rescue mode' which gives me the option first to choose 'a device you wish to use as a root file system'. If I select /dev/sda1, I have the options to either 'execute a shell in /dev/sda1' or 'execute a shell in the installer environment. With the former If I type 

```
fsck -f /dev/sda1
```

on that, I get a warning that 'the filesystem is mounted If you continue you will cause severe filesystem damage'

If I select any of the other options, or try executing a shell with no root file system, the command is not recognised.

Background - computer has two hard disks in it. It was a dual boot XP/xubuntu (I think). As I got fed up of windows, my plan was to install xubuntu only, using the second hard disk as for /home.

That gave me the above problem, so I've reinstalled just using the primary hard drive, (with root and swap partitions). no partitions on the secondary atm. But the same problem is there.

---

### Post by arrange on 2010-06-16
Pretend you're trying to install, but once the installer starts asking you questions (not when the installation actually starts later), press Ctrl+Alt+F2. You should see a black screen with something like *Press Enter to activate this console*. Then run ```
e2fsck -f /dev/sda1
```You get back to the first console by pressing Ctrl+Alt+F1 and then choose *Abort* or *Cancel the installation*.

---

### Post by gabble on 2010-06-16
Thanks - got to the console. On typing that command now getting

```
-/bin/sh: e2fsck: not found
```

likewise for fsck.

I've looked in /bin, /sbin, /usr/bin, /usr/sbin, and can't see it. :/

---

### Post by arrange on 2010-06-16
Hmm, then I don't know. I've just checked with my Ubuntu Alternate 10.04 CD, and the *busybox* shell has *e2fsck* command available, but I don't know how the *xubuntu* variant is different...

---

### Post by gabble on 2010-06-16
Hmmm. On the verge of giving up. thanks for trying to help though!

---

