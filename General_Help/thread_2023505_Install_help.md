---
title: "Install help?"
date: 2012-07-12
forum: General Help
---

### Post by pmahoney14 on 2012-07-12
Here's the situation:
My old computer got a very nasty virus on it and to get rid of it I ended up reformatting my hard drive. So now I have a blank formatted hard drive. When I try to install ubuntu onto it as an external hard drive it says it installs but then i cant boot from my broken computer. Any suggestions?

P.S. It always says "bootmgr is missing"

---

### Post by papibe on 2012-07-12
It looks like grub (the program that shows the boot options) was not installed in the main disk (the one that is set on the BIOS to boot up from).

I would recommend using the CD/USB installer as a Live CD,  and repair your boot disk using the tool Boot-Repair. Take a look at this [guide]("https://help.ubuntu.com/community/Boot-Repair") for details.

I hope it helps, and tell us how it goes.
Regards.

---

### Post by kc1di on 2012-07-12
> **pmahoney14 said:**
> Here's the situation:
My old computer got a very nasty virus on it and to get rid of it I ended up reformatting my hard drive. So now I have a blank formatted hard drive. When I try to install ubuntu onto it as an external hard drive it says it installs but then i cant boot from my broken computer. Any suggestions?

P.S. It always says "bootmgr is missing"

go here and download boot-repair burn it to a cd and run it.
it should install the boot loader for you.

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by pmahoney14 on 2012-07-12
Thank you but the computer is unable to read a disk or flash drive.

---

### Post by papibe on 2012-07-12
> **pmahoney14 said:**
> Thank you but the computer is unable to read a disk or flash drive.

This could be possible:
[LIST]
[*]Take the disk out, and put it in an USB enclosure.
[*]Find a computer that can boot from USB or CD.
[*]Use the Ubuntu Live CD/USB to boot into the Live Desktop (Try Ubuntu option).
[*]Very carefully use Boot-Repair to install grub on the external disk and **not** in your main disk: Grub Location tab -> Place Grub into
[/LIST]
That should be it.

If you are not sure what is the logical name of your external drive (e.g. /sda1 or /sdb1, etc) open 'Disk Utility' before repairing so you are absolute sure (Hint: usually the main disk is sda1 and an external would be named sdb1).

Tell us how it goes.
Regards

---

### Post by kc1di on 2012-07-13
> **pmahoney14 said:**
> Thank you but the computer is unable to read a disk or flash drive.

does it allow you to boot to the Bios screen?
There you should be able to choose a priority boot disc. 
eitther usb or CD.  or tell it which disk in the machine to boot from.  my guess is that you installed the grub boot manager in the root section instead of the MBR.  

Does the machine have windows install?  if so does it boot to that?

Give us some information about the machine please.

Post like it doesn't boot to usb or cd is of little help in trying figure out what's going on.

---

