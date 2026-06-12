---
title: "Recovering &quot;locked&quot; Ubuntu files using a Live CD?"
date: 2009-12-08
forum: General Help
---

### Post by CBR1100XX on 2009-12-08
Ok, here's the deal.

Since I installed Windows 7, my Ubuntu installation won't start.  I've already looked at all the "how to dual boot Ubuntu and Win7" guides, but think I'll just stick with Windows 7.

But I'd like to get my Firefox bookmarks, but they're "locked", I don't have permission to move them over to my USB drive.  How do I unlock these while I'm in Live CD?

I'm running 9.10.

Thanks a bunch, I've searched Google but I find so much information it's hard to tell what I need to pick out.

---

### Post by CBR1100XX on 2009-12-09
Bump?

I just need to know how I log in "elevated" so I can transfer files which are "locked" from my old Ubuntu installation.

---

### Post by joes7 on 2009-12-09
Yes, simply use the "Repair" function after booting the CD. It should work fine.

---

### Post by snowpine on 2009-12-09
The simplest solution I would recommend is this: 

From the Ubuntu Live CD, press Alt+F2 and type 'gksu nautilus' (without the quotes). This will open a file browser with "root" privileges so you can copy/edit/delete any locked files. You can also right click on a file or folder and choose Properties->Permissions if it's set to the wrong owner.

---

### Post by plucky on 2009-12-09
> **CBR1100XX said:**
> Bump?

I just need to know how I log in "elevated" so I can transfer files which are "locked" from my old Ubuntu installation.

Open a terminal window on the Live CD and ```
gksudo nautilus
``` should give you the right to mount the disk and access the bookmarks.

Be careful as you are in super user mode.

Good Luck

---

### Post by CBR1100XX on 2009-12-09
Thanks a million guys! :popcorn:

---

