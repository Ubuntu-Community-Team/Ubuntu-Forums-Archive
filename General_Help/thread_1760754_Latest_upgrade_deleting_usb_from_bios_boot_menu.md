---
title: "Latest upgrade deleting usb from bios boot menu"
date: 2011-05-17
forum: General Help
---

### Post by dougalkerr on 2011-05-17
I ran a partial upgrade as suggested by update manager and now I have no bios boot menu entry for USB device.

Any ideas folks?

I corrected it the long way round (using Windows as no option from Dell to supply Linux bios file). I had to temorarily install Windows (ohhhh, bother...) and run the BIOS flash file from there and then I reinstalled Linux. I was not happy with the way I had partitioned the drive so I rebooted to start again only to find that the BIOS boot menu entry for USB had gone again.
Heavens above... what is going on?
I have no idea other than there must be a bios upgrade somewhere in the Ubuntu upgrades that is doing this - yes?

Any help appreciated as always. Thanks.

---

### Post by sj1410 on 2011-05-17
i dont believe this. theres no update that can change your bios. Recheck it, theres something else wrong.

---

### Post by pricetech on 2011-05-17
Agreed.  You have a problem with the BIOS itself, or you're just missing / misinterpreting something.

Wipe the drive completely since you plan a reinstall anyway and boot it a few times to get familiar with all the "hardware" menus, then attempt an install.

---

### Post by dougalkerr on 2011-05-17
Thanks for the input guys. I am familiar with the ins and outs of the BIOS and hardware. It gets stranger though, I had a go at changing the USB settings and changing them back again in the BIOS but, although the BIOS was showing USB in the Boot section it still does not appear in the Boot menu at start time. So I rebooted a couple of times and then decided to swap the USB key to another USB port and hey presto the system is happily booting from that USB port. I didn't get a chance to check if it appeared in the Boot menu though. I will have a look again when my system has finished reinstalling and let you know.
Looks like I have a problem with one of the USB ports.
This might explain why I can't get a USB 3.0 Express card to work at speed even though it does transfer but, only at USB 2.0 speeds.
Mmmm...

---

