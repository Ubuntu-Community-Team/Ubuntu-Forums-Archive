---
title: "Boot Up Failure"
date: 2010-08-17
forum: General Help
---

### Post by NDW57 on 2010-08-17
This seems to be a similar query to one posted by "Vadtec". A couple of times recently my PC has failed to boot up properly and has displayed a message:

Gave up waiting for root device common problems:
-Boot args (cat/proc/cmdline)
 - Check rootdelay = (did the system wait long enough?)
 - Check root = (did the system wait for the right device?)
-Missing modules (cat/proc/modules; ls/dev)

Alert! /dev/disk/by-uuid/a8c3852a-7741-4c01-8914-ef2e0d2da0f4 does not exist. Dropping to a shell!

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)

Enter "help" for a lisy of built in commands

(initramfs) (Flashing cursor)

In the recent past I pressed the reset button on the PC and the thing seemed to boot up normally. However today I tried resetting three times and got the same message. In desperation I switched off the mains supply for ten seconds and then rebooted - and it worked. I am though, concerned that this may well happen again - any ideas? (Incidentally the message I've written above is one I copied with pen and paper so it may have one or two errors in!)

I'm using Ubuntu 10.04 (Lucid), 1.2Ghz processor, 576mb RAM

---

### Post by mitsios on 2010-08-17
Try running grub-mkconfig.

---

### Post by NDW57 on 2010-08-18
Hi "Mitsios"
I tried your suggestion in "terminal" and I got a message along the lines of I needed to be in the "root account". So I tried prefixing your suggested command with "sudo" - hope that was OK ! Terminal appeared to run something and when it had finished I shut it down and, with fingers crossed, shut down the PC. When I switched back on it booted up again apparently without trouble. So, thanks so far. I'll leave this as unsolved for now as it was an intermittent fault and see how it gets on.

---

### Post by NDW57 on 2010-08-22
No more problems after a few days - problem solved. Many thanks.

---

### Post by ceejay724 on 2010-08-26
Hey
 
I am having the same problem and it was not solved by switching it off at the main switch. Also, I cannot get to the terminal interface to make the suggested changes. 
Some assistance please.
 
Thank you in advance

---

