---
title: "Windows 7 reboots at splash screen"
date: 2010-05-09
forum: General Help
---

### Post by censory on 2010-05-09
Whenever I select windows 7 from grub it will boot up to the splash screen and then restart.
I do NOT have a repair cd.

---

### Post by bumanie on 2010-05-09
You can get a repair disk from [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/") - fix the boot on win 7 and then reinstall grub 2 as per [here]("http://ubuntuforums.org/showthread.php?t=1195275") (assuming you are using grub 2). Point 13 should be the one you need.

---

### Post by censory on 2010-05-09
> **bumanie said:**
> You can get a repair disk from [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/") - fix the boot on win 7 and then reinstall grub 2 as per [here]("http://ubuntuforums.org/showthread.php?t=1195275") (assuming you are using grub 2). Point 13 should be the one you need.

Yesterday when I did this it booted into windows fine, but now it doesn't.
[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8930595&postcount=3](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8930595&postcount=3)
Anyway to do it without reinstalling grub?

---

### Post by bumanie on 2010-05-09
Well, meierfra. is basically an expert on grub and his instructions are from a [sourceforge page]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") - so if what he said didn't work, the only way to repair win 7 that I know of is to get the disk from neosmart (as you don't have your own) and then you would have to reinstall grub 2 as the repair disk will overwrite grub in the mbr.

---

