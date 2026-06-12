---
title: "Dialog box when trying to click M3U files"
date: 2006-06-06
forum: General Help
---

### Post by Subban on 2006-06-06
Hi, I have looked through the forums and can't find a solution to this.

When trying to double click an M3U file it opens a dialog asking if I want to:
Run In Terminal / Display / Cancel / Run

I have right clicked the m3u files, choosen Properties then Open With tab, and tried to set to either Rhythmbox or XMMS(prefered choice) it doesn't however open the m3u file in these without first putting the dialog up onscreen and I have to choose 'Display'

Any help would be greatly appreciated as this is probably a minor problem but is driving me daft, Breezy had nps, its just Dapper for me.

---

### Post by GameGod on 2006-06-06
Hmmm, it looks like your .m3u files are executable for some reason maybe... If you right click on them, and go to "Permissions", uncheck the executable boxes...

---

### Post by Subban on 2006-06-06
Thank you very much GameGod you were absolutely spot on.

For some reason the executable flag was set, clearing that and all is well again.

---

### Post by .t. on 2006-06-06
Are they on a vfat/ntfs partition? I find that all of the files I used to have (NO MORE CLOSED SOURCE) on windows were executable by default.

---

### Post by ifokkema on 2006-06-06
[QUOTE=.t.]Are they on a vfat/ntfs partition? I find that all of the files I used to have (NO MORE CLOSED SOURCE) on windows were executable by default.[/QUOTE]

That's right. NTFS and FAT32 don't store permissions like ext3 does. All files have the same permissions. You can set an umask for the drive in the /etc/fstab, but then your directories won't be executable and thus usable :)

---

