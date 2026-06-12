---
title: "how do I unmount an .img file from my usb which is read only????"
date: 2009-12-08
forum: General Help
---

### Post by Pycnopodia on 2009-12-08
I made a USB flash drive have a bootable command following these directions([https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)). Now I cannot get rid of it. Please help I would really like to get my USB back. thanks

---

### Post by pastalavista on 2009-12-08
Open a terminal (Applications-> Accessories-> Terminal) and enter these commands
```
sudo fdisk -l
``` and enter your password. (the password keystrokes won't show up but hit enter anyway) This will tell you the dev # (sdb1 or similar) of the USB drive. Then enter```
sudo umount /dev/sd**
``` replacing the ** with the actual letter and number of your drive.

---

### Post by Pycnopodia on 2009-12-08
Ok, that sounds good but I am not getting my USB drive to come up when I plug it in (in fdisk), so I don't know what name to call it.

---

### Post by pastalavista on 2009-12-08
If it doesn't "come up", you have gotten "rid of it" Try using the gnome partition editor (gparted) to unmount/reformat the flash drive... download it first```
sudo apt-get install gparted
```
It will be in the System-> Administration menu.

---

