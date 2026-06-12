---
title: "File access inside Natty/XP:Home Dual Boot"
date: 2011-05-18
forum: General Help
---

### Post by PrfJennings on 2011-05-18
Howdy, I just installed a dual boot on my Acer Aspire One and it runs great. I was wondering is there anyway to access the files from either side? If so I can't see the XP file system from the Ubuntu system.

---

### Post by wildmanne39 on 2011-05-18
> **PrfJennings said:**
> Howdy, I just installed a dual boot on my Acer Aspire One and it runs great. I was wondering is there anyway to access the files from either side? If so I can't see the XP file system from the Ubuntu system.
Hi, you should be able to see windows by going into places on your menu, it might just show the size of your windows partition. There is now way to see ubuntu from windows.

---

### Post by PrfJennings on 2011-05-18
I am still able to boot into XP, however under places the drive that shows up is "file system" which only contains the Natty File info, I tried it on the Unity interface and classic, same thing.

EDIT: I plugged in a SD card and it can read that on both sides.

---

### Post by wildmanne39 on 2011-05-18
> **PrfJennings said:**
> I am still able to boot into XP, however under places the drive that shows up is "file system" which only contains the Natty File info, I tried it on the Unity interface and classic, same thing.

EDIT: I plugged in a SD card and it can read that on both sides.
Hi, open synaptic and in the search put in ntfs and install it if it is not installed.

---

### Post by PrfJennings on 2011-05-18
Yes, the ntfs support is installed.

---

### Post by wildmanne39 on 2011-05-18
> **PrfJennings said:**
> Yes, the ntfs support is installed.

Hi, what is listed when you go to places in the menu?

---

### Post by PrfJennings on 2011-05-18
Home Folder
Computer Under Computer I have the File System and the SD card
Templates
Trash
Network

---

### Post by wildmanne39 on 2011-05-18
> **PrfJennings said:**
> Home Folder
Computer
Templates
Trash
Network

Hi, go to administration open disk utility and look through the drives on the left of the panel and click on the windows drive and mount it, let me know if it works,or if it is not there.

---

### Post by PrfJennings on 2011-05-18
Yes it was mounted, I figured it out, the file system had put it under the /host folder. thanks for all your help!

---

### Post by wildmanne39 on 2011-05-18
> **PrfJennings said:**
> Yes it was mounted, I figured it out, the file system had put it under the /host folder. thanks for all your help!

Hi, your welcome.

---

