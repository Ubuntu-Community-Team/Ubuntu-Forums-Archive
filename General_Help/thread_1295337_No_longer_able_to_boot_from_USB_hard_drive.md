---
title: "No longer able to boot from USB hard drive"
date: 2009-10-19
forum: General Help
---

### Post by Swirlster on 2009-10-19
Hi,

Recently I decided to change my main personal OS from Windows Vista to Ubuntu 9.04. I needed to keep windows to use windows based software for work so decided to install on a spare 40 Gb USB hard drive. Actually the drive from a previous laptop in a caddy. I completely formatted the drive and removed all the old partitions and changed the file system to ext3 then installed linux to it from a live cd. It wasn't quite that smooth as I managed to overwrite the MBR on the internal hard drive the first time I installed it but fixed that using a vista recover cd.

Eventually I had a laptop that could boot into vista from the internal hard drive or ubuntu from the USB drive. However, today I've not been able to boot ubuntu from the USB drive and when I go into the boot menu on startup there is no option to boot from the USB drive. Vista still runs fine, hence I can post this.

Interestingly, even though I changed the bios boot order to boot from bootable USB drives before booting from the internal drive it always booted into windows unless I went into the boot menu and told it to boot from USB.

I've tried reinstalling to the USB drive from the live cd and although the install seems successful it still won't boot.

Any ideas as to a solution?

---

### Post by sgosnell on 2009-10-19
The Vista fix probably removed grub.  There are several threads on the forum which discuss reinstalling grub, with detailed instructions.

---

### Post by Swirlster on 2009-10-19
Where should I have grub installed? It's definitely seems to be on the USB disk with the rest of linux and I've followed the instructions on [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) to make sure it was there. 

Also ubuntu would boot after I fixed the Vista problems through choosing to boot from USB in the boot menu at startup. It's since then the USB option has disappeared.

Also I'd like to make it clear I'm not very good at this stuff.

---

### Post by Giblet5 on 2009-10-19
> **Swirlster said:**
> Where should I have grub installed? It's definitely seems to be on the USB disk with the rest of linux and I've followed the instructions on [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) to make sure it was there. 

Also ubuntu would boot after I fixed the Vista problems through choosing to boot from USB in the boot menu at startup. It's since then the USB option has disappeared.

Also I'd like to make it clear I'm not very good at this stuff.

It sounds like the bootable stick image is wrong in some way.

When your laptop is POSTing, it will read the first block of the stick to see if there is either an active partition to jump to, or a MBR.

So, how did you create the bootable stick?

That's the key, cuz your laptop's BIOS doesn't think that stick is bootable.

Karmic has a tool to create a bootable stick and, despite some incredibly flaky UI behavior, it works after a try or seven.

---

### Post by Swirlster on 2009-10-19
> **Giblet5 said:**
> 
So, how did you create the bootable stick?

That's the key, cuz your laptop's BIOS doesn't think that stick is bootable.

Karmic has a tool to create a bootable stick and, despite some incredibly flaky UI behavior, it works after a try or seven.

It's not a stick, it's a disc, the version that worked with windows I made by installing ubuntu 9.04 to the drive making sure the boot sector was installed there too. By this point I'd taken out the internal hard disk to make sure I didn't naff up windows again.

---

### Post by Giblet5 on 2009-10-19
> **Swirlster said:**
> It's not a stick, it's a disc, the version that worked with windows I made by installing ubuntu 9.04 to the drive making sure the boot sector was installed there too. By this point I'd taken out the internal hard disk to make sure I didn't naff up windows again.

It'll be treated as a stick by BIOS and that's where it isn't working.

Is the Ubuntu partition active? Where is the boot loader installed? MBR or partition? Did you install Grub? Did you do that booted from that disk or from a Live CD?

---

### Post by Swirlster on 2009-10-19
> **Giblet5 said:**
> It'll be treated as a stick by BIOS and that's where it isn't working.

Is the Ubuntu partition active? 

Not quite sure what you mean, I can access it as a disc in ubuntu

> Where is the boot loader installed? MBR or partition? 
partition

> Did you install Grub? Did you do that booted from that disk or from a Live CD?Yes, from a Live CD.


EDIT:

I've just tried booting from the USB stick on a borrowed laptop and it booted straight away. I don't really know what this means but I guess it highlights there may be something wrong in the BIOS on my laptop.

---

### Post by sgosnell on 2009-10-20
Is the BIOS set to use the USB drive as the first boot device?  If not, it won't even look there, it will just boot directly from whatever is set as the first boot device, presumably the HDD/SSD.

---

### Post by Swirlster on 2009-10-26
Oddness, I've just booted my laptop from the drive but I had to do this: 
 
Plug in another USB hard drive, with no bootable sector. 
Go into the boot menu. 
Unplug that drive and plug in the one with Linux 
Select boot from USB device 
 
So I've got a work around but it still doesn't explain why I can't boot straight from the Linux drive or why it doesn't appear in the boot menu of its own accord.

---

### Post by sgosnell on 2009-10-26
Apparently your BIOS isn't recognizing the drive as a drive.  I'm not sure what to suggest here, other than reflashing the BIOS, and that's not something to be done without forethought.

---

