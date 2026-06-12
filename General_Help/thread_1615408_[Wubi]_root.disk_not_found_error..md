---
title: "[Wubi] root.disk not found error."
date: 2010-11-06
forum: General Help
---

### Post by cholic on 2010-11-06
I have two hard disks. 

Hard disk A has windows 7, and Hard disk B has Wubi installed.
Yesterday, I exchanged the cables going from motherboard to hard disks.
(which means, consider, there are 6 SATA-II ports on mainboard, if hard disk A was on the first slot, and disk B was on the second slot, I exchanged those. I had to do this because of some other reason)

Since I just exchanged the sata slots between two hard disks, everything worked out fine, (boot to window, files are still there)

But, wubi boot fails with a following error. (I can still choose between wubi and window on the startup)

ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell.

Thing is that I do still have 15GB root.disk file in a drive E: as well as every other file (all wubi related files are in E:).  and it seems that wubi does not able to find correct hard disk location.
(I am not sure whether the wubi installed drive ID was E: or D: or whatever.. I have many partitions..)

1. How can I resolve this problem??

2. Also, for the last thing to do, if I just backup the root.disk file, reinstall the wubi, and paste it over to a newly made root.disk file, will be able to get all the data backup? will it boot?


If i remember correctly, I think I have seen some information that I have to download a wubi config file to c:\(the main windows 7 drive) to get the wubi startup. It was not a big file if I remember it correctly. I currently have no file related to wubi in c:\ (the main windows 7 drive).

---

### Post by bcbc on 2010-11-06
Maybe /dev/sdb changed to /dev/sda... when you see the wubi menu press 'e' and change all references to (hd1,Y) and /dev/sdbY to (hd0,Y) and /dev/sdaY  
Then CTRL+X to boot.

It will be something that simple. Once it's up and running run
```
sudo update-grub
```

---

### Post by cholic on 2010-11-07
> **bcbc said:**
> Maybe /dev/sdb changed to /dev/sda... when you see the wubi menu press 'e' and change all references to (hd1,Y) and /dev/sdbY to (hd0,Y) and /dev/sdaY  
Then CTRL+X to boot.

It will be something that simple. Once it's up and running run
```
sudo update-grub
```

I didn't try that yet, but in the provided shelll, when I go into /host/ I see files that are in C:\. So some form of drive assignation is wrong I guess. Wubi is right now assigned to c:\, and I need to change it back to e:\ I think. Let me try your solution

---

### Post by cholic on 2010-11-07
> **bcbc said:**
> 
It will be something that simple. Once it's up and running run
```
sudo update-grub
```


Hey, it worked!!, I am now on ubuntu. I just have one more question. Is it save to do 'sudo update-grub' in wubi??? I have some bad experiences with wubi&grub

---

### Post by bcbc on 2010-11-07
> **cholic said:**
> Hey, it worked!!, I am now on ubuntu. I just have one more question. Is it save to do 'sudo update-grub' in wubi??? I have some bad experiences with wubi&grub

Yes it's safe. :)

The problems with grub have mostly had to do with updates to grub-pc (the package for grub2) where you get prompted to install it to a device e.g. /dev/sda ; but as long as you just don't install it to any devices it's fine. PS this only happens now to wubi installs on a partition different to windows (i.e. your case). But it doesn't happen running sudo update-grub.

The other issues have to do with upgrading from 10.04 to 10.04.1 and 10.04.1 to 10.10. Again it's the update of grub-pc and probably lupin-support. That won't happen by running update-grub.

By the way - since you have another drive, what is the reason you haven't gone for a full install of Ubuntu? It's generally more stable (although not immune to problems either).

---

### Post by cholic on 2010-11-07
> **bcbc said:**
> Yes it's safe. :)
By the way - since you have another drive, what is the reason you haven't gone for a full install of Ubuntu? It's generally more stable (although not immune to problems either).

Well, I thought its impossible to install windows and ubuntu in one computer, because window 7 will set the mbr back to original state. (thats what I heard.. I am new to linux..).
So, if I just download the ubuntu image to usb-flashdrive, and install it, what are the some of the important procedure to do??
Because if I search for 'ubuntu window install' online, the things that I see are tons of wubi..

---

### Post by bcbc on 2010-11-07
> **cholic said:**
> Well, I thought its impossible to install windows and ubuntu in one computer, because window 7 will set the mbr back to original state. (thats what I heard.. I am new to linux..).
So, if I just download the ubuntu image to usb-flashdrive, and install it, what are the some of the important procedure to do??
Because if I search for 'ubuntu window install' online, the things that I see are tons of wubi..

True, there are some windows applications that will damage grub in the drive MBR. Also, if you install/repair windows following the ubuntu install it will replace the MBR. But it's fairly easy to repair the MBR.

Also, if you have two drives you may be able to select which drive to boot from - then just keep windows's MBR on the windows drive, and grub on the Ubuntu drive.

But anyway - there's no rush to get off wubi. It gets a bit of a beating on the forums from the regular users, but I think it works OK. Especially if you avoid grub-pc/grub-common updates and upgrades you should be fine. Then when you feel more comfortable go for a [migration]("http://ubuntuforums.org/showthread.php?t=1519354") or reinstall.

---

