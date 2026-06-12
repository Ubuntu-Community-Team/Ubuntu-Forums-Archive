---
title: "I don't have permisions to save documents! Please help."
date: 2010-04-02
forum: General Help
---

### Post by Cityscape on 2010-04-02
Hi,

I have a computer with 3 hard drives/partitions. On the 2 non-OS ones I can not save documents from Emails or websites. It tells me "You do not have permission to write this file". I'm the computer administrator, why can't I save a simple document!

Can someone please help me, I want full access permanently to these drives?

---

### Post by Cityscape on 2010-04-02
BTW my PDF is Adobe Reader 9.x

---

### Post by Cityscape on 2010-04-02
Foxit will not save them either. I just get an error beep.

---

### Post by Arsaine on 2010-04-02
You are trying to save .pdf files?
Try saving them in some other file format, if possible.
And why Foxit and Adobe, are you trying to save these files while running Ubuntu or are you using Windows?

---

### Post by Cityscape on 2010-04-02
I just checked the properties>permissions on some folders in these 2 other hard drives and it says can't modify it because I'm not the owner. The Root is the owner, but I should be the owner and have the power to modify the permissions of my own files.

---

### Post by Arsaine on 2010-04-02
> **Cityscape said:**
> I just checked the properties>permissions on some folders in these 2 other hard drives and it says can't modify it because I'm not the owner. The Root is the owner, but I should be the owner and have the power to modify the permissions of my own files.

Well okay, these hard drives need to be mounted so as to give you permission to read and write. Are they mounted automatically? Could you post your fstab here?

---

### Post by JustinR on 2010-04-02
Try pressing "ALT + F2" and type, "gksudo naulilus". This will open the file manager. Navigate to the folder were you want to save the file to, right click it, and go to the permissions tab and change them so you can read and write.

Edit: Automatically mounted partitions are owned by root by default. So you can try what I wrote above the on the directory to the drive in /media. Or Arsaine can tell you how to edit your /etc/Fstab file to have it automatically mount with read/write permissions. (The latter solution is permanent)

---

