---
title: "boot issue"
date: 2010-07-27
forum: General Help
---

### Post by wahshan on 2010-07-27
Hi . 
i'll drop my issue here and i hope it can be fixed :) 
i am a windows user and i wanted to try ubuntu so i downloaded the wubi.exe and installed it from windows and it worked amazingly but somehow i wanted to change the bootloader interface to be more organized than the original ... after i done doing that using the terminal : *command used below

[PHP]sudo add-apt-repository ppa:bean123ch/burg
[/PHP]
[PHP]sudo apt-get update && sudo apt-get install burg burg-themes
[/PHP]
[PHP]sudo burg-install "(hd0)"
[/PHP]
[PHP]sudo update-burg
[/PHP]

now when i boot up my laptop it says : 

> GRUP Loading .
error : no such device : 62c64a66-8a48-4b1b-8cbf-8e6883c4e45c
entering rescue mode
grup rescue< _

Please Guide me to go through this because i have my final year project inside and i don't want to format and lose everything just like that :( 


Info you might need: 
windows 7
ubuntu the latest 

my life between your hands :(

---

### Post by stlsaint on 2010-07-27
Now i am aware of what burg is but im not sure how the procedure for installing is but it seems that you have changed where grub looks to for root (/). From my understanding Grub is looking for a UUID for a device but data has been moved to another device. So please run the bootinfoscript from my signature. Download it from the link and follow the instructions. To run the script. It will produce a RESULTS.txt file that you can attache here to topic and we will find out how to edit your fstab to point grub to the correct device. From there you should be able to start fresh with burg. Speaking of which you probably should have removed grub prior to installing burg.

---

### Post by wahshan on 2010-07-27
stlsaint thanks for the guide but i don't have any recovery CD's for both windows or ubuntu, all i have is a Live CD for ubuntu 9.10 and i used it and now i can access my windows 7

---

### Post by stlsaint on 2010-07-27
> thanks for the guide but i don't have any recovery CD's for both windows or ubuntu

The really isnt a UBUNTU Recovery disc. The livecd provides all functionality needed. There are disk like super grub but not just tailored for ubuntu unless you make one!! :D
Please mark thread as solved.

---

### Post by bcbc on 2010-07-27
> **wahshan said:**
> Hi . 
i'll drop my issue here and i hope it can be fixed :) 
i am a windows user and i wanted to try ubuntu so i downloaded the wubi.exe and installed it from windows and it worked amazingly but somehow i wanted to change the bootloader interface to be more organized than the original ... after i done doing that using the terminal : *command used below

[PHP]sudo add-apt-repository ppa:bean123ch/burg
[/PHP]
[PHP]sudo apt-get update && sudo apt-get install burg burg-themes
[/PHP]
[PHP]sudo burg-install "(hd0)"
[/PHP]
[PHP]sudo update-burg
[/PHP]

now when i boot up my laptop it says : 



Please Guide me to go through this because i have my final year project inside and i don't want to format and lose everything just like that :( 


Info you might need: 
windows 7
ubuntu the latest 

my life between your hands :(
Just reinstall the windows bootloader.

With wubi, you have to loop mount the virtual disk - it's not a partition - and grub (and I assume burg) is expecting to find it's core.img and grub menu somewhere but (since it doesn't exist yet - not yet loopmounted) you're out of luck.

Install the windows bootloader and windows will boot. You may have messed up your wubi though. If this is true, boot a live CD, loopmount it, chroot into and reinstall grub2 (but don't install the grub2 bootloader anywhere). A lot of work indeed. (I'd just copy off any important data and reinstall).

If you don't have a windows disk lying around, you can also use the lilo bootloader from a live CD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```

---

