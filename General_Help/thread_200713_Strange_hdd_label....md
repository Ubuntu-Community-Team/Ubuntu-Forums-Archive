---
title: "Strange hdd label..."
date: 2006-06-20
forum: General Help
---

### Post by spidernik84 on 2006-06-20
Hi, after some mass upgrade my HDD label shows as shown in the attachment...
Tried to rename it but without any success.
Any clue? :(

Ubuntu 6.06 and gnome

---

### Post by barbarian on 2006-06-20
Wau, cool, how you achieved it?=D>  

seriosly try:
*sudo dpkg-reconfigure locales*

---

### Post by matrooswolf on 2006-06-20
I get those same signs for some letters, e.g., when hovering above the attached thumbnail in your post ...
But I cannot help you ...

---

### Post by matrooswolf on 2006-06-21
Try this
```


sudo apt-get install xfonts-intl-arabic
sudo apt-get install xfonts-intl-asian
sudo apt-get install xfonts-intl-chinese
sudo apt-get install xfonts-intl-chinese-big
sudo apt-get install xfonts-intl-european
sudo apt-get install xfonts-intl-japanese
sudo apt-get install xfonts-intl-japanese-big
sudo apt-get install xfonts-intl-phonetic
sudo apt-get install gsfonts-x11
sudo apt-get install msttcorefonts
sudo fc-cache -f -v

```

---

### Post by spidernik84 on 2006-06-21
Uff, did what you suggested but no way, that "cool"(i do NOT like it barbarian :D ) label is still there! :(

Wtf, how can i rename it easily? Keeps saying me i have no privileges for doing that!

Thanks for your suggestions, btw

---

### Post by spidernik84 on 2006-06-28
Sorry for bumping but i'm still fighting against gnome to get back to a serious label :D

Is there any way to rename a label via terminal? Can't find out how via gnome...

Thanks!

---

### Post by yopnono on 2006-06-28
have you tried just to restart the machine?

---

### Post by Buffalo Soldier on 2006-06-28
The title said it's for renaming USB thumb drives, not sure whether it will work on harddisk. Hope at least it can give you ideas on where to proceed next.

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by spidernik84 on 2006-07-02
I've just solved the problem: i had to rename my hard disk while running windows xp...looks like the os gave a name ubuntu did not like :|

Thanks for your help once again ;)

---

### Post by bryanlking on 2006-07-02
For your future reference, you can change drive labels in Linux.

For Ext2/Ext3 filesystems -
     # e2label <device> NewLabel

For ReiserFS -
     # reiserfstune --label NewLabel <device>

BK

---

