---
title: "Nothing appears in trash..."
date: 2009-08-24
forum: General Help
---

### Post by EmanuelO on 2009-08-24
I have sent multiple items to trash. I click the trash icon and nothing appears in the trash directory. Where are the files I am sending to trash and why don't they appear?

---

### Post by EmanuelO on 2009-08-24
Also, when I try to paste something into the trash I get an error.

*Operation not supported by backend*

---

### Post by EmanuelO on 2009-08-24
bump

---

### Post by uylug on 2009-08-24
Alright, first of all, are you deleting files under your File System or are they under some mounted media, such as a usb stick or maybe a ntfs windows partition?

---

### Post by EmanuelO on 2009-08-24
> **uylug said:**
> Alright, first of all, are you deleting files under your File System or are they under some mounted media, such as a usb stick or maybe a ntfs windows partition?
I am deleting within my filesystem. Not through any external device or foreign partition.

---

### Post by uylug on 2009-08-24
> **EmanuelO said:**
> I am deleting within my filesystem. Not through any external device or foreign partition.

That's weird. I've never had such a problem. When deleting files, if shift+delete is pressed, the file will not be moved to the trash. If you press delete it should be moved to trash.

---

### Post by tuxxy on 2009-08-24
Maybe they have been moved to root trash for some reason, its worth a look anyway as you may have things from a while back in their.  Run this command in terminal to check;

```
gksudo nautilus /root/.local/share/Trash/files
```

---

### Post by EmanuelO on 2009-08-24
I apologise. I appear to have wasted your valuable time. I just restarted and lo and behold the files were there. Thank you for your patience and assistance. I will try to be more patient before I ask.

---

### Post by tuxxy on 2009-08-24
> **annawei said:**
> You should check if you have cleared up all the files you sent to trash.

I think he already did :confused: and why are you advertising retail store websites in your sig?

---

