---
title: "? corrupted boot loader"
date: 2011-09-17
forum: General Help
---

### Post by DrBob89 on 2011-09-17
Dell Insprion desktop with dual boot Ubuntu 11.04 and Win7

Every few weeks I boot into Win7 to download some audiobooks that require DRM.  This time some Dell crapware called DataSafe decided it needed to update itself.  At the end of the installation, the computer re-booted (or attempted to re-boot) without warning.

I am now stuck with the Dell splash screen, stuck half-way through the boot process.  Hitting the shift key does not bring up grub.

I was only peripherally paying attention during this software update but it was doing something to the rescue partition.

My dx is that grub was corrupted and needs to be restored.

Any suggestions on how to start?

Buck

---

### Post by drs305 on 2011-09-17
Being able to identify the Dell apps as the problem helps.

Forum member Meierfra identified this issue early on in Grub 2 and came up with some solutions. See if they work for you.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR")

---

### Post by DrBob89 on 2011-09-19
Thanks for the reply.  It turns out that the culprit was the MP3 player that was plugged in.  I probably owe Dell an amend for all the bad thoughts I had about them.  It was their trouble shooting website that suggested the solution.

---

