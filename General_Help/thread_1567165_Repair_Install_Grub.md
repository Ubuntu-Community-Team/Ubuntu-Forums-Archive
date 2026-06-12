---
title: "Repair Install? Grub?"
date: 2010-09-03
forum: General Help
---

### Post by spdtrip on 2010-09-03
Hi, 
I have Dell Precision M3400 laptop with Ubuntu 10.04 and Windows 7 (dual boot). 

Not too long ago, I was using the Windows 7 partition with no issues. I shut down, got to work and when I booted, the laptop just kept rebooting before GRUB would prompt me to choose what to boot to. (Ubuntu is the default)

I thought it may be a hard drive issue, but the on-board diags said everything was ok. 

I reinstalled Ubuntu on its partition and was able to log in to both partitions again, though I lost all of my settings on the Ubuntu side (i chose to format the partition)

Well, same thing happened this morning and instead of reloading Ubuntu from scratch again, I'd like to repair the installation or GRUB if possible. Not too much personal stuff there, just don't want to reload everything again. 

I have booted to the Ubuntu disk and both partitions are there - I can mount the hard drive and browse the files. 

I'm a noob if not already evident. 

Thanks for any help.

---

### Post by andrewthomas on 2010-09-03
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

---

### Post by spdtrip on 2010-09-03
> **andrewthomas said:**
> [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
Excellent! This worked. 

Now to keep it from overwriting the MBR.

Thanks!!

---

