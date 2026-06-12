---
title: "quick terminal question"
date: 2010-04-02
forum: General Help
---

### Post by spiky001 on 2010-04-02
how do I cd in to a usb stick 
```
cd media/New Volume
```

it returns not found i,m just missing the bit where gap is in new volume

---

### Post by eksasol on 2010-04-02
Put a single hyphen around the location:
**cd '/media/New Volume'**

Or type _**cd** _, then open nautilus and go to the folder /media and drag the directory that you want into the Terminal window.

Now if your volume do not have a label yet, it will be shown in UUID format. In that case, you have to open GParted and give it a label.

---

### Post by spiky001 on 2010-04-02
That worked thks

---

### Post by theDaveTheRave on 2010-04-02
If you are using a usb and stick it in different ports the address may change.

if you set a specific label for the drive you can then get the fstab file to always mount it in the same location.

this thread has instruction on editing the fstab file.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

have fun.

David

---

