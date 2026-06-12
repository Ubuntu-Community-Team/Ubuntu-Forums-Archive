---
title: "Ubuntu on Dell Dimension 5150C"
date: 2011-11-18
forum: General Help
---

### Post by badkidjdd on 2011-11-18
I installed Ubuntu on a partition of the hard drive in my 2006 Dell Dimension 5150C. At first it worked fine but then I decided to reinstall Ubuntu and change the partition size and Ubuntu still works great, but the Windows XP partition doesn't seem to be working. This isn't a huge deal to me because I know Ubuntu is better anyway, but I am unable to get the computer to boot to anything besides Ubuntu. When I turn the computer on, it shows that GRUB menu and Windows XP is on the list but when I select it, the screen goes blank for a few seconds and then it shows that menu screen, only allowing me to boot into Ubuntu. I know I haven't screwed up the Windows XP drive because I can still see all the files in the Ubuntu file manager, so is there any way to fix this?

---

### Post by Mark Phelps on 2011-11-19
If you have Ubuntu installed to separate partitions, then you installed GRUB to the MBR of the drive in the process -- removing the ability to boot into XP from startup.

What you could try is regenerating the GRUB menu -- as a first step.

Boot into Ubuntu, open a terminal and enter "sudo update-grub".  Then, reboot.  Try selecting XP now.

If it still does not boot, then you could try repairing its boot files using the Boot-Repair utility.  See the link below:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

