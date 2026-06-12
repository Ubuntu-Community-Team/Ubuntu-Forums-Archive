---
title: "usb stick"
date: 2012-04-25
forum: General Help
---

### Post by sperian on 2012-04-25
hey, i have a usb storage stick and when i plug it in nothin happens. the computer doesnt see it at all. i cant find it in gparted either. the light on the stick comes on but thats it. any help would be great.

---

### Post by houseworkshy on 2012-04-25
Take a peek in "disc utility" which is in System>Administration, that may see it.  It could be something to do with it's format.  A friend brought one round here which had been formated to something exotic by win7 and that behaved as you described.  I re-formated it to FAT32 and it worked again.
If not that it's a mounting issue, searching for "mounting usb stick" and other word combo's on those lines in will bring up dozens of posts, look for threads marked as solved.

---

### Post by km3952 on 2012-04-25
Does sudo fdisk -l in a terminal tell you anything useful?

(It should be in the id column)

---

### Post by km3952 on 2012-04-25
If you wish to reformat it to fat32 dos;

in a terminal do;  sudo mkdosfs -F 32 /dev/<your drive number here>    (i.e. /dev/sdb1 or similar)

---

### Post by sperian on 2012-04-25
I cant find the drive number to Format it. 
In fdisk it doesn't appear at all. Just picks up my main hard drive.

---

### Post by sperian on 2012-04-25
It randomly appeared just then. Prob fixed. 
Where is system-administrater I cant find administrator anywhere. Im using ubuntu 11.10

---

### Post by dino99 on 2012-04-25
set "usb legacy" to "auto" in your bios

---

### Post by sperian on 2012-04-25
I only have legacy USB support and it is enabled. No auto setting, just enabled or disabled.

---

### Post by Ceiber Boy on 2012-04-25
Do you have another machine to try it on? Even a windows machine perhaps!

You might be able to get some more information about format etc..

Trust their is not any important information on it!

---

