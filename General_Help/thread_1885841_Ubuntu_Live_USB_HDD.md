---
title: "Ubuntu Live USB HDD?"
date: 2011-11-24
forum: General Help
---

### Post by JeremyT on 2011-11-24
I've been trying to do a little googling, but I haven't come up with an answer.

I got a bus powered USB HDD to be able to use Ubuntu on any computer as I would with my USB flash drive.  However, the ways I found to accomplish this for the flash drive don't work.

Does anyone know how to do this? Or would just installing Ubuntu onto the USB drive be best?

---

### Post by rokytnji on 2011-11-24
Have you tried formatting the external drive with a fat32 partition ,(I don't know the size of your external hardrive) , hence a suggestion of lets say a 20 gig fat32 partition.

Boot up a Ubuntu (10.04 on up) since I don't know if you are running Ubuntu Yet. You can do this as a live session off of a 10.04 cd if not installed.

After booting up Ubuntu. Use the live USB creator in ubuntu and pick the persistent option for that fat32 
partition you made. It will do the rest. Be careful to make sure you point the installer to the external usb Hardrive and then to the fat32 partition next before clicking OK.

---

### Post by JeremyT on 2011-11-24
Well, it looks like I just didn't wait long enough when I went the  boot device menu.  At first it just hung there for a while with an underscore blinking and it seemed to be stuck.  However, when I waited long enough it finally got to the boot device menu.  And I gotta say, once Ubuntu is loaded its a lot snappier off of the USB HDD compared to the thumb drive.

I'm going to have to check my home computer when I stop by tomorrow to see if it works there too (I don't think it even realized there was a bootable drive attached)

---

### Post by efflandt on 2011-11-24
Whether a computer will boot from a USB drive depends upon boot order set in BIOS, and possibly BIOS USB setting. Otherwise the BIOS splash screen during boot usually lists a function key (or Esc) to select a different boot device on the fly.

---

### Post by JeremyT on 2011-11-24
Yeah, on my Acer Aspire AX1301-U9052 it doesn't seem to work with my external usb hdd as a boot device.

In BIOS, I get a vague boot order that only lists Device type vs specific devices like I've seen in other BIOS.  So I get "Hard Drive", "Removable" some NVIDIA thing, and I believe one other thing.

When I hit F12 to select a boot device, only my internal HDD is visible under hard drive and nothing is listed under removable.

I'm wondering if the problem I have on the computer I was using last night is related to this one.  On that computer when I loaded select a boot device screen it took 1-3 minutes for it to actually load that screen where without the drive or with my USB flash drive it loads relatively instantly.

A little info about my HDD:
It's a brand new [OWC bus powered USB 3.0]("http://eshop.macsales.com/item/OWC/ES2.5BPU3S/") (using 2.0 right now) case with a [Hitachi 120 GB drive]("http://eshop.macsales.com/item/Hitachi/0A57910/").

---

