---
title: "BIOS update with Asus M2A-VM"
date: 2010-09-14
forum: General Help
---

### Post by TheFalcon 2010 on 2010-09-14
In the Asus website (M2A-VM) it says "Please update bios version to 0901 to support Linux OS".also in Ubuntu wiki it says "Uprading the BIOS to at least 0601 is strongly recommended".and my currently bios version is 0302.
now i am confused because i have read that updating bios has a high risk and can make my pc not boot.so will it be easy as in this [page]("http://support.asus.com/technicaldocuments/technicaldocuments.aspx?root=198&SLanguage=en-us") using EZ-Flash?
and in this bios versions [page]("http://support.asus.com/download/download.aspx?SLanguage=en-us&product=1&model=M2A-VM&type=map&f_type=3") in some versions it says that i can not use EZ-Flash.but in the latest version it does not say that,does this mean i can use EZ-Flash to update from 0302 to 5001?
Please Help thank you

---

### Post by sanderj on 2010-09-14
I have got a M2A-VM HDMI myself, and I've upgraded the BIOS a few times: put the new BIOS on a USB stick, reboot system, go into the BIOS setup -> BIOS upgrade, wait a few minutes and you're done.

Easy.

Dangerous? I don't know; I've only upgraded a few times.

---

### Post by TheFalcon 2010 on 2010-09-14
I have just updated it to the latest version (5001 beta) without problems :D using EZ-Flash.
Thanks any way:).

---

### Post by philinux on 2010-09-14
> **TheFalcon 2010 said:**
> I have just updated it to the latest version (5001 beta) without problems :D using EZ-Flash.
Thanks any way:).

Could you describe the process step by step to help others with this type of mobo.

---

### Post by TheFalcon 2010 on 2010-09-14
ok,
When the system is at POST after boot-up,press "Delete" to enter BIOS setup and access EZ-Flash from the "Tools" option on the navigation bar.
Step 1.
Please select Tools > ASUS EZ Flash 2 > YES
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169431&stc=1&d=1284466113[/IMG]

Step 2.
Please wait for checking system BIOS.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169432&stc=1&d=1284466113[/IMG]

Step 3.
Please insert unzipped BIOS in selected path drive so system can detect the file. 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169433&stc=1&d=1284466113[/IMG]

Step 4.
Please wait for system to check BIOS file.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169434&stc=1&d=1284466113[/IMG]

Step 5.
Click "Yes" to update BIOS after system has finished checking. 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169435&stc=1&d=1284466113[/IMG].

Everything worked fine :).
Note:This explanation is from the official ASUS website.

---

### Post by TheFalcon 2010 on 2010-09-14
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169437&stc=1&d=1284466650[/IMG]

---

### Post by Jazzy_Jeff on 2010-09-14
It is nice to see they are making it super easy to update the BIOS now.

---

### Post by TheFalcon 2010 on 2010-09-14
ok,now i upgraded to the latest version.Here is the description of the latest bios version:
M2A-VM BIOS 5001
1&#65294; Beta Bios for Supporting AM3 CPUs.
2&#65294; System still able to POST when set CPU Multiplier to 35X, but actual frequency will not change.
3&#65294; Due to chipset limitation, Max HT Link is 1000MHz only.
4&#65294; It will no display if downgrade Bios to lower version.

But in an older bios version:
M2A-VM release BIOS 0901 
Fixed video output flicker or black screen
Fixed that AM2 Athlon(tm) 61 X2 Dual Core Processor 6000+ CPU show "AMD Processor Model Unknown" message
[COLOR="Red"]Fixed Red Hat Enterprise Linux 4 installation failed[/COLOR]
Fixed sometimes can’t resume from S3
Modify MB temperature range of PC Probe II 

now my question is does the latest version include the older ones or will i have to downgrade to install Ubuntu?

---

### Post by ubfu on 2010-09-15
Pretty sure they include all the previous fix into their latest bios.But do remember 5001 is a beta for AM3 support.
So I guess you can install ubuntu linux without any problem.If anything happens just downgrade it.
Reset to the default setting of the bios and Make sure when updating using ez flash, no one should interrupt the process.

---

### Post by pgarnett on 2010-10-12
Several gotchas that almost got me:
- the Asus website warns against using the EZ Flash utility to upgrade from very old BIOS versions, and recommends using the DOS Boot floppy upgrade technique instead
- if you used the EZ Flash utility anyway, and after all apparently went well your system won't boot and won't even display the BIOS setup screen, before you conclude you've just bricked our system, remove the BIOS battery (the button battery on the motherboard), wait 60 seconds, replace the battery, and try booting again.  It worked for me. YMMV.

~Pryor

---

