---
title: "creating Ubuntu dual boot with Ubuntu on 2nd hdd no wubi"
date: 2011-07-27
forum: General Help
---

### Post by Trilogin on 2011-07-27
I just reinstalled Ubuntu from the LiveCD onto my second HDD because that was my intent originally, and I very much disliked having to choose my OS a second time before finally booting into Ubuntu. 
 
Is there any way for me to turn these separate installations (Win7 on my first HDD, Ubuntu on my second HDD) into a nice dual boot system without reinstalling Ubuntu or am I going to have to reinstall Ubuntu?
 
If I do have to reinstall Ubuntu, do I tell the partition manager to load the boot loaders from Ubuntu onto the Windows drive, or do I tell it to load them onto the 100MB windows system partition? I currently just put the entire installation onto my second HDD, and then lost my dual boot option. Now I have to switch first boot device in BIOS to switch between operating systems.

---

### Post by wildmanne39 on 2011-07-27
Hi, in ubuntu open a terminal and type
```
sudo update-grub
```
and see if that works, and no you do not want to install grub to your 100mb boot partition because then windows will not boot.

---

### Post by Trilogin on 2011-07-27
I just ran that command, then I restarted my PC. I went into BIOS and set the Win7 drive as firstboot and I got no dual boot option. I will try it again using the Ubuntu HDD as firstboot and see if that works.

---

### Post by wildmanne39 on 2011-07-27
Hi, ok let us know.

---

### Post by kumaranphoenix on 2011-07-27
While installing ubuntu from live cd, u should set a option( or whatever it is called) as '/'. This is done in the point wher u choose the partition i which ubuntu should be install. U also should set a swap space during this time. Did u do that?

---

### Post by Trilogin on 2011-07-27
Okay, so I changed the boot configuration and put the Ubuntu HDD as firstboot, and low and behold I get grub. When I choose Windows 7 loader, it loads Windows 7 immediately. Thanks guys! :)

What are these other grub options? They should be visible in the attachment if it loads.

---

### Post by wildmanne39 on 2011-07-27
Hi, your welcome! one is used for recovery if you can not boot ubuntu and the other one runs a memory test which takes a very long time to run.

---

