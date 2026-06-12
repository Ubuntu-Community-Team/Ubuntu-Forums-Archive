---
title: "screwed? - grub rescue"
date: 2010-02-23
forum: General Help
---

### Post by sincerelyydavid on 2010-02-23
so i deleted ubuntu from gparted. i tried to boot again into windows, a screen came up with something about grub rescue. how can i fix this? all i have is a linux cd and a windows 7 cd.

---

### Post by Arand on 2010-02-23
Boot the windows cd and use the repair install (I think there should be an option) or go to the command line and do```
bootrec /fixmbr
bootrec /fixboot
```Note, these commands to be done from the windows cd
- Arand

---

### Post by sincerelyydavid on 2010-02-23
i can't boot into the cd. everytime i try to, it just goes back to the screen with the grub rescue.
edit: i just booted my windows xp cd and it does boot. but when a blue screen comes up saying, "A problem has been detected and Windows has been shut down to prevent damage to your computer..."

---

### Post by Arand on 2010-02-23
If the CD doesn't boot, possibly the BIOS settings isn't set for CD booting, see if you can get into the bios and rearrange so that the CD boots before the disk (F1, F2, or Del key is common to enter bios setup).

I don't know what the windows XP CD thing is all about, if the w7 cd doesn't boot I don't see how the xp one would, unless the w7 cd is actually corrupt..

 - Arand

---

### Post by sincerelyydavid on 2010-02-23
> **Arand said:**
> If the CD doesn't boot, possibly the BIOS settings isn't set for CD booting, see if you can get into the bios and rearrange so that the CD boots before the disk (F1, F2, or Del key is common to enter bios setup).

I don't know what the windows XP CD thing is all about, if the w7 cd doesn't boot I don't see how the xp one would, unless the w7 cd is actually corrupt..

 - Arand
i don't think the windows 7 cd is corrupt. it's an "upgrade to windows 7 from vista" cd, which i ordered for free when i got my laptop that came with vista. can this cd do a full install of windows 7? because i stuck in my ubuntu cd and reinstalled ubuntu, but i don't really want ubuntu, which is why this happened in the first place when i deleted the ubuntu partition and messed up windows.

---

### Post by Arand on 2010-02-23
It may very well be that this CD is not bootable.

This might be worth a try, at the grub rescue prompt use:```
insmod ntfs
set root=(hd0,1)
```
(This (hdX,Y) has to correspond to the partition where windows boots from, normally first disk (0), first partition (1), but may be different)
Then```
chainloader +1
boot
```

Then when you get into windows, run the bootrec commands mentioned above from an administrator command prompt

 - Arand

---

### Post by lidex on 2010-02-23
> **sincerelyydavid said:**
> i can't boot into the cd. everytime i try to, it just goes back to the screen with the grub rescue.
edit: i just booted my windows xp cd and it does boot. but when a blue screen comes up saying, "A problem has been detected and Windows has been shut down to prevent damage to your computer..."

Have a look at this page; section: "How to restore the Windows Vista or 7 bootloader"

[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Arand on 2010-02-23
@lidex *&#8593;&#8593;&#8593;
Already tried and discarded, since no bootable CD.
- Arand

---

### Post by lidex on 2010-02-23
You can download a recovery disk from here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by oldfred on 2010-02-23
Your win7 upgrade disk will require the Vista install to upgrade, it is not a full install from a blank HD. It wants to see that you have the previous install to qualify for the upgrade.

---

