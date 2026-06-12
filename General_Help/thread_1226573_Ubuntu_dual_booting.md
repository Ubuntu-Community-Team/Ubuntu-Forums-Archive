---
title: "Ubuntu dual booting"
date: 2009-07-29
forum: General Help
---

### Post by davewickett on 2009-07-29
I have Ubuntu  dual booting  with vista on my c drive with a grub loader. I have a d drive  which is my recovery drive for Vista. What i need help with is to format my d drive & put ubuntu on my hole c drive & Vista or Xp on my d drive with a boot loader for them so if there is any1 who could help me please thank you  
Dave:biggrin::biggrin::biggrin:

---

### Post by quixote on 2009-07-31
First, Windows OSes generally need to be installed first, Ubuntu second, so I'm not sure what you say is the way to do it. (The reason is that Windows isn't intended for a multi-OS environment, whereas Unix/Linux is.)  Why not leave Vista where it is, on C:, and install Ubuntu on D: ?

If you install Ubuntu on D:, I'm pretty sure grub will detect c: and the windows install, and will put it in the bootloader automatically. (If it doesn't, it's pretty easy to put an entry for Windows in by hand.)

The only tricky bit is that in this case you want grub *not* to mess up the Windows Master Boot Record (MBR) on C:, so I'm pretty sure you want to use the option to put it on the same partition as ubuntu.  You do that at the last step before hitting the "install" button.  You do a "manual partition", do NOT format c: (which will probably be called /dev/hda1, or the like).  Concentrate on d: (/dev/hdb1 or similar).  Put the / (root) mount point there.  Make a separate /home partition there if you want.  Make sure that whichever drive is c: is *not* going to be formatted.  And hit the button for "Advanced Options."  That takes you to an option to participate in package survey, and, finally!, to put grub on the same partition as ubuntu.

I'm not absolutely sure about this, so if someone who does know for sure can give a better answer ...?

---

### Post by davewickett on 2009-08-02
thanks mate im sorting something out with it now

---

