---
title: "Computer won't boot from cd"
date: 2011-11-17
forum: General Help
---

### Post by Cooter2543 on 2011-11-17
My friend's computer crashed, and I'm trying to do a clean install for him. The problem is it won't boot from any CD I try. I've tried two versions of Windows and three versions of Ubuntu that have all worked on separate systems, in both of the computer's CDROM drives. Both drives are recognized by the BIOS, and I have double and triple checked the boot priority order. 

The lights on the CD drives come on, and the disc spins up, but still takes me to the GRUB screen. Here's the thing, even when I disable the HDDs in BIOS setup, it STILL takes me to the GRUB screen.

Can anyone help?

---

### Post by Cooter2543 on 2011-11-17
After pulling my hair out for hours, I figured it out. I unpluged the power cables on the hdd, and it booted to CD. Then I shut it down, replugged the HDDs, and it worked just fine. I don't know why, but it worked.

---

### Post by jjex22 on 2011-11-17
There's a few options - bios update may help? In the immediate there's always the analog option of unplug the hdd until the cd getss to it's boot selection screen then plug the hdd in?

less rash if you can usb boot you could try making a usb key or a usb key of a [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") if you have a key smaller than 2gb

---

### Post by jjex22 on 2011-11-17
Glad all's sorted! :)

---

