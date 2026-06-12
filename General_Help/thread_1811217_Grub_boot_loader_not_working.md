---
title: "Grub boot loader not working"
date: 2011-07-24
forum: General Help
---

### Post by inabitofapickle on 2011-07-24
I'm in a real spot of trouble you see, I was playing with the Ubuntu side of my laptop, and I was looking a tweaks for it. I saw a program called BURG, Juts the pretty themed version of Grub I guess. Any who. I installed it, Terminal reported no problems. I decided to restart because of other changes I made. Now every time i start up my laptop, It tells me:

"GRUB loading.
 error : no such device : 572b8468-634b-42dc-be03-287f3a4d0bcf.
 Entering rescue mode...
 grub rescue>_"

Any help? My laptop is an Acer Aspire D255, Single Core atom N450, with a Hitachi HTS545012B9A300 HDD, There are two operating systems. Ubuntu 10.10 (personally my favorite.) and Windows Seven Home Premuim. 

What I'd like to do is save the Windows Side if I can. Or both. But Mainly windows for my iTunes.

Please please help me! I might give you a Cookie :P:KS

---

### Post by Quackers on 2011-07-24
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by inabitofapickle on 2011-07-25
Okay. I tryed that, So I: Booted it up, Hit F12, Selected USB Boot, And then It gave me "DISK ERROR, press any key to restart" How do i fix that?

---

### Post by inabitofapickle on 2011-07-25
I also tried to format the Memory stick & then place ubuntu on it, boot from there etc. and it just says 
"Remove disks or other media.
 Press any key to restart"

---

### Post by Kira_Belka on 2011-07-25
> **inabitofapickle said:**
> I also tried to format the Memory stick & then place ubuntu on it, boot from there etc. and it just says 
"Remove disks or other media.
 Press any key to restart"

Hi, boot from Ubuntu Live CD/usb..
so.. execute in terminal 
     sudo fdisk -l

attach result here plz :)
I think firstly you had problem in grub.cfg
probably UUID of one of bootable devices was changed..
So now you have broken mbr(
but anyways show result of fdisk -l
before you try to repair GRUB)

so how to repair GRUB
..
Boot from Ubuntu Live CD/usb

then 
cd /media
sudo mkdir salvation
sudo fdisk -l

then you have to find your linux partition..
something like /dev/sda1 or sda2 or sda3 or ... :))
all depends from quantity of your real disk and partitions on it :) mmmm let's name it for exapmle sdXY ( where X 's number of physical disk, Y 's number of partition on it)

then you have to do next thing

sudo mount /dev/sdXY /media/salvation
 sudo mount --bind /dev /media/salvation/dev
sudo mount --bind /proc /media/salvation/proc

sudo chroot /media/salvation

then you can edit mtab and grub.cfg (because I think you grub couldn't find some bootable partition :(  )

then ...
sudo grub-install /dev/sdX

reboot and FUN :)

---

### Post by inabitofapickle on 2011-07-25
> **Kira_Belka said:**
> Hi, boot from Ubuntu Live CD/usb..
so.. execute in terminal 
     sudo fdisk -l

attach result here plz :)
I think firstly you had problem in grub.cfg
probably UUID of one of bootable devices was changed..
So now you have broken mbr(
but anyways show result of fdisk -l
before you try to repair GRUB)

so how to repair GRUB
..
Boot from Ubuntu Live CD/usb

then 
cd /media
sudo mkdir salvation
sudo fdisk -l

then you have to find your linux partition..
something like /dev/sda1 or sda2 or sda3 or ... :))
all depends from quantity of your real disk and partitions on it :) mmmm let's name it for exapmle sdXY ( where X 's number of physical disk, Y 's number of partition on it)

then you have to do next thing

sudo mount /dev/sdXY /media/salvation
 sudo mount --bind /dev /media/salvation/dev
sudo mount --bind /proc /media/salvation/proc

sudo chroot /media/salvation

then you can edit mtab and grub.cfg (because I think you grub couldn't find some bootable partition :(  )

then ...
sudo grub-install /dev/sdX

reboot and FUN :)





Okay, Just to get this "Live CD straight, it's just the .iso right?

---

