---
title: "Boot failure"
date: 2011-06-01
forum: General Help
---

### Post by JackofHarts94 on 2011-06-01
Hi, 

ubuntu crashed on me when i went to take out the power cable from my laptop , i got a frozen screen and it would not respond. so i decided to hold down the power button to turn it off and restart. when i did this i got this message: 

NTFS5 error "prefix" is not set
 Not found; /ubuntu/disks/root.disk
 Not found; /ubuntu/install/boot/grub/grub.cfg

then it takes me to a grub command line interface. i have a dual boot system and when i go on windows 7 if boots up fine no problem. any help would be greatly appreciated

---

### Post by Rubi1200 on 2011-06-02
Hi and welcome to the forums :-)

You need to either use or get hold of a LiveCD/USB (there are instructions on the page further down):
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Then do the following:

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

### Post by JackofHarts94 on 2011-06-04
thanks very much, i will mark this as solved. this is the second time this is happened to me. first time it happened i uninstalled and reinstalled and wsnt very happy about it haha. hopefully it doesnt happen again

---

### Post by Rubi1200 on 2011-06-04
Well, I am glad you got it sorted out in the end.

Be aware that Wubi installs tend to be quite sensitive to hard shutdowns, whether from the Ubuntu or the Windows side.

If you need more help with anything, just ask.

---

