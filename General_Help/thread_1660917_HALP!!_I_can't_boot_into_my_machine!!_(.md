---
title: "HALP!! I can't boot into my machine!! :("
date: 2011-01-06
forum: General Help
---

### Post by Spaarkplug on 2011-01-06
Hi all,

I put my computer (which was working fine) into suspend and the battery died overnight. Now it will not boot. I get:

mount: mounting /dev/disk/by-uuid/c3c4608e-fb99-4989-bfe2-ede4aec72b38 on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting / sys/ on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= boot arg

BusyBox v1.10.2 (Ubuntu 1:1.10.2.2ubuntu7) built-in shell (ash)

(initramfs)

:confused:

I dont know what to do. I tried everything I know to fix it. I dont want to lose my data.

I was digging around for solutions and I found this --> [http://ubuntuforums.org/archive/index.php/t-1244466.html](http://ubuntuforums.org/archive/index.php/t-1244466.html) and was more sad because that guy lost his data.

Will y'all please help me?

---

### Post by wilee-nilee on 2011-01-06
Since this site has a lot of people dual booting and running wubi setups, and no mention by you of any OS do this please. It will give us a look  at the whole set up what it is and where stuff is at.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

---

### Post by Spaarkplug on 2011-01-07
I get the following when I run the script, and then nothing happens. I just remains like that...

ubuntu@ubuntu:~/Desktop$ sudo bash boot_info_script055.sh 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda5 for information... 

:(

I use the latest Ubuntu by the way, 10.10 maverick meerkat.

---

### Post by wilee-nilee on 2011-01-10
The command is this with the script on the desktop.
```
sudo bash ~/Desktop/boot_info_script*.sh 
```

This is the only method I use.

---

### Post by bcbc on 2011-01-10
If you've got important data, boot a live CD and run "photorec" on it. It's read only access that can recover data from any file system, broken, formatted or not. [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

To install it from a live CD go to the Terminal and run:
sudo apt-get install testdisk

And you'll need a USB or one of your good partitions to store the recovered files.

After that you could try repairing the partition.

---

