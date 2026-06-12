---
title: "Grub Rescue, only detects HD0 (fsck, e2fsck, TestDisk)"
date: 2010-10-15
forum: General Help
---

### Post by primaxx on 2010-10-15
Oh man, I'm in trouble! 

Sitting here in Norway, I (through TeamViewer) helped my mother (who is in Spain) updating her laptop to 10.10. I was of course doing this while doing other things at work, and managed to replace the Grub installation. Now the machine won't boot. :oops:
It stops in Grub Rescue.
After having a look at the [Grub Rescue Mode Megathread]("http://ubuntuforums.org/showthread.php?t=1594052") I made her type the command
```
ls
```
with the result that it only detects HD0

The previously mentioned thread then says: > 
If all you get is (hd0) you most likely have a partition table or disk error. Seek assistance elsewhere! (fsck, e2fsck, TestDisk, etc.)

It used to be (at least) two partitions on the disk, one with Win 7 and one with Ubuntu 10.04.

Can anyone *please* help me with the arguments I need to tell her (over the phone) to type in order to make the computer boot again?

The laptop is, by the way connected to the Internet.

Normally I am so careful when doing stuff like this, but today, I messed it up. And of course it had to be my 2500km's away mothers machine... :redface:

---

### Post by dino99 on 2010-10-15
- take control of your mother machine, chroot it if necessary, 
- make some control: update, install -f, dpkg --configure -a
- then into synaptic: remove/purge grub-pc then reinstall it, it might boot

---

### Post by primaxx on 2010-10-15
> **dino99 said:**
> - take control of your mother machine, chroot it if necessary, 
- make some control: update, install -f, dpkg --configure -a
- then into synaptic: remove/purge grub-pc then reinstall it, it might boot

Thank you so much for the response!

I can manage step two and three of your suggestions if I only knew how to manage step one...

Is it possible to get for instance ssh-access in Grub rescue?

---

### Post by primaxx on 2010-12-10
It turned out that my problem was generated because I upgraded a version of Ubuntu that was installed using Wubi.
The only solution I found was to reinstall Ubuntu.

---

