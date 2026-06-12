---
title: "Ubuntu won't boot: Grub error 15"
date: 2010-03-13
forum: General Help
---

### Post by Shadow12313 on 2010-03-13
After I accidentally ran a distro update command ubuntu now is unable to boot.
Grub returns an error 15: file not found.

Please help me!  I am using a live cd right now.
Thanks in advance.

---

### Post by audiomick on 2010-03-13
Hallo.
This might help:

From here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
> **File Not Found (Error 15)**

 This error is the result of a GRUB 2 installation to /boot but a Master Boot Record ( MBR ) which still contains Grub legacy. This can happen if you don't select your drive when running **sudo update-from-grub-legacy**. Shortly after starting this command the user will be asked to select the device (*sda, sdb, etc*). Highlight the drive and press the space bar to select it when presented with this screen. *Failure to select a drive* will result in an *Error 15*. 
To recover from this error, GRUB 2 must be reinstalled. Go to _[COLOR=Red][Reinstalling from the LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")[/COLOR]_ for instructions. 

---

### Post by Shadow12313 on 2010-03-13
Unfortunately I am unable to install grub 2 because I am using a live cd.  The cd thinks it's already using grub two and will not update.

---

### Post by lidex on 2010-03-13
The link in audiomick's post [quoted section] gives instructions for re-installing grub2 *USING* a LiveCD. Check it out.

---

