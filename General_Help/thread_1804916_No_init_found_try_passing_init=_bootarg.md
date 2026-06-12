---
title: "No init found try passing init= bootarg"
date: 2011-07-15
forum: General Help
---

### Post by worldblackstar on 2011-07-15
I installed the ubuntu 10.10 inside windows xp 2 months back.  It works perfectly for 2 months.  Today i had problem with booting into ubuntu.

It showing[B]: 
[/B]mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /dev on /root/sys failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init.
No init fount.  Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built in shell (ash)
Enter 'help' for a list of build in commands

(initramfs)
--------------
See there is lot of page in internet explaining how to recover this one using live cd:

One of that page is:
[http://ubuntuforums.org/showthread.php?t=1386549](http://ubuntuforums.org/showthread.php?t=1386549)

What all they are saying , use fsck command.  Unfortunately i tried lot of time.  
I got this only but my problem is not solved:
buntu@ubuntu:~$ sudo fsck -y /dev/sda2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?


May be it is different for linux installed inside windows.


If you have met with this error and got solution, Please let me know.
Thank you.

---

### Post by Rubi1200 on 2011-07-15
Hi,
to help us troubleshoot this problem, please do the following:

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

### Post by worldblackstar on 2011-07-17
Ok Thanks.
My problem solved.  
Someone had similar problem helped me to solve it.

---

### Post by Rubi1200 on 2011-07-19
Sorry for the delayed response; been busy at work.

Okay, great news that you got this sorted out.

Please mark this thread Solved using the Thread Tools near the top of the page.

---

