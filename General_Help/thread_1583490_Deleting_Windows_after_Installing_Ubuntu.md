---
title: "Deleting Windows after Installing Ubuntu"
date: 2010-09-27
forum: General Help
---

### Post by Killer_Distro on 2010-09-27
I didn't know how to Make a cd image out of the Ubuntu iso so I made a seperate partition in my drive.
Now I'm wondering how to delete the windows partition without formating the whole hard drive.

Or someone could tell me how to create a bootable cd image

Thanks:)

---

### Post by Tibuda on 2010-09-27
> **Killer_Distro said:**
> 
Or someone could tell me how to create a bootable cd image

Thanks:)
How have you installed Ubuntu?

If you are using Windows, you can burn the ISO using [ImgBurn](http://www.imgburn.com/). If you are on Linux, you can use Brasero or K3B.

---

### Post by Ordes on 2010-09-28
1 mhm.. so u actually didnt install ubuntu yet? and just copied the files on a seperate partition?
2 or is your ubuntu already installed & running?

if 1, than follow the post above; burn the image; load ubu-live from the cd and install; if you are sure you dont want the windows anymore you can format your disc during the installation process; or keep windows first and delete it later; but you will need to install ubuntu

if 2: load up your ubuntu
> you can use brasero to burn a bootable cd from a iso (in sound& video)
> if u have a usb and your pc can boot from usb, than you can also use the "startup disc creator in ubuntu" (in system > admin);

> deleting:
> you can use gparted to delete/ create/ merge partitions; download from synaptic or boot up ubu-live from cd/ usb

>if you make bigger changes to the partitions; e.g merging with ubuntu, changes to ubuntu /root; /home; etc; you should always use gparted from the live-ubuntu, instead of your running system; 

> pay attention if you are changing the partition tree, sda1, sda2; in this case u might need to reconfig grub (bootloader), fstab (mounting of /; /home; etc)

---

