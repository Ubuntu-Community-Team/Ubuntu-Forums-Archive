---
title: "Unresponsive desktop"
date: 2011-03-01
forum: General Help
---

### Post by Timos798 on 2011-03-01
Hey UbuntuForums,
I recently installed Ubuntu 10.10 as a dual-boot with Windows 7. But when I boot into Ubuntu and open firefox or any other application, the desktop becoms unresponsive, I can only switch applications, but I can't close any of them unless I right click on the taskbar and click close. I can't even turn off my computer unless I use the power switch on the computer itself. Does anyone know what could be causing this problem and how to fix it?
Thanks

---

### Post by soullessgod on 2011-03-01
try running nautilus.

alt+F2 -> type nautilus

---

### Post by ajgreeny on 2011-03-01
What hardware are you running?  If you are not sure open a terminal and use command ```
sudo lshw >hw.txt
``` which will make a file called hw.txt in your home folder.  Copy that file back here in code tags (use # in reply box and copy the text between the two tags which appear).

---

### Post by Timos798 on 2011-03-01
Hardware:GPU-Ati Radeon HD 6970
Processor- Intel i5 @3.2GHZ
Motherboard- Asus P7P55D Deluxe
RAM-2 x 2GB

---

### Post by Rubi1200 on 2011-03-01
Try turning off desktop effects as a start to see if that helps.

System > Preferences > Appearance > Visual Effects > None

---

### Post by Timos798 on 2011-03-01
Nothing helps, it still doesn't work. Rubi1200 the desktop effects were already off from the start. Could it be that the installation went wrong and maybe corrupted something that causes this?

---

### Post by rockstarrem on 2011-03-01
It's possible, yeah, did you test the disc before you installed it? Make another disc and verify the data in your ISO burner of choice (I recommend IMGBurn for Windows), and then reinstall the OS. That's if you don't mind doing so, of course.

---

### Post by Timos798 on 2011-03-01
> **rockstarrem said:**
> It's possible, yeah, did you test the disc before you installed it? Make another disc and verify the data in your ISO burner of choice (I recommend IMGBurn for Windows), and then reinstall the OS. That's if you don't mind doing so, of course.
Yeah, I checked everything on the disc using PowerISO, everything was fine, but I was having problems before(which Rubi1200 knows about) and I think those problems might have affected the installation somehow. Oh well, I'll just format the drive and do a re-install.
Thanks.

---

### Post by bryanfblareunion on 2011-03-01
Get a new desktop. Apparently a core i5 3.2 GHz with 4GB of RAM isn't fast enough for your Ubuntu install. lol

---

### Post by Rubi1200 on 2011-03-02
You have an ATI Radeon video card.

See here for more details:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Timos798 on 2011-03-04
I re-installed Ubuntu and installed all the drivers, but nothing has changed, it still stops working after a couple of mins.

---

### Post by bcbc on 2011-03-05
What's the version of your bios? Perhaps there is an update available that might help.

---

### Post by dwitkin on 2011-03-07
I'm having the exact same problem. My HW.txt file is attached. Any help would be appreciated.

I also wiped the install clean and reinstalled. Note that the desktop DOESN'T freeze when I boot into the "safe" desktop mode (I can't remember exactly what the mode is called, but it is the safer GUI desktop.)

Thanks.

---

