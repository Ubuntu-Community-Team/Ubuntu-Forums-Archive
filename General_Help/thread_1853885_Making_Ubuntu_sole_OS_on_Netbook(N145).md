---
title: "Making Ubuntu sole OS on Netbook(N145)"
date: 2011-10-03
forum: General Help
---

### Post by Oregand on 2011-10-03
Hey guys,

Xbuntu beginner here so be gentle with me, also for the record yes I am a complete idiot. Now that thats out of the way lets get down to the nitty grttiy.

I installed xbuntu on my netbook as of yesterday via the wubi partion.

Now I have my little machine duel booting Windows starter and xbuntu(grub menu). 

I want to delete my windows partition altogether and install Ubuntu/Xbuntu as my main OS on my netbook(Samsung N145 PLus).

I have am some serious problems trying to do this thought so if anyone could help me out I would be very thankful.

So heres what Ive tried so far,

I downloaded Gparted and was going to delete the nfts partitions and resize linux BUT my dev/sda2(nfts) is locked and when I try to unmount it I get the error (Monuted on host, device is busy).

So after failing to figure the partition side out I thought a fresh install from a bootable usb was the way to go but every time I tried I get the error message that my dev/sda drive cannot be unmounted.

Can anyone tell me how to unmount this locked drive and then proceed to delete the windows partition and make ubuntu my sole OS on my netbook?

Thanking yall in advance

David

---

### Post by Mark Phelps on 2011-10-03
You can't make changes to a partition that's in use -- and when you're running Ubuntu on your netbook, the partition containing it is in use.

You will need to boot from a USB stick or drive containing GParted and make the changes from there.  You can get the GParted ISO image from distrowatch.com.

---

### Post by mörgæs on 2011-10-03
If everything else fails you can completely wipe the hard drive using [www.killdisk.com](www.killdisk.com)

---

### Post by ajgreeny on 2011-10-03
Why not run xubuntu to download the xubuntu .iso file, if you haven't already got it, and burn/copy that image to a usb flash drive using the startup-disk-creator.  You can then boot to that usb flash disk and use it to install xubuntu on the whole disk.

I recommend that you choose "Something Else" at the disk preparation stage and set partitions manually, using a separate /home partition, which makes life so much easier when you want or need to reinstall the OS.
[Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome")

---

### Post by mike555 on 2011-10-03
If you installed Ubuntu using wubi, Ubuntu is inside Windows, if you delete Windows you will be deleting Ubuntu also.......... so backup your stuff (important documents, bookmarks, email, etc.) to an external media, then just install Ubuntu or Xubuntu to the whole hard drive using a cd or usb .......

---

### Post by t0p on 2011-10-03
Another important step is to check that the boot order is usb device *before* hard drive.

---

### Post by Oregand on 2011-10-03
Ok so what Ive established is this,

Since I installed Xbuntu using windows I cant delete the windows partition without taking Xbuntu with it.

I have tried installing the iso onto a usb, make that a bootable device and then tried to clean install ubtuntu.

The problem was when I got to the install screen I was throw back to the original screen were you select the install option and underneath I got the message:

Error, dev/sda cannot be mounted.

After this im kinda at a loss because if I cant just clean install Ububtu from a USB I have no idea how to make it the sole OS.

ANy tips?

---

### Post by mike555 on 2011-10-03
So you made a bootable usb drive and booted your computer to it, you should open gparted and delete all partitions ,then you should have only one partition, now click on that one partition and resize ,so you have a small 2GB partition for swap and the rest for (X)ubuntu.......format the big partition ext4 and format the small one for swap file ........ then close gparted and install ...


this is assuming the hard drive shows in gparted , if not you might need to fix errors on hard drive first .

---

### Post by eganopen on 2011-10-06
I assure everyone I'm biggest idiot.  
 
I joind to accomplish the same thing on my old ibm t41 laptop.  Also used wubi to install but have a wrinkle where all my removable drives broke; no cd usb.  
 
My inclination was to double install ubuntu on a 3rd partition and delete then.  
 
I tried to unlock my c drive through win and ubuntu gparted w/o luck.  
I magine there must be someway, I hate to have win taking up space.

---

### Post by wildmanne39 on 2011-10-06
Hi, if ubuntu is still there you can use this link to migrate your wubi install to a normal install.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
Thank you

---

