---
title: "Questions about (K)Ubuntu and Lilo"
date: 2010-01-24
forum: General Help
---

### Post by cage47 on 2010-01-24
New to (K)Ubuntu. But not linux. Cut my teeth on a floppy install of Debian Potato. Been running debian steady since Woody. I'm very old-school. I have used Lilo all along. But have grub now because there was no choice in the 9.10 install (don't like that). Couple questions.

1. Is there a way to force lilo to install during system install? And not by using the alternate cd. I know about that but don't want to use that cd for reasons.

2. Has anyone installed Lilo after install by apt-get install-ing? Any issues to deal with?

And before giving me the schpele of how grub is more robust and all that. I have no need for robust. I have my reasons for wanting lilo. I just want to know if there are any issues with loading it AFTER install. Let's just say I Don't Like Grub and leave it at that.

---

### Post by Leppie on 2010-01-24
i don't see why lilo would not work, unless you're booting off an ext4 partition. at the moment i cannot verify this, my system doesn't use any extX fs.
installing shouldn't be a problem.

---

### Post by Mazin on 2010-01-24
I believe lilo has been deprecated as (or may never have been) an option during install.

You should be able to switch to lilo by first apt-getting lilo and then running (as root, obviously) liloconfig. 

Googling dug up this guide ([http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html](http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html)), but it's slightly outdated so I wouldn't follow its directions to the letter, but please do it from a live CD (i.e., not while you're running off the drive) and have a backup lilo or grub boot disc handy while you do this.

---

