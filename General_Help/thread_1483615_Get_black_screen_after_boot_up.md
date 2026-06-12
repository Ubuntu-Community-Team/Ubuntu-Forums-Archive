---
title: "Get black screen after boot up"
date: 2010-05-14
forum: General Help
---

### Post by relldagreat on 2010-05-14
Hey guys i'm some what new when it comes to using ubuntu. I had an improper shutdown and now when I try to use recovery mode or simply load the first unbuntu option I get an all black screen. can some one help please. I don't know what to do

---

### Post by rudeboyskunk on 2010-05-14
Usually when something like this happens and I can't figure it out, I end up just doing a fresh install of Ubuntu (using a usb flash drive so I can save files that I need).  Are you dual-booting into Windows or another OS?

---

### Post by Sin@Sin-Sacrifice on 2010-05-14
Sounds like something wasn't written to the disk properly. You can try to search it out and replace it by looking at log files but it would probably take less time to reinstall. Whenever you have to "shut down improperly" you sould never hit the power button or pull the plug unless you absolutely have to. In stead you should hold right ctrl+alt+prtscr/sysrq (prtscr is right above backspace) and type the letters R-E-I-S-U-B  which writes to disk and a few other things before rebooting. Not sure if you'll be able to recover from the black screen but stick around and see of someone else has a better solution.

---

### Post by relldagreat on 2010-05-14
how do i boot up windows again?

---

### Post by Sin@Sin-Sacrifice on 2010-05-16
Heh... well... if you didn't write over it when you installed ubuntu then rebooting should bring you to a list of installed operating systems. Select windows. If you wrote over it then I hope you have an install disk.

---

### Post by garvinrick4 on 2010-05-16
```
XP fix boot 
How to restore the Windows XP bootloader For this you will need your Windows XP installation CD. Boot into it now. You will get to a part where it asks if you want to repair or recover. To do so, press "r". If prompted, enter your Windows XP administrator password. This will leave you at at a command line, so type in the following two commands: 

Code: fixboot 

Code: fixmbr 

Code: exit 

Vista and 7 fix boot 
How to restore the Windows Vista or 7 bootloader To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD. If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download for Vista or Win 7. When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer." On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next. Then click on "Command prompt". From there, type in the following: 

Code: bootrec.exe /fixboot 

Code: bootrec.exe /fixmbr 

```

---

### Post by garvinrick4 on 2010-05-16
After you get Windows booted. Lets use your installation Ubuntu disk in try only mode and get Ubuntu fixed. Let us know what is going on.

---

