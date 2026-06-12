---
title: "installed using Wubi and got an Error  NTFS5:NO Wubildr"
date: 2011-09-19
forum: General Help
---

### Post by Jimwest1980 on 2011-09-19
Hello I have 3 hard drive 2 of them are running windows 7 OS 32 bit and 64 bit. I tried to install using windows installer. After I rebooted I got an Error saying 
using the UBUNTU From the windows boot loader I get 
Try (hd0,0):NTFS5: No Wubildr 
try (hd0,1) Invalid or Null
try (hd0,2) Invalid or Null
try (hd0,3) Invalid Or Null
try (hd1,0) NTFS5: No wubildr 
and it wont load past I have to CTRL ALT DEL to reboot and go back to the windows boot loader. I have tried to uninstall and reinstall. I have used the one from the ISO as well as the One from the website and let it download from the web. 32 bit and 64 bit  have failed not sure what else to do from here.

if anyone can give me a hand with this that would be great.

---

### Post by Rubi1200 on 2011-09-19
Hi and welcome to the forums :-)

Please post the results of the boot info script so we can get a better overview of what is happening.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by Jimwest1980 on 2011-09-19
here is the Error

---

### Post by Rubi1200 on 2011-09-20
Jimwest1980,
the only way we can help you deal with this is if you post the results of the boot info script.

This will help us determine what is going on and will make offering solutions much easier.

Thanks.

---

### Post by Jimwest1980 on 2011-09-20
> **Rubi1200 said:**
> Jimwest1980,
the only way we can help you deal with this is if you post the results of the boot info script.

This will help us determine what is going on and will make offering solutions much easier.

Thanks.


here is the TXT file 
Thank you for helping me to get this to work

---

### Post by bcbc on 2011-09-20
This a grub4dos issue (wubi uses that to boot). It's looking for the wubildr file and it doesn't get as far as the partition that it's on /dev/sdb2. I don't know why. 
So it looks on /dev/sda1 (hd0,0) - can't find it - looks for a couple of partitions that don't exists, then switches to /dev/sdb2 (hd1,0) and then gets stuck.

What can you do to fix it?
1. Boot a live CD, mount /dev/sda1 and copy wubildr to it
```
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo mount /dev/sdb2 /mnt
sudo cp /mnt/wubildr /media/win/wubildr
sudo umount /media/win
sudo umount /mnt
sudo reboot
```
That's a harmless solution that will most likely work fine.

2. Try partitioning and installing direct. With so much hard drive real-estate it shouldn't be too hard. e.g. /dev/sda is a single drive with one partition. You could install on there.

If you don't like either option, try a live USB (slower than Wubi but okay to check out Ubuntu) or a virtual machine.

---

### Post by Jimwest1980 on 2011-09-20
Thanks will try the other option. 
I wanted to be able to keep the windows boot loader instead of using the grub boot loader  because if i wanted to later take Ubuntu off I wouldn't have to do a full format to get ride of the Grub boot loader. 
I have used UBUNTU and Love it but was looking at this option so it would be easier to use. If i don't want it around any more I can just uninstall it.

---

### Post by Jimwest1980 on 2011-09-20
Thank you that worked and I am up and Running. 
thank you to everyone who helped me

---

### Post by Rubi1200 on 2011-09-20
Excellent! Glad you got things sorted out now :-)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

### Post by uncontrolable™ on 2011-09-21
Which option fixed your system, if you don't mind my asking?

---

### Post by Jimwest1980 on 2011-09-21
The Option from BC BC I followed his code using the live cd and it works

---

### Post by menyou on 2013-03-19
I am using window 8, and was trying to download “32 bit” 12.10 on my USB drive but when it reboots, I am getting these error messages. I need step-by-step assistance to solve this problem. I thank you in advance.
 
Try (hd0 ,0): NTFS5: NO Wubildr
Try (hd0, 1): NTFS5

---

