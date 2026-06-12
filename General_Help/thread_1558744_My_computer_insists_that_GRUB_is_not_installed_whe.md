---
title: "My computer insists that GRUB is not installed when it is."
date: 2010-08-22
forum: General Help
---

### Post by MikeHaggarKJ on 2010-08-22
basically, I had Ubuntu installed and decided to reinstall windows on the same pc on a partition on the same hdd. Now i need to restore grub to be able to boot Ubuntu.
I've done this a million times, what ive done is that ive inserted my old ubuntu 8.10 disc and followed this guide: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) but now that wont work since 8.10 doesnt read ext4 which I upgraded to a while ago. (at least I think thats why it wont work in 8.10)
I downloaded the newest ubuntu to the same thing from that disc but when I type "sudo grub" it simply tells me that grub is not installed despite the fact that it is (and ubuntu 8.10 seemed to recognize that it was, it would just stop when i typed "find /boot/grub/stage1".

Any suggestions?

---

### Post by utnubuuser on 2010-08-22
I think 9.04 has support for ext4 and still uses legacy grub.

---

### Post by uRock on 2010-08-22
> **utnubuuser said:**
> I think 9.04 has support for ext4 and still uses legacy grub.
This is correct. Ubuntu 9.10 and 10.04 have grub2 unlike previous versions. You will need the Jaunty(9.04) Image in order to install and repair the legacy grub, which your system needs.

Are you still using 8.10?

---

### Post by -kg- on 2010-08-22
> **uRock said:**
> Are you still using 8.10?

Good question, since support for Intrepid ended a while back.  Support for Jaunty (9.04) ends the end of next month.  If it were me, I would upgrade to at least Karmic (support expires April of next year), and really, Lucid is working great for me.  Being the next LTS version, that would be the thing.

If you wouldn't be losing too much or causing yourself all kinds of re-installation work, I would back up critical data, delete the old Ubuntu partitions, and do a fresh installation.  That would automatically put the GRUB boot loader back in the MBR where it belongs and you would have access to both your OSes.

---

