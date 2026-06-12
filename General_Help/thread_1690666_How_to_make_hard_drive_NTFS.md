---
title: "How to make hard drive NTFS?"
date: 2011-02-18
forum: General Help
---

### Post by Uthallan on 2011-02-18
Hello,

I am attempting to put vista onto my laptop from a Full install of Ubuntu 10.10, but when I boot from my vista CD and attempt the instalation it says I have to have my drive formated to NTFS, I have tried to google how to get this done. I have tried to go to System>Administration>Disk Utility and then edit the type of the partition but there are like 20 options and none of which are just NTFS. what should I do?

---

### Post by TeoBigusGeekus on 2011-02-18
```
gksu gparted
```
to start gnome-partition-editor.

---

### Post by Uthallan on 2011-02-18
I tried to use Gparted but it wont let me edit the format of anything, the "Format To" option is just greyed out.

---

### Post by TeoBigusGeekus on 2011-02-18
You have to unmount the partition first.

---

### Post by Uthallan on 2011-02-18
The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.


I got this

---

### Post by TeoBigusGeekus on 2011-02-18
I think I understand.
You're trying to shrink your linux partition(s) in order to make room for vista.
This has to be done from a live cd/usb, as the partitions have to be unmounted.
Bear in mind that after installing vista you'll lose grub. 
[Here's]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html") a guide on how to recover it.

---

### Post by Uthallan on 2011-02-18
So If I understand you correctly I should use the CD I used to install Ubuntu to do the partitioning and then proceed to install vista and re-install GRUB? if this is the case do I just go to the "try ubuntu without installing" option and use that interface to get the partitioning done, or is there another way that I don;t know of.

---

### Post by TeoBigusGeekus on 2011-02-18
> **Uthallan said:**
> do I just go to the "try ubuntu without installing" option and use that interface to get the partitioning done
Yeap...

---

### Post by Uthallan on 2011-02-18
I'll do that, and thank you very much for you fast responses I really appreciate it!

---

### Post by TeoBigusGeekus on 2011-02-18
Anytime...
Post back with your progress and any further question you have.

---

### Post by Uthallan on 2011-02-18
well I tried to boot from my CD, and with two different drives, but it doesn't allow me to do anything. It just boots as if i'm booting normally and brings me to my desktop.

---

### Post by TeoBigusGeekus on 2011-02-18
Go into BIOS and select cd as the first boot device.

---

### Post by Uthallan on 2011-02-18
I did that, still the same result

---

### Post by oldfred on 2011-02-18
Your NTFS partition has to be a primary partition with the boot flag. You set boot flag in gparted when you create partition.

Windows only installs to NTFS partitions with boot flag or empty drives.

---

### Post by TeoBigusGeekus on 2011-02-18
Oh wait...
I think you have to hit the shift button when an icon flashes briefly at the bottom of the screen during startup (or something like this :P).

---

### Post by Uthallan on 2011-02-18
I'll give the shift thing a shot an see what happens

---

### Post by Uthallan on 2011-02-18
well nothing happened with shift, I tried both drives again with pressing **** at many different point of the startup but nothing happened. Holding shift just brings me to the GRUB menu where I can choose to boot regularly or in safe mode, at least I think thats what it was saying

---

### Post by TeoBigusGeekus on 2011-02-18
Are you sure the cd is ok?

---

### Post by Uthallan on 2011-02-18
yeah I used it to install just yesterday, and it hasn't been anywhere but a padded CD case so there are no scratches or anything.

---

### Post by TeoBigusGeekus on 2011-02-18
> **Uthallan said:**
> yeah I used it to install just yesterday, and it hasn't been anywhere but a padded CD case so there are no scratches or anything.

Can't be...
Please double check the BIOS settings.

---

### Post by Uthallan on 2011-02-18
alright, ill go recheck just to be sure.

---

### Post by Uthallan on 2011-02-18
yep, my drive is set as my first boot device, I also tried the shift thing again but all I got was a regular boot as if there wasn't even a CD there.

---

### Post by TeoBigusGeekus on 2011-02-18
I don't know what to say...
This has evolved into a can't boot from cd issue...
Sorry for my inadequacy.
Someone else?

---

### Post by Uthallan on 2011-02-18
Hmm, well you were a great help up until this point, and I thank you for that. I suppose i'll check out google and see what I can do there, thanks.

---

### Post by Uthallan on 2011-02-18
Well I wasn't able to google anything of use, so if anyone wants to jump in here that would be great!

  In summation all I need now is to be able to boot from my live CD, but for some reason when I try to do so nothing but a normal boot takes place and I am brought to my desktop as normal. My drive is propberly set as my boot device in BIOS, but that doesn't seem to fix anything.

---

### Post by williamts99 on 2011-02-18
> **Uthallan said:**
> My drive is propberly set as my boot device in BIOS, but that doesn't seem to fix anything.

[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

Read the manual from the manufacturer of your computer/motherboard, it will let you know.  Ensure that your CD-rom drive(s) are set as the first boot device, and check for other settings for something to enable 'external boot'.

Just because it booted from the CD before does not mean that it was set as the first boot device.  It will do that even if the CD drive is listed after the hard drive, provided that the hard drive is blank, or something is wrong with the os on the hard drive.

Either way, the best resource is the manual for your computer/motherboard.

---

