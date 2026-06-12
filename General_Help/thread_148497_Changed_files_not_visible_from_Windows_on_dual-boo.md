---
title: "Changed files not visible from Windows on dual-boot when writing to FAT32"
date: 2006-03-22
forum: General Help
---

### Post by schleppkraut on 2006-03-22
Hi,

Thought this day would never come as I usually found the answers to all my Breezy needs in the forum. This time my search came up empty.

I have Breezy installed as a dual-boot on my Vaio SRX-Series. Works fantastic! Hotkeys (change display Brightness, Volume, etc), Suspend to disk, Bluetooth, Wi-Fi, etc. - all working from the start. Great work!

This was working for quite a while now with no problems. After a recent crash I can't permanently write to my FAT32 partition from Breezy anymore. e. g. If I create a picture file and copy it to the FAT32 partition everything looks normal. I can look at the picture and move it around. I can even suspend or reboot the computer and the file still looks fine from Breezy. As soon as I boot XP, the file is gone! No sign of it ever being there. Windows chkdsk reports "lost chains" and some errors returning the number of files I tried writing to the FAT32 partition.

Even more bizarre... when I change a file that is saved on the FAT32 drive... I can only access the "old version" from Windows. As if the changes are stuck in RAM or SWAP.

I also have a FAT32 external HDD. Same problems there - I simply can't write changes to it. Unmounting and remounting doesn't help. fstab looks pretty much like this:

```
/dev/hda5       /media/windows  vfat    iocharset=utf8,umask=000   0       0
```

If I e-mail myself the files I just "saved" on the FAT32 partition, they arrive just fine.

Nothing special in my Breezy setup otherwise. Any ideas?

---

### Post by schleppkraut on 2006-03-23
Usually I hate people who push threads back to the top, but this is rather urgent so I would appreciate any help.

Are there any packages I should consider reinstalling? Any tools I can use?

---

