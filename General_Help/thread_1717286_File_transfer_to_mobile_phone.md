---
title: "File transfer to mobile phone"
date: 2011-03-29
forum: General Help
---

### Post by dlemos on 2011-03-29
****Hi all 

I'm trying to send mp3 files via usb to my mobile phone, but file transfer speed gets incredibly low, like 5,3 kb/s.

Any idea on how to solve this / useful ubuntu software ?

Thank you

---

### Post by sanguinoso on 2011-03-29
What kind of phone is it, and have you tried it on another OS?

---

### Post by dlemos on 2011-03-29
[LG GD 510]("http://www.lg.com/uk/mobile-phones/mobile-phones/LG-touch-screen-phones-GD510.jsp")

Yes, Win7, used to work fine:/

---

### Post by sanguinoso on 2011-03-29
What kind of speeds did you see with Windows 7? Also, what method are you using to put the files on there? Drag and Drop? Are you connecting the phone in the same usb port?

---

### Post by dlemos on 2011-03-29
Used to work fine on windows, don't know the exact speed but seemed fast enough.

I tried several usb ports. I'm only using copy-paste. 
What I don't understand is, part of the file is quickly copied, but the other is slow.

For instance I'm trying to copy a 34mb .mp3 file

The progress bar of the file operations window goes fast untill 33mb, then it stops there. 

I've attached a screenshot

:confused:

---

### Post by sanguinoso on 2011-03-29
Just to verify, you have enough space on the device correct? Because I see one 4MB filesystem and one 2GB filesystem. Unfortunately it looks like this could be an open bug. I'm assuming your usb slots are 2.0? See here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/177235](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/177235). There are some workarounds in there that you could try.

---

### Post by dlemos on 2011-03-30
Yes, USB 2.0 and plenty of space left. I'll try the steps on the link and then I'll give some feedback to this topic, thanks!

---

### Post by SeijiSensei on 2011-03-30
> **dlemos said:**
> The progress bar of the file operations window goes fast untill 33mb, then it stops there.

If you wait long enough, does it complete the copy?  Copying between devices is usually buffered by the operating system.  At the beginning things go quickly as the buffer is filled, then slow down (sometimes considerably) while you wait for the buffer to be drained.

That said, I have an older LG that refuses to work with Linux via USB and only grudgingly so with Bluetooth transfers.  Other phones have these problems, too.  See this [bug report](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363329).

I like my phone, but I won't buy another LG phone after this experience.

---

### Post by dlemos on 2011-03-31
It does complete the transfer. Th phone is approximately 2 years old I guess.

Sorry for my "noobness", but what does mount exactly mean? The devise is recognized and accessible by the OS, everything seems functional, except for the file transfer speed.

---

### Post by SeijiSensei on 2011-03-31
> **dlemos said:**
> It does complete the transfer. Th phone is approximately 2 years old I guess.

Sorry for my "noobness", but what does mount exactly mean? The devise is recognized and accessible by the OS, everything seems functional, except for the file transfer speed.

You "mount" devices into the file system tree.  If you mount your phone's disk drive, it's assigned to a location like /media/disk with the appropriate drivers that correspond with the type of filesystem on the device.  Most USB devices like phones use either the older "FAT32" filesystem, the one used by DOS and Windows before Windows NT was introduced, or "NTFS" the filesystem used by Windows since that time.

To see the list of mounted devices on your machine, just type the command "mount" at a terminal prompt.

---

### Post by dlemos on 2011-04-01
I've updated the mobile phone firmware.

I get superior speeds now like 100-300 kb/s, but it's still slow.

I'm trying to transfer the files not to the phone internal memory but to a microSD card. The devices are mounted. Do I need a specific driver to transfer files via usb to a microSD card?

---

