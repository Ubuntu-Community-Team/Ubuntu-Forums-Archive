---
title: "Dual Boot 2 HDs"
date: 2011-05-09
forum: General Help
---

### Post by blukid on 2011-05-09
Hi, i just received an old dell optiplex, which is better than my current desktop lol, and it has WinXP on the HD.  I would like to add my Ubuntu 10.10 HD to the system, and choose which OS/HD to use at boot time. Kind of a noob with linux still, so would GRUB be able to help me with this, and how would I set that up?

---

### Post by ajgreeny on 2011-05-09
It may require nothing more than attaching the hard drive, changing the boot priority to make that drive the first device, and booting the machine.  If you can get into ubuntu that way, and then run ```
sudo update-grub
``` the windows install ought to be added to the grub menu.

The problem may be simply knowing which disk is which in the BIOS, but if one does not work, choose the other.

---

### Post by blukid on 2011-05-09
Thanks for the reply.

I did what you said, and now when I boot up, I get the grub menu, and Ubuntu starts correctly, but when trying to get to Windows, it says:
```

error: no such device: d668a7b668a793b1.
error: hd1,msdos1 cannot get C/H/S values.

Press any key to continue...

```
any ideas?

Just a thought, I know linux auto-detects hardware when installing, do you think reinstalling Ubuntu might help? That's an option, but can't re-install XP.

---

### Post by blukid on 2011-05-09
Nevermind, got it.

In BIOS I had the WinXP HD off. So it works now. Thanks so much! This is awesome :D

---

