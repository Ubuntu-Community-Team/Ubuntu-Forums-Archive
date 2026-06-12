---
title: "Installing Linux on laptop, but Keep Windows 7 OEM Partition"
date: 2012-05-17
forum: General Help
---

### Post by morbid_bean on 2012-05-17
I am looking to install the latest Ubuntu on my Lenovo Ideapad S10-3 ( NETBOOK) , It currently is running windows 7 starter with a couple hidden partitions.


30GB partition with all drivers and software
186GB (C:\) With Windows 7 OS installed
14.75GB OEM Partition with my Restore image ( Hidden by default, but appears in the Disk Management )



I want to completely Trash The windows 7 OS and run 100% Ubuntu on the Large partition, however want to keep the 2 Lenovo portions.

Why? I want to keep this factory image in-case I ever want to restore Windows 7 Starter, and the fact that my Laptop is still under warranty..

My question IS, How can I back this up? Or, how can be become usable when I decide I want to restore windows 7??

---

### Post by wilee-nilee on 2012-05-18
Keeping which partitions? You actually have 4 partitions I'm quite sure a boot partition is there as well. YOu will see it with gparted from the live ubuntui cd.

If it was me I would just clone the whole thing the whole HD so it can just be slipped back in. 

 Partially removing partitions that are linked together to save the recovery image if I'm correct, is probably a little beyond us here as far as knowing exactly how lenovo has set it up.

You can do a one time full back up of the C partition to dvd's with a oem as well.

If it was me I would clone and get the oem install discs from lenovo, probably about $30 bucks then you have the same a image and a recovery in the discs if needed.

---

### Post by c2tarun on 2012-05-18
> **morbid_bean said:**
> I am looking to install the latest Ubuntu on my Lenovo Ideapad S10-3 ( NETBOOK) , It currently is running windows 7 starter with a couple hidden partitions.
 
 
30GB partition with all drivers and software
186GB (C:\) With Windows 7 OS installed
14.75GB OEM Partition with my Restore image ( Hidden by default, but appears in the Disk Management )
 
 
 
I want to completely Trash The windows 7 OS and run 100% Ubuntu on the Large partition, however want to keep the 2 Lenovo portions.

For this I would suggest do a full installation and give all the HDD to Ubuntu, or choose a particular partition click on Change button select type EXT4/3/2, select option to format the partition and Then select the mount point as '/'
BTW managing partition while installation is something which you shouldn't touch if you are trying to install for the first time. It takes some time to understand what and how this behaves
 
> 
 
Why? I want to keep this factory image in-case I ever want to restore Windows 7 Starter, and the fact that my Laptop is still under warranty..
 
My question IS, How can I back this up? Or, how can be become usable when I decide I want to restore windows 7??
If you ever want to restore windows back then try to make DVD of the factory image. I also did that but never used that disc till now.
About warranty I think only Software support warranty will be void. Hardware warranty will be intact. And I can guarantee that UbuntuForum can provide more support and help on Ubuntu then any company can provide on Windows :)

---

### Post by jadtech on 2012-05-18
actually  if  you have a a 45gb usb flash drive or a USBportable hard drive  you can even do it with like 7 DVD's you can make  copies of that image right from win7 and recovery cd I recomend portable Drive the image is about 25 to 45 gb depending on how much junk was load on the leveno :) 

then you can just wipe the whole drive and go ubuntu  putting linux on it dont hurt the  warranty at all  at least according to geek squad you can use what ever OS you  choose as long as you dont open  it internally and remove or install anything hardware ... 

you can do all types of search on google how to make the restore and recovery  there are thousands of  sites  giving detailed information its very simple ..

and if non of that actually works for you  you can call  and they should send you  the install disks  for nothing but maybe the cost of shipping ..

---

### Post by Mark Phelps on 2012-05-18
In my experience, the easiest way to do an image backup of Win7, such that you can restore it later, is to download and install the FREE version of Macrium Reflect in Windows.  Use that to make a backup of Windows.  Also use the option to create and burn a Linux Boot CD.  With these, you can later restore Win7 to your current condition.

---

