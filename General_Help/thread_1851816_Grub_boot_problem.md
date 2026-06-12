---
title: "Grub boot problem?"
date: 2011-09-29
forum: General Help
---

### Post by PFactorial on 2011-09-29
Hello,
I've been using Ubuntu for about a month and I tried messing with the partitions to install Linux Mint too.
And I didn't really like Linux Mint so I deleted the partition in which it was in, leaving Ubuntu's partition undisturbed. And when I tried to boot again, it wouldn't boot. It couldn't find the boot partition.

I looked at the GParted manual, and it said the Master Boot Record was disturbed and broken or something since I tried to install that new OS. I tried the instructions used to restore it, but it said "/boot/grub/stage1/" was not found. I went to look and sure enough, there was no stage1.

I'm running Linux Mint off of a Live CD right now, and I need the fix soon.
So may anyone help me?
Thank you.

---

### Post by PFactorial on 2011-09-29
I saw this post:
[http://ubuntuforums.org/showthread.php?t=1114005](http://ubuntuforums.org/showthread.php?t=1114005)
and I seem to have the same problem but I don't really get it.

---

### Post by Quackers on 2011-09-29
I would suggest that you boot from the Ubuntu live cd (NOT the Mint live cd) and select "try Ubuntu" then open a terminal and run ```
sudo fdisk -lu
``` then decide which partition is your Ubuntu root partition. You can then re-install grub using that partition with the following commands ```
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX
```  where /dev/sdXY in the first command is your Ubuntu root partition (eg /dev/sda5) and /dev/sdX in the second comand is the drive which you boot from (or want grub installed on) - eg /dev/sda.
That should report "Completed. No errors". 
You can then reboot and you should get back into Ubuntu. If you need other operating systems in the grub menu open up a terminal and run ```
sudo update-grub
```

---

### Post by raja.genupula on 2011-09-29
+1 this link also can help you on this issue 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by PFactorial on 2011-10-24
Wow thanks the Grub Restore software worked! Thank you for the timely reply and solution

---

