---
title: "ubuntu 11.04 boot errors"
date: 2011-06-16
forum: General Help
---

### Post by weissnich on 2011-06-16
hi, 

i cannot start a newly installed 11.04, i installed the boatloader into the root partition because i use another bootload called boot-us which start from its own partition, this worked fine with other ubuntu versions, but now i got the following errors after i try to start ubuntu with grub:

error no such device following a number
error no such disk
error you need to load the kernel first

can anybody help me with this?

---

### Post by Rubi1200 on 2011-06-16
This may have been fine to do with the older version of GRUB, now referred to as legacy-GRUB, but GRUB2 does not seem to play nicely when installed to the PBR.

Either you need to install GRUB to the MBR of the drive and let it control all booting or revert to legacy-GRUB. Perhaps, one other possibility would be to create a separate boot partition for Ubuntu.

In any event, to give us a better overview of the current state of the system, I suggest you post the results of the boot info script:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by weissnich on 2011-06-16
I did the following, i used a live cd and did a grub-update, then it worked, that's all:popcorn:

---

### Post by Rubi1200 on 2011-06-16
Excellent! Glad you got things sorted out :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

