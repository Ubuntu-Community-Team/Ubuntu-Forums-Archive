---
title: "Problem getting USB HDD to boot GRUB"
date: 2010-01-16
forum: General Help
---

### Post by chrols on 2010-01-16
I have this (fairly recent) laptop I want to boot from an external USB HDD as it has no internal drive. The problem however is that once Ubuntu (or other distributions I've tried) are installed I get "Operating System not found" rather than GRUB when I reboot. If I stick the USB HDD into another computer and choose to boot from it GRUB shows up and there is no problem. 

The strange thing is that if I use a live USB creator on the USB HDD, the laptop has no problem booting from the USB HDD. However I would prefer to use a straight installation of Ubuntu rather a live USB edition.

I tried to install GRUB manually, configure it in a number of ways, different partition schemes, use an USB key instead of an USB HDD etc, etc. Also I fail to find anything resembling my situation on the net. 

I guess there must be some hardware limitation since other computers can boot from the USB HDD flawlessly in the standard case, but since a live USB edition of Ubuntu can be booted of the USB HDD the hardware clearly isn't incapable of USB booting. I suppose the next step would probably be to try and use SYSLINUX which the live editions seems to use instead of GRUB. 

If anyone know how to make GRUB work or why it doesn't work while the live editions work I would be very grateful for the input

---

### Post by john newbuntu on 2010-01-16
Do you think this is a BIOS related problem where the lookup order is USB first.  The external hard drive is probably not in this list or is disabled?  If you have not already checked this, please go into your BIOS and confirm this.

---

### Post by efflandt on 2010-01-16
Assuming you have grub in the mbr of the USB drive, some systems still have trouble booting from a USB hard drive, maybe because it is not up to speed when a fast computer boots.

For example with a new Dell 1545 laptop I was setting up for someone, even when I had USB before hard drive in boot order in BIOS and hit the key to select which device to boot from and selected USB, it still booted Win7 on the hard drive.  But if I went into CMOS setup, saw that USB was still before hard drive, and then it would boot USB.  Or maybe I only had to go through that if I had booted without the USB drive and then reconnected it and tried to boot from it.  I think it may have recognized the USB drive and could repeatedly boot from it if I was regularly booting from it without disconnecting it.  But I no longer have that laptop to test.

---

### Post by bsh on 2010-01-16
"it has no internal drive" :shock:

i am not sure if i understand your problem clearly, (i am also afraid of you tried all kinds of random things already and you already have a big chaos on your drive(s) :) ), but i had this experienced a few times, it may be also useful for you: installed ubuntu onto different external hard drives and pendrives etc., and they worked fine, but then i connected them onto other computers, and some of them worked, while others didn't (these were all new and modern computers!)
as it turned out, it was because the drives were either 160 or 250 gb ones, and i put a big ntfs partition to the beginning, and put some small partitions to the very end of the disks for ubuntu. once the boot partition was above the 128gb mark, some computers were unable to boot grub. i moved the boot partition to the beginning of the disk, and all was well.
so make a small /boot partition at the beginning of the disk space. or if you wish /boot be on the / partition, then make the / partition on the beginning of the disk, and make sure it isn't too big (10 or 20gb should be more than enough), so it remains bootable on any computer.
i always though this 128gb bios limitation is already solved since many years, but seemingly, some bioses still having it (at leas on usb drives)

---

### Post by chrols on 2010-01-16
I had hoped I had made myself clear in my initial post but regardless: The USB HDD is perfectly happy to boot if I put a live USB edition on the disk, but not with GRUB. While that fact would suggest it, I should probably also state explicitly that the BIOS never fails to detect the HDD.

Also the thought had crossed my mind that it might have something to do with settling times. However I think I have ruled that out, as I stated earlier with a live USB edition on the disk it boots all of the time, with GRUB none of the time.

Finally, the problem is not that the partition is to large for BIOS to detect as I've tried both with and without a small (~40 mb) boot partition at the beginning of the disk.

---

### Post by chrols on 2010-01-18
For anyone with similar problems:

I went ahead and made it work with SYSLINUX, took much less time than anticipated and in retrospect I should have tried that earlier.

---

