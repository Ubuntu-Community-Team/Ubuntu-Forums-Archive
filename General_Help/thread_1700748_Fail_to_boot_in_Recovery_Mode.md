---
title: "Fail to boot in Recovery Mode"
date: 2011-03-05
forum: General Help
---

### Post by kkrishnan on 2011-03-05
Hi folks

I am helping this guy whose laptop went on the fritz while he was trying to update it. Halfway through the update, his laptop rebooted (without the updates completing). Now, when I try logging into the ubuntu, the login splash screen comes up (without a background) but neither the trackpad nor keyboard respond. I tried using an external USB mouse, with the same effect.

I tried booting in recovery mode and the boot sequence halts abruptly midway. The last messages is:

[    5.135990] Adding 2121720k swap on /dev/sda5. Priority:-1 extents:1 across:2121720k

I have no idea what this means, and don't know what to do next.

Any ideas?

---

### Post by inkrypted on 2011-03-05
Try booting to a live CD and running fsck in a terminal to check the file system. Here is more info on fsck.  [http://linux.die.net/man/8/fsck](http://linux.die.net/man/8/fsck) . It kinda sounds like a bad drive or filesystem to me. Best of luck.

---

### Post by kkrishnan on 2011-03-05
Thanks inkrypted.

Running fsck gave me this:
$ sudo fsck /dev/sda2
fsck 1.41.12 (17-May-2010)
/dev/sda2: clean, 452668/4276224 files, 3376846/17089792 blocks (check in 3 mounts)

Any tips on how to proceed from here?

Also, I tried running:
$ sudo chroot /media/xxx [where `xxx' is the partition name]
chroot: failed to run command `/bin/bash': Exec format error

Does this shed any light on the problem?

---

### Post by inkrypted on 2011-03-06
Well that means your drive is good and the filesystem is clean. I would proceeed starting to recover from a failed upgrade. If you can get into recovery console try typing sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade

If that does not work you might try reinstalling off the live cd.

---

### Post by inkrypted on 2011-03-06
I got to thinking that you might need to purge the old debs so this might be helpful 
sudo apt-get clean
sudo apt-get update
sudo dpkg --configure -a

If you can make it to the recovery console.

---

