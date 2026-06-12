---
title: "fsck trying to scan recently removed Hard disk on boot"
date: 2010-11-08
forum: General Help
---

### Post by moo9801 on 2010-11-08
Dear Ubuntu buddies,
I have ran into a bit of a problem.  my server(10.10) is hosting a website with no problems whatsoever.  I decided to install an extra hard drive, and format. i did both, and turned off my server after some more configuration.  After a while, I decided that the new hard drive was a little loud for my liking, so I removed it.  I had not put any files on it.  I rebooted and saw a message that said this:
> 
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 101202/2351104 files, 1516082/9393920 blocks

I think that when I turned it off, it was formatting.  How do I stop this from halting the boot?  I can get by it by pressing the b or a key.

thanks
SC

---

### Post by efflandt on 2010-11-08
Check /etc/fstab and comment out or remove any line(s) related to the non-existing drive.  Note that you need to precede your editor command with **sudo** to do it as root (or **gksu gedit**).

Note that your system will run fsck during boot after a partition has been mounted a certain number of times, and you should let it do that.

---

### Post by moo9801 on 2010-11-12
> **efflandt said:**
> Check /etc/fstab and comment out or remove any line(s) related to the non-existing drive.  Note that you need to precede your editor command with **sudo** to do it as root (or **gksu gedit**).

Note that your system will run fsck during boot after a partition has been mounted a certain number of times, and you should let it do that.

Ah, yes, now i feel completely incompetent. should have known that as i did write it :(

Marking as solved now.

---

