---
title: "Can't Boot After Install"
date: 2012-08-10
forum: General Help
---

### Post by moniker127 on 2012-08-10
Hello I just installed Ubuntu 12.04 to dual boot with windows 7 through the Ubuntu installer. 
After installing, my computer restarted, and Ubuntu is now in the list of select-able operating systems along side windows 7. Windows 7 works fine, but when I select Ubuntu, I see only a blank purple screen. No keys seem to do anything, and I just have to power off my computer to continue. To make sure nothing would happen, I let it sit for a few hours to finish any potential install, and I tried booting with each one of my peripherals disconnected individually. 

My computer has an intel q6600, 4 gigs of ram, an nvidia 550 ti, and a one terabyte samsung spinpoint harddrive. 

Does anyone know why it won't boot and how I can fix this?

---

### Post by Kalanac on 2012-08-10
Could be a bad install.  Double check the md5 sum of your downloaded image and run the "check this disk for defects" option from the boot menu to double check all the files are OK.

If everything checks out fine, try re-installing Ubuntu.

[https://help.ubuntu.com/community/BurningIsoHowto/](https://help.ubuntu.com/community/BurningIsoHowto/)
[https://help.ubuntu.com/community/HowToMD5SUM/](https://help.ubuntu.com/community/HowToMD5SUM/)

---

### Post by Ninnetyer on 2012-08-10
Im not a guru but, I'm asumming you installed ubuntu with the live cd and not with the wubi program, if not then try installing with the live cd and let the ubuntu installer handle the partitioning by telling it how much space will each OS have.
A while ago I tried installing ubuntu inside windows with wubi and it didn't boot.
Still if you are in grub try second option (recovery mode), and try failsafe graphics, then resume boot, for some reason when i installed 12.04 with an nvidia card it didnt show anything when I boot the system, same for my ati card, fail safe save my life. if it doesn't work obviously is bad installation.
Hope this helps.

---

