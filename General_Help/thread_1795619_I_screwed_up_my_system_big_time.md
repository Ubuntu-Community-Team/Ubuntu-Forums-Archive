---
title: "I screwed up my system big time"
date: 2011-07-03
forum: General Help
---

### Post by maxoctane on 2011-07-03
Well, I'm back on my iPad because I deleted the partitions and this is what came up

Error: no such partition
Grub rescue>  _

---

### Post by maxoctane on 2011-07-03
Please respond very promptly so I can know if I need to take my laptop in for professional repair.

---

### Post by Rubi1200 on 2011-07-03
Please do the following so we can see what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by maxoctane on 2011-07-03
> **maxoctane said:**
> Please respond very promptly so I can know if I need to take my laptop in for professional repair.

No, I can't even get into windows xp.
It just gives me that black screen with the no such partition thing.

---

### Post by Rubi1200 on 2011-07-03
You need to get hold of either an Ubuntu CD or USB and boot the computer with it to run the script.

There are instructions on this page on how to create a CD/USB and how to boot the computer with it:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

