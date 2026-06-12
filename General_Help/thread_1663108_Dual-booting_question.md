---
title: "Dual-booting question"
date: 2011-01-09
forum: General Help
---

### Post by neon401 on 2011-01-09
Hello

I'm in a rather peculiar situation. I have a laptop with two partitions, one with Windows XP and one for storage (formatted in NTFS). I would like to install Ubuntu on the storage partition, but my problem is that I can't boot from CD (or anything else) because my BIOS is password protected. I obviously don't know the password.

My question is: If I plug the laptop's hard drive into another computer, install Ubuntu as described above and then reconnect it to my laptop, will it work?

Thanks!

---

### Post by James_Lochhead on 2011-01-09
> **neon401 said:**
> My question is: If I plug the laptop's hard drive into another computer, install Ubuntu as described above and then reconnect it to my laptop, will it work?

Yes.

---

### Post by neon401 on 2011-01-09
Alright, so I proceeded with installing Ubuntu, everything worked as expected, the GRUB menu popped up after install, Ubuntu booted fine and all was good.

However, after restarting, booting into Windows XP and restarting again, the GRUB menu no longer shows up and the computer gets stuck in an infinite reboot loop, so now I can't boot into either OS. I formatted Ubuntu and did everything again, but the problem shows up as soon as I boot into Windows XP.

What could be causing this? Is there any fix?

Thank you for any help.


EDIT: After some extensive Googling, I managed to find out the cause. The MBR gets modified by a program installed in Windows XP, in my case it was ZISD (Novell ZENworks Image-Safe Data). Removing the problem should solve the problem. Unfortunately, I'm not personally able to uninstall programs due to restrictions set by my works' sysadmin.

Further reading: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

---

