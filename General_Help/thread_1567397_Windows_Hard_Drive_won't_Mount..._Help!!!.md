---
title: "Windows Hard Drive won't Mount... Help!!!"
date: 2010-09-03
forum: General Help
---

### Post by RCW777 on 2010-09-03
Help is appreciated...
 
Wierd issue... Windows XP Laptop hard drive is stuck in a hibernated mode. Will not let me access it through Windows, period.
 
I loaded Ubuntu Live on the suggestion of a coworker in order to retrieve my important files by hooking up the Windows HD through a USB adapter (Inland).
 
Ubuntu recognizes the 160GB HD, but refuses to mount the drive because "Windows is Hibernated." I Know my disk is hibernated, I need a way to get my important files from the drive...
 
(Screen Shot Attached in .jpeg format)
 
I know very little abount Ubuntu so please keep that in mind with your gracious replies.
 
Thank you in advance!!!
 DOTV
(Dieing On The Vine)

---

### Post by Smart Viking on 2010-09-03
Hopefully the two following commands will work for you, paste them into  the terminal program(Applications->Accessories->terminal) and  press enter:

```
sudo mkdir /media/mount
```
Then type:
```
sudo mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /media/mount
```
Just paste them into the program and press enter, and it should be mounted. :)

---

### Post by RCW777 on 2010-09-04
Thanks so much Viking! It worked!

---

