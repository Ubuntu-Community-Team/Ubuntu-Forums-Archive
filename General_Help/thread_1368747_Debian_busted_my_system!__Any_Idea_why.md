---
title: "Debian busted my system!  Any Idea why?"
date: 2009-12-31
forum: General Help
---

### Post by TheForkOfJustice on 2009-12-31
I installed Debian 5.0.3 via a netinst CDROM onto a ReiserFS partition (changed from an ext4 partition) but I did **not** install Grub.  GRUB2 was already installed by my Ubuntu Karmic install and I didn't want to replace it.

After I was finished, even though Ubuntu and Vista were listed in Grub, they wouldn't boot to desktop.  The farthest I got was Ubuntu's bootsplash.  I could CTRL+ALT+DEL out of Ubuntu but had to hold down the reset button for Vista.  Debian wasn't listed in Grub since I was not able to enter Ubuntu to do a needed 'sudo update-grub'

I replaced Debian with Ubuntu on a reformatted ext4 partition and that fixed everything.

Question: Any ideas on what happened so I can install Debian properly this time? 

Was it:
- using ReiserFS as the partition's format instead of ext3?
- not installing Grub
- something else?

I can try another install later on but I want to know how Debian could break my other OS's as well.  I don't want to lose everything the next time I try this.

---

