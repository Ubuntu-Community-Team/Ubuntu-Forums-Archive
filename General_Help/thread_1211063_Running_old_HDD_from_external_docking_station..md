---
title: "Running old HDD from external docking station."
date: 2009-07-12
forum: General Help
---

### Post by Polomint01 on 2009-07-12
I am having some trouble with my hdd , I am trying to get it to run from a HDD docking station via one of my USB ports.

The HDD has Ubuntu 8.10 on it , and boots no problem when connected internally.

It is set as my hdd 0,0 position in boot order.

I can get it to recognize the external l drive, but I get a GRUB 13 error.

I think I need to edit the grub menu to let it know that the drive is now external via the USB, but what do I use.

The main reason I want to get this to work, is my HDD keeps crashes after in loads up Ubuntu when connected internal, and the CPU fan spins very fast, and states that its over clocking.

I thought when the fan was spinning fast it was a heating problem, so installed another fan, which helped for awhile,but it seems my pc is having problems with my HDD,

I thought my HDD had died on me, however when I use it via the external docking station, and using my laptop (running linux) I can assess the contents of the drive (which I now luckily have backed up).

Sorry for the convoluted question, I am sure I will have to reinstall :-(

The HDD is a Seagate Barracuda 7200.11 500GB drive. 


Any ideas welcome.

---

### Post by blueridgedog on 2009-07-12
Are you trying to boot off of the drive?

If you are trying to boot off of the external drive, you will need to edit your grub menu on the hard drive and re-install grub to the mbr as the drive's location in Linux (/dev/sdX) and grub (hdX) has changed.  

Do you have an internal drive in addition to the external one?

Can you post the output of:

```
sudo fdisk -l
```

and

```
mount
```

and 
```

sudo grub
find /boot/grub/stage1
```

(you can exit the grub shell with quit)

---

### Post by Polomint01 on 2009-07-12
Yes, i am trying to boot off the external drive.

I do have an internal drive, however its got XP on, using it right now.

If I need to edit the grub menu, I can to that by connecting the drive to my laptop which is running Crunchee.

But, reinstalling GRUB,not sure.

---

### Post by blueridgedog on 2009-07-12
If you post the output of the suggested commands, I and others should be able to talk you through booting from the drive (assuming your motherboard's bios can boot from an external drive).

---

