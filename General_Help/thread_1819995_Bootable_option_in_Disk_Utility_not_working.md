---
title: "Bootable option in Disk Utility not working"
date: 2011-08-07
forum: General Help
---

### Post by DemiImp on 2011-08-07
Maybe it's because I'm doing something "stupid", but I can't seem to get the bootable option to work.

I'm doing something a bit out of the ordinary, I know, but this is what I'm doing:

I've recently bought a 8 gb usb stick so I could install Ubuntu on it.  After finding out that there's (still) no easy way to do this directly (other than a live version), I kept searching until I found this [http://mintarticles.com/read/operating-systems-articles/how-to-install-portable-linux-ubuntu-on-a-bootable-usb-flash-drive-from-sun-virtualbox,13641/](http://mintarticles.com/read/operating-systems-articles/how-to-install-portable-linux-ubuntu-on-a-bootable-usb-flash-drive-from-sun-virtualbox,13641/) (which is suggested by Ubuntu)

I didn't follow it exactly, but I did install Ubuntu 11.04 directly onto the usb using the normal installer (after fumbling around with the error messages, I eventually created one partition ext4 of 7 gigs and one fat32 of 1 gig).  Linux was installed on the ext4, of course, and the swap space was the 1 gig fat32.

So of course, following the instructions, I opened up the Disk Utility (using the live cd) and eventually found the bootable option, clicked it, hit apply..... and nothing happened.  A little symbol in the partition made it look like something was happening, so I kept waiting.  Eventually it failed.

Further investigation led me to find out that the program that was launched by clicking apply just soaked up memory slowly until it ran out and then crashed.


So, am I doing something seriously wrong?

Is there a better way to make a bootable linux on a usb that acts exactly like a normal installation? (completely modifiable and such)

---

### Post by ottosykora on 2011-08-07
well depends on many things, but few things are wrong from begining.

Make more then one partition on a usb flash drive:
yes one can make it, but it is not supposed to be done as the controllers inside the usb stick may produce unpredictable behaviour when two standard partitions are found.

Second: why use fat32 as swap? Swap partition should have the format 'swap' which is kind of linux native for that purpose. But in fact swap partition is not so essential, if not present, swap file will be created instead

next is , you probably managed to make the partition bootable with setting the boot flag to it. But did you make some kind of MBR on the flash drive first? I mean before you created partitions etc?
Boot partition alone has no meaning if there is no master boot record on that drive. 

Where did you store the grub exactly? How do you intend to start the ubuntu at the end?

---

### Post by ottosykora on 2011-08-07
BTW:

the link to this instruction about virtual box etc I have read, but sorry it makes no sense there at all. What ever is written there is either missing half of the initial content or otherwise is simply some nonsense. 
Someone tries to install operating system into virtual box and is preparing lot of strange partitioning for it. 
in this case all is stored inside a file as virtual drive of virtual box. So has nothing to do with real installation.

---

### Post by DemiImp on 2011-08-07
Actually, you're right.  It was a "swap" partition.  But I believe it was also being registered as fat32 (maybe I'm wrong about the fat32 part).

So, if I understand correctly... I need to make at least 2 partitions.  A MBR partition and a Linux partition (and potentially a swap partition).

I was following different instructions to make an MBR, but honestly I don't really understand what the MBR specifically does.  Does it point to a specific Linux partition or is it just a general scan of the other partitions for OS's and then points the user to which ones can boot?

I guess that question isn't as important as "How do I set up a valid MBR on the stick?"

Before I gave up last night, I was following instructions that put Grub4Dos onto a partition of just above 200 megs.  (Then further instructions told me to copy the casper folder of the live ubuntu cd onto that partition, but I didn't have enough space) ... but honestly I didn't understand what I was accomplishing, I was just following instructions.  I believe what was going on was that I was manually creating a boot sector for a usb drive for the Linux install cd.  Where I could have stopped following the instructions and had a perfectly bootable Linux usb drive, I do not know.  (I was following this: [https://help.ubuntu.com/community/Installation/FromUSBStick#Create Bootable USB Manually](https://help.ubuntu.com/community/Installation/FromUSBStick#Create Bootable USB Manually) )

Also, thanks for the quick response :)

> **ottosykora said:**
> well depends on many things, but few things are wrong from begining.

Make more then one partition on a usb flash drive:
yes one can make it, but it is not supposed to be done as the controllers inside the usb stick may produce unpredictable behaviour when two standard partitions are found.

Second: why use fat32 as swap? Swap partition should have the format 'swap' which is kind of linux native for that purpose. But in fact swap partition is not so essential, if not present, swap file will be created instead

next is , you probably managed to make the partition bootable with setting the boot flag to it. But did you make some kind of MBR on the flash drive first? I mean before you created partitions etc?
Boot partition alone has no meaning if there is no master boot record on that drive. 

Where did you store the grub exactly? How do you intend to start the ubuntu at the end?

---

### Post by ottosykora on 2011-08-08
I am not 100% sure what do you want accomplish at the end.

I mean, ubuntu will just work from usb stick in life mode without any of your complex partitioning. 
If you go to: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
you will find all the instruction there.

Partitioning of flash stick is possible but not always it works well. For basic real ubuntu installation you need one partition on the stick, but you can have more, e.g for /home. Swap on usb stick is probably no real advantage, as write on stick is very, very slow and therefore of no practical use.

MBR does not have any own partition, it is simply code at the beginning of the drive. As many usb sticks are sold without any mbr (master boot record) on it, one has to do it sometimes. First small part of the grub boot loader will be stored there then.

let us know what exactly are you trying to do and someone may give you exact instruction for that.

---

### Post by ottosykora on 2011-08-08
When I have some new usb stick, I first make sure it is formated in a way to be able to have an mbr.
For that I use mostly the famous, but win only, tool from HP:
[http://www.chip.de/downloads/HP-USB-Disk-Storage-Format-Tool_23418669.html](http://www.chip.de/downloads/HP-USB-Disk-Storage-Format-Tool_23418669.html)

then there are numerous ways, one is for example to use unetbootin to create some stick compatible boot os from a CD or so.

You could I suppose use the original installer on the ubuntu CD, but then select not alongside or something like that, but 'other' or better say manual install.
From there you can point the installer to your usb stick whic will be some sdb.. probably and also make sure you select a place where to install the grub. This has to go into the same drive as root! and not to the mbr of the main drive of the computer!!!!!!! 
If you do not do this correct, your computer will run only when the stick is inserted from then. So be careful.

But running ubuntu from any average usb stick seems to me not very practical , as this will be dead sloooooow.
You can not compare it to live system operation, as this is taking long time to start, but then it runs in a dedicated ram-drive so it is rather speedy. 
I can not see any practical use of running ubuntu of some current version directly from an usb flash media other then kind of prove of concept.

---

### Post by dcstar on 2011-08-10
> **DemiImp said:**
> 
.........
Is there a better way to make a bootable linux on a usb that acts exactly like a normal installation? (completely modifiable and such)

You mean like using the USB Creator and selecting the "Persistence" feature?

---

