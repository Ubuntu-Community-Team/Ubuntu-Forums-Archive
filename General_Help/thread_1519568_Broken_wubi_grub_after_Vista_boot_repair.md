---
title: "Broken wubi grub after Vista boot repair"
date: 2010-06-28
forum: General Help
---

### Post by tuthmosis on 2010-06-28
I broke my Vista MBR after an attempt to install BURG on wubi. (Which i know now should not be done !)

I was able to "apt-get install mbr" and got the OS selection screen back asking me to choose between Vista and Ubuntu... Unfortunatly, both failed to start with similar problems.

Vista: winload.exe was missing or corrupted
Ubuntu: "some similar file" was missing or corrupted

So i used a Vista repair CD and got Vista back. (Which i am using now.)
But when i try to load Ubuntu, i still get the same error as before.

I guess Grub2 should be reinstalled... How should i do that with WUBI ?

I just read the [section]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?") on how to repair the vistual Ubuntu partition at [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)... unfortunatly, it just describe how to mount the virtual partition and it doesn't say anything about fixing it.

Thanks for any help.

---

### Post by tuthmosis on 2010-06-28
Just solved the problem by myself like a big boy !!!

The missing or corrupted file was wubildr.mbr.

My instincts guided me to this tool from neosmart. (easybcd)

It fist showed a kind of report with Ubuntu present but with no disk values. As it is a wubi, the disk should have been c:/.   The path to wubildr.mbr was already there....

The only thing to do was to fix with the button on the left menu and here i am !

2 full days without Ubuntu !! WOW... I was starting to experience some auto mutilation compulsions !

---

### Post by Mark Phelps on 2010-06-28
For future reference, Wubi does NOT use GRUB or GRUB2; instead, it uses its own version known as GRUB4DOS.  So, don't do any GRUB/GRUB2 installs or updates.

---

