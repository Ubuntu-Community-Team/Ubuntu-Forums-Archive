---
title: "External HDD boot"
date: 2010-04-13
forum: General Help
---

### Post by thebigob on 2010-04-13
Looking to make exteral HDD as a boot device...

I will try and explain what I am planning to make this a bit clearer.

I currently run ubuntu 9.10 on my laptop. I also have a partition with Windows installed.

This works great. When I boot up it loads grub I can choose between ubuntu and windows.

I have recently purchased an external usb sata disk dock. I have a couple of sata disks which I would like to install OS's on. (Things like Lucid to try it out before it is officially released.)

I use ubuntu as my work machine so dont want to mess about with the disk on the laptop if I can help it.

Back to my question. I want to make the external disk stand alone if that makes sense. 

I initially tried installing lucid on the usb sata disk and booted from usb. Though this didnt work even worse it also altered my grub table on the laptop disk. This meant that when I unplugged the usb grub died with an error device not found. Though i have now fixed this I was wondering if there is a way to make the usb disk a "stand alone boot disk"?

I maybe missing something obvious. Any input gratefully received.

---

### Post by Doctor Mike on 2010-04-13
> **thebigob said:**
> Looking to make exteral HDD as a boot device...

I will try and explain what I am planning to make this a bit clearer.

I currently run ubuntu 9.10 on my laptop. I also have a partition with Windows installed.

This works great. When I boot up it loads grub I can choose between ubuntu and windows.

I have recently purchased an external usb sata disk dock. I have a couple of sata disks which I would like to install OS's on. (Things like Lucid to try it out before it is officially released.)

I use ubuntu as my work machine so dont want to mess about with the disk on the laptop if I can help it.

Back to my question. I want to make the external disk stand alone if that makes sense. 

I initially tried installing lucid on the usb sata disk and booted from usb. Though this didnt work even worse it also altered my grub table on the laptop disk. This meant that when I unplugged the usb grub died with an error device not found. Though i have now fixed this I was wondering if there is a way to make the usb disk a "stand alone boot disk"?

I maybe missing something obvious. Any input gratefully received.During the install of Lucid or Karmic you should be presented with a pop up window asking you where you wish to install grub2. The default selection won't work for you, so be sure that you select only the main partition of the usb drive. If you've already done a usb OS install you could use super grub to correct the grub2, or install grub2 to the usb HDD. You will then have a copy of grub2 on usb and the copy on your internal HDD will not be touched. You may not be able to access a windows install from the usb grub2, but they will be isolated.

---

### Post by varunendra on 2010-04-13
Create a fat32 partition (primary) on your usb HDD. Keep its size around 4.7-5 GB.

Now boot into Ubuntu 9.10, plug in your usb disk, let it get detected.
Insert your Ubuntu Live CD in the CD drive.

Goto system>administration>_create **usb startup disk**_. In the opened dialogue box- select the fat32 partition you just created as destination & Live CD as source. Also, select maximum size (4GB) for the file storing changes (it'd be a slider) and **GO !!**

Within a couple of minutes your USB drive would become bootable in Live Session mode, but with changes being persistent !!

Please note that selecting a wrong (non-fat32) partition, or not having a pre-formatted fat32 partition will erase all the partitions on the usb disk & hence all the data on it.

Except for this precaution, everything is quite cool & easy.

Tell me if you need any detailed description.

---

### Post by thebigob on 2010-04-13
> **Doctor Mike said:**
> During the install of Lucid or Karmic you should be presented with a pop up window asking you where you wish to install grub2. The default selection won't work for you, so be sure that you select only the main partition of the usb drive. If you've already done a usb OS install you could use super grub to correct the grub2, or install grub2 to the usb HDD. You will then have a copy of grub2 on usb and the copy on your internal HDD will not be touched. You may not be able to access a windows install from the usb grub2, but they will be isolated.

I think this is exactly what I am after however I will need to wait till I get home to give it a try. If you can remember of the top of your head how I can change the location of the grub install that would be great if not I will have a look tonight. Thanks for your help!

> **varunendra said:**
> Create a fat32 partition (primary) on your usb HDD. Keep its size around 4.7-5 GB.

Now boot into Ubuntu 9.10, plug in your usb disk, let it get detected.
Insert your Ubuntu Live CD in the CD drive.

Goto system>administration>_create **usb startup disk**_. In the opened dialogue box- select the fat32 partition you just created as destination & Live CD as source. Also, select maximum size (4GB) for the file storing changes (it'd be a slider) and **GO !!**

Within a couple of minutes your USB drive would become bootable in Live Session mode, but with changes being persistent !!

Please note that selecting a wrong (non-fat32) partition, or not having a pre-formatted fat32 partition will erase all the partitions on the usb disk & hence all the data on it.

Except for this precaution, everything is quite cool & easy.

Tell me if you need any detailed description.

I have given this a try already. Though it is so simple I do want to do a full install rather than run in live mode if that makes sense. Thanks for again for the reply!

---

### Post by varunendra on 2010-04-13
Hope I didn't sound stupid again ([see my post]("http://ubuntuforums.org/showthread.php?t=1451172")). By the way, I'm really quite happy with my setup of this kind.

Best of luck !):P

---

### Post by thebigob on 2010-04-13
> **varunendra said:**
> Hope I didn't sound stupid again ([see my post]("http://ubuntuforums.org/showthread.php?t=1451172")). By the way, I'm really quite happy with my setup of this kind.

Best of luck !):P

Not at all! Though this works well with ubuntu I was also looking to test out some other unix style systems that may not have the option of a live cd. I just realised that the set up of these will be different for each operating system though. DOH!!

---

### Post by Doctor Mike on 2010-04-13
> **thebigob said:**
> Not at all! Though this works well with ubuntu I was also looking to test out some other unix style systems that may not have the option of a live cd. I just realised that the set up of these will be different for each operating system though. DOH!!
If your not sure how the grub will be setup from any particular disto you can physically disconnect the internal drive while installing to usb. That's one way to make sure your copy of grub on the internal drive is not altered...

---

### Post by varunendra on 2010-04-13
> **Doctor Mike said:**
>  You may not be able to access a windows install from the usb grub2, but they will be isolated.

Hey Doc! Isn't it possible for him to install GRUB on usb drive the way u told, then simply edit the** /boot/grub/menu.lst** file to manually add an entry for his windows install? Just an imagination....

> **Doctor Mike said:**
> If your not sure how the grub will be setup from any particular disto you can physically disconnect the internal drive while installing to usb. That's one way to make sure your copy of grub on the internal drive is not altered...
  Good advice to follow....

---

### Post by thebigob on 2010-04-14
Thanks for the input on this guys. Really has helped. Disconnecting the internal hdd - genius! 

Marking this thread as solved. Thanks again for all the replys!

---

