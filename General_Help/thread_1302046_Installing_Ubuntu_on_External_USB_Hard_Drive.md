---
title: "Installing Ubuntu on External USB Hard Drive"
date: 2009-10-26
forum: General Help
---

### Post by jet123 on 2009-10-26
Hi:
I am new to Ubuntu and this forum. 
I am trying to install ubuntu on an external USB hard drive. I've created an ISO Ubuntu installation disk. Before booting to CD ISO, I've shut the internal drive off via the BIOS. When I boot to CD a screen appears where one of the choices is install Ubuntu. When I choose that the screen freezes. What am I missing? Thanks in advance. BTW, I can set my computer to boot from USB device.

---

### Post by undecim on 2009-10-26
Do you hear the CD drive spinning?

Also, try the option from that menu to check the disk for defects

---

### Post by meinvateristnein on 2009-10-26
i have done this many times ... ok the problem is not the disc it is the External even know you are booting from it there is no actual memory to save the boot data to ..... all you have to do is DO NOT turn off the internal ... run LIVE CD then select install then when the menu comes up that allows you to choose your device you select your External (probably) Hda2 ........ BTW never use discs they can get easily stratched and easily corrupted with ubuntu IDK y... i recommend highly UNETBOOTIN it automaticly does everything for you then you just plug in your USB drive then boot up as if it were a live cd HOPE I HELPED

---

### Post by jet123 on 2009-10-28
Thanks for all replies.
 
> **meinvateristnein said:**
> i have done this many times ... ok the problem is not the disc it is the External even know you are booting from it there is no actual memory to save the boot data to ..... all you have to do is DO NOT turn off the internal ... run LIVE CD then select install then when the menu comes up that allows you to choose your device you select your External (probably) Hda2 ........ BTW never use discs they can get easily stratched and easily corrupted with ubuntu IDK y... i recommend highly UNETBOOTIN it automaticly does everything for you then you just plug in your USB drive then boot up as if it were a live cd HOPE I HELPED
 
Thanks. I'll try this.

---

### Post by tsucol11 on 2009-10-28
I have been running Ubuntu on an external HD for over a year. During this time I did several installs testing various versions.

Like meinvateristnein said do not disable your internal drives.

-here I am assuming that your MB will permit you to boot from any storage device (with ASUS MB's use the F8 key while booting).

- boot from the ubuntu CD
- choose install
- after a few questions the partition editor will come up. Look at your hard drives carefully & choose the external (in my case it was SDD (sata HD's).

Carefully read [COLOR="Red"]ALL[/COLOR] info in the partition editor screens, resize the boot partition to about 8 gigs, swap to about 2 gigs & home to whatever size you need. In my case I did not want grub installed on the first hard drive. Partition editor (Gparted?) will permit you to install grub on your external without affecting your main HD.

Works great at my end. When booting I press F8, chose the external drive, grub starts & the rest is history. If I want to run windows I let the computer boot without pressing F8 & window boots up automatically.

Brian

---

### Post by hoarenet on 2009-10-29
Hi Everyone. I just joined today 29/10/09

I am running Ubuntu 9.10RC from a 16gb Sandisk USB stick. I had to read  many forum posts before finally managing to get it all to work but I have a few questions about utilising the rest of the USB disk space.

What I found originally was that the "USB Startup disk creator" in ubuntu 9.10 was formatting the USB to FAT32 but when trying to boot it  doesn't seem to work. So I formatted it to FAT16 and used UNetbootin to install the linux files. That is how I got it to work.

At present the USB has a 2gb (FAT16) boot partition and a 14gb (FAT32) spare partition.

That setup is ok for running but wont allow me to install more software because of the 2gb size limitation of the installed OS.

What I want is for linux to install its bootup files on the boot partition but load all the linux software onto the 14gb partition so that I can make better use of the USB size.

I would appreciate any help.

Thanks.

---

### Post by hoarenet on 2009-10-29
> **hoarenet said:**
> Hi Everyone. I just joined today 29/10/09

I am running Ubuntu 9.10RC from a 16gb Sandisk USB stick. I had to read  many forum posts before finally managing to get it all to work but I have a few questions about utilising the rest of the USB disk space.

What I found originally was that the "USB Startup disk creator" in ubuntu 9.10 was formatting the USB to FAT32 but when trying to boot it  doesn't seem to work. So I formatted it to FAT16 and used UNetbootin to install the linux files. That is how I got it to work.

At present the USB has a 2gb (FAT16) boot partition and a 14gb (FAT32) spare partition.

That setup is ok for running but wont allow me to install more software because of the 2gb size limitation of the installed OS.

What I want is for linux to install its bootup files on the boot partition but load all the linux software onto the 14gb partition so that I can make better use of the USB size.

I would appreciate any help.

Thanks.

I have now resolved this by reading this. Sorry if it has been mentioned here before.

[http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

Anyway its all working and I'm downloading the latest updates to my nice 16gb drive.

Thanks anyway

---

### Post by hoarenet on 2009-10-30
I thought I had it working and would have full use of the entire drive but then I tried downloading software and hit a problem. The message that appeared was that I only had 1mb of space left and the software download was aborted.

I tried to use ubuntu's disk tools to see what space I had available on ALL drives on the computer and none of them was showing that I was anyway near using up the available space. I wondered if somehow linux had created some sort of partition on my hard drive that wasn't big enough. However there was no evidence of any new partitions and my PC's disk activity light wasn't showing any activity as you would expect when using the USB stick only.

My own assumption about what happened is that the original setup of my USB stick didn't go as I had expected and somehow had limited the size of the boot partition to around 2gb but isnt visible to the ubuntu disk tool. This particular USB stick came from SANDISK and originally contained the U3 software. I didn't use the SANDISK U3 removal tool but simply formatted it from windows to remove the U3 software. Maybe that was the problem.

---

