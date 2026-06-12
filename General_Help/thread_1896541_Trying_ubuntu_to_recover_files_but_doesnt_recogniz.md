---
title: "Trying ubuntu to recover files but doesnt recognize external drive"
date: 2011-12-17
forum: General Help
---

### Post by UbinTook on 2011-12-17
Have a W7 machine that wont boot, all test say hardware is fine, typical windows issue.  booting into an Ubuntu 11.10 disk and "trying"  i  am able to see the files i need to copy.
Issue is this...if i try to boot into Ubuntu with the external drive attached( to copy files to) the machine wont boot, if i allow it to boot without the drive, then attach it, Ubuntu doesn't see it.
   any suggestions on how to get Ubuntu to see this drive after its running?

---

### Post by dandnsmith on 2011-12-17
This sounds like a problem with the format of the external HDD, and possibly the BIOS settings for boot order as well.

How recent is the machine?
Have you tried booting Ubuntu without that external drive, and then running gparted to see what it tells you about your primary drive?
Have you tried attaching the external drive and then running *lshw* with root privileges, to see whether the hardware is recognising the external drive?

---

### Post by UbinTook on 2011-12-17
Machine is an HP about 3 years old.
Maybe im not looking in the correct place for the disk...where should it be shown? and as what?


Disk was recently quick formatted on a W7 machine...should l i reformat? how? to get correct format?
I can seem to find anything in the HP BIOS that even says USB in boot order.
ubuntu is very new to me so i dont even know what gparted and ishw are let alone how to run them.
instructions?

---

### Post by UbinTook on 2011-12-17
now i cant even get ubuntu to load, its sitting at the screen with the ubuntu logo with the dots chnaging form orange to white...been doing this for 20 minutes, occasionally you can hear cdrom or Hdd activity.

---

### Post by dandnsmith on 2011-12-18
That sounds, despite your 'tests' having shown the hardware as OK, as though you have a serious problem with that PC.
I suggest you suspect the RAM first - if you don't know how to go about testing the PC properly, then you may have to involve outside help.

---

### Post by UbinTook on 2011-12-18
well, i tried several more times to load ubuntu11.10,  it just hung and hung.  i gave up and used a  partedmagic boot disk, it loaded quickly i was able to retrieve all the files and have since formatted/restored and reloaded the files.  Screaming along without issue.
  Not sure what the issue was, but the only time i was having issue was in trying to load ubuntu.(even though it worked once, it wouldnt again afterwards)

---

