---
title: "PC boot problem , please help"
date: 2009-11-28
forum: General Help
---

### Post by parkinrg on 2009-11-28
Hi 
I have been using Karmic Koala for several weeks with no problem , on a fairly new desktop.
After leaving the PC on for a few days today I came to use it and the it was frozen. I rebooted and was presented with a long list of text that I could not understand , and unfortunately did not copy.  
I tried running from live CD and this works fine ! 
After several reboots to no avail I decided to re install 9.10 . the install gets so far then just hangs !
Thinking that my CD might be faulty , I tried installing 8.04 and I get an error message 177.963325 Buffer I/O error on device fd0 logical block 0
The hard drive is SCSI , but I have an old IDE drive  with 8.04 already on it , so I installed it and it boots fine  , everything works , but if I try to re install 9.10 or 8.04 on the IDE drive I get the same problem with either it hanging or the same error message . Sorry its a bit of a ramble , 
Can anyone help ?

---

### Post by cariboo on 2009-11-29
The error you're getting is from the floopy drive, do you have one installed?

---

### Post by john newbuntu on 2009-11-29
Go through the thread [http://ubuntuforums.org/showthread.php?t=438923](http://ubuntuforums.org/showthread.php?t=438923) and see if you are able to find a solution.  Perhaps disabling the floppy drive in the BIOS might help.

---

### Post by Sverro on 2009-11-29
> **john newbuntu said:**
> Go through the thread [http://ubuntuforums.org/showthread.php?t=438923](http://ubuntuforums.org/showthread.php?t=438923) and see if you are able to find a solution.  Perhaps disabling the floppy drive in the BIOS might help.

Yes, that worked also for me.

---

