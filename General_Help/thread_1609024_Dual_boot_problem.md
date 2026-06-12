---
title: "Dual boot problem"
date: 2010-10-29
forum: General Help
---

### Post by bchecca1 on 2010-10-29
I'm using 9.10, duel booting with Windows XP.  The XP side has gone bad, and won't even start up. Can I re-install windows on the drive the duel boot created for it without affecting the ubuntu side? Any suggestions on how to do that would be appreciated...

Bruce
[email]bchecca1@nycap.rr.com[/email]

---

### Post by gufide on 2010-10-29
yes you can using the xp partitionning tool, but I'm not sure that you will can access ubuntu again. I suggest that you reinstall xp in a partition and reinstall ubuntu 10.10 in another one.

I'm not an expert in this situation, but you should first check your xp partition if xp is not broken. If it is not, Open a terminal window and type: sudo update-grub
this will refresh you os chooser

---

### Post by Omnomnom on 2010-10-29
If you reinstall windows, it will overwrite GRUB with it's own boot menu. That means if you wanted to use Ubuntu again you'd have to reinstall GRUB.

---

