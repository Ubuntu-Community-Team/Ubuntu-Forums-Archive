---
title: "Automount NTFS on demand"
date: 2011-04-09
forum: General Help
---

### Post by Beowolf64 on 2011-04-09
I have created a desktop shortcut to the folder on NTFS volume. But it doesn't work unless the volume was mounted by clicking the icon in Places->Volume_Name. One possible solution is to mount NTFS volume at boot time but that requires editing of fstab (directly or indirectly). Is there a way to mount the NTFS volume on demand when shortcut is clicked? Maybe some sort script which  would emulate clicking Places->Volume_Name first and the open the shortcut?

Thanks,
Wolf.

---

### Post by vanadium on 2011-04-09
You can use pmount. pmount is not (anymore?) automatically installed by default, so there should also be another way.

---

