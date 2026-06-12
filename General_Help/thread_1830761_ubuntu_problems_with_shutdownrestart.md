---
title: "ubuntu problems with shutdown/restart"
date: 2011-08-22
forum: General Help
---

### Post by ParaIdioma on 2011-08-22
I have dual boot win7 and ubuntu. If i start PC in WIN7 and then shut down PC and launch again to win 7 everything is fine. IF i restart o launch at first to ubuntu and then SHUTDOWN from ubuntu i get bios startup crash and restart (message that boot was interrupted/error no more details press f1 to continue ) and  i am able to boot to win7or ubuntu again from grub. If I REBOOT from ubuntu i can boot to ubuntu with no problem but if i try WIN7 it crashes on login screen (and after restart i can boot anywhere again). I updated my bios (did not help) and have no idea what to do next as i can not find any more info

---

### Post by sanderd17 on 2011-08-22
Do you completely shut down Win7? If you do fastboot, hybernate or suspend, than you need to reboot to the same OS.

---

### Post by ParaIdioma on 2011-08-22
> **sanderd17 said:**
> Do you completely shut down Win7? If you do fastboot, hybernate or suspend, than you need to reboot to the same OS.

yes complete shutdown: win7

---

### Post by ParaIdioma on 2011-08-22
at first i thought it is some win7 problems or grub (i reinstalled it)
but it is clear that if i use only win7 everything works fine.
If i use only ubuntu restarting to ubuntu works ok but if i shutdown and start pc again i get PC BEEP no BIOS image (like a failed atempt) then 1 more BEEP BIOS image and a message later:
-----------------------------------------------
Warning: System Boot Fail
Your system last boot fail or POST interrupted
Please enter setup to load default and reboot again

press F1 to continue     DEL -setup
--------------------------------------

del - goes to bios settings
F1 everything boots fine

---

### Post by sanderd17 on 2011-08-22
maybe look in the BIOS if you can disable a "fastboot" setting or so.

---

### Post by ParaIdioma on 2011-08-22
> **sanderd17 said:**
> maybe look in the BIOS if you can disable a "fastboot" setting or so.
there is no fastboot setting in BIOS
i found Quic boot one and disabled it but that did not solve anything made bootup ultra slow but the problem remained, so after few cycles of shutdown ubuntu - start PC BOOT FAIL - F1 - ubuntu - shutdown - boot fail - f1 i reseted bios settings to default settings to boot up faster
any other ideas?
Can that harm my PC?

---

### Post by raja.genupula on 2011-08-22
> **ParaIdioma said:**
> at first i thought it is some win7 problems or grub (i reinstalled it)
but it is clear that if i use only win7 everything works fine.
If i use only ubuntu restarting to ubuntu works ok but if i shutdown and start pc again i get PC BEEP no BIOS image (like a failed atempt) then 1 more BEEP BIOS image and a message later:
-----------------------------------------------
Warning: System Boot Fail
Your system last boot fail or POST interrupted
Please enter setup to load default and reboot again

press F1 to continue     DEL -setup
--------------------------------------

del - goes to bios settings
F1 everything boots fine

hey sometimes i got this , sometimes with out booting option directly grub loading going on .i have enquired  about this and got it as CMOS battery problem .why dont you give a try .

---

### Post by ParaIdioma on 2011-08-22
i do not want to damage my PC and not sure if i shoud mess with hardware
do you mean i should reset cmos? 
as I said it seems to be ubuntu issue because if i startup shutdown startup shutdown Windows 7 everything works fine without any problems and only after starting ubuntu i get the problem

---

### Post by ParaIdioma on 2011-10-25
:/ Cmos reset and battery change did nothing 
i got new ram/psu and that did not solve the problem too
i tried xubuntu and kubuntu and that did not solve 

i will format and reinstall ubuntu in a few weaks hope that will solve

---

### Post by ParaIdioma on 2011-11-08
Fresh install Kubuntu on new SSD did not solve the problem

---

### Post by ParaIdioma on 2012-05-16
upgrade to 12.04 solved

---

