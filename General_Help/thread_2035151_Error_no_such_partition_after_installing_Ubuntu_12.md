---
title: "Error: no such partition after installing Ubuntu 12.04"
date: 2012-07-30
forum: General Help
---

### Post by gabrielddimitrov on 2012-07-30
Hello guys,
I'm newbie here. Yesterday I decided to install Ubuntu 12.04 as I have already installed Windows 7 and want to go for dual boot. The problem is it doesn't shows me the boot menu. This is what I get:
> 
Error: no such partition
grub rescue>
First, I installed it manually and when I saw this message, I started searching for the solution. Tried to fix it many ways - recommended boot repair, manual GRUB2 reinstall, GRUB2 upgrade, ensured that it's in the right dev/sda drive and dev/sda7 partition (in my case), but still the error occurs... Even when I used EasyBCD, I made a Ubuntu boot entry but when I select it, the same happens.
So, I deleted all linux partitions and tried automatically with the alongside option in the installer. The main partition was sda6. Well, it didn't fixed it again. After then I restored the original MBR of win7 and now I'm writing you through it. Here is the link of the boot info script: [http://paste.ubuntu.com/1118378/](http://paste.ubuntu.com/1118378/) What am I doing wrong? Hope you answer me. Thanks!

---

### Post by gabrielddimitrov on 2012-07-30
Another mess up seems happened, somehow after the alonside install and after I deleted its linux partitions. Gparted shows that my logical partition(Local Disk D) have bad sectors and it is with extended file system, while Acronis disk director and windows disk manager shows everything is ok and it is as it was before - ntfs file system. There's no any data loss in that partition or problems, maybe its something from GParted? I attached a pic to see what I really mean. Sorry for the double post. Hope you'll help me. Thanks.

---

### Post by gabrielddimitrov on 2012-07-30
Anybody? :( I really need to have Ubuntu on this system.

---

### Post by Mark Phelps on 2012-07-31
According the the screen shot, the NTFS partition has over 140 bad sectors!  You need to fix THAT before you do anything else.

What might work is using Win7:
1) Boot into Win7
2) Click on Computer in the menu
3) Click on the "drive"
4) Click on properties, tools, Check the drive for errors

IF this works, it will run CHKDSK on the "drive" -- and that may fix the filesystem corruption.

---

### Post by gabrielddimitrov on 2012-07-31
I did a full format on that partition yesterday, backup my files and put them back in, now I check for errors and bad sectors on it. ...And finally I found that it was my wrong, the unallocated disk space I made was really too small - just 8GB, which I found it isn't enough, should be at least 10GB. I will make it 25GB and try Ubuntu again. I have just one question now. Will resizing partition with the ubuntu installer cause data loss? Thank you for the response. :)

---

### Post by oldfred on 2012-07-31
Always best to resize Windows system partition with Windows partitioning tools, eveything else you can/should  do in gparted. I think gparted will not let you make a partition too small, but may let you make it too small to be really usable.

---

