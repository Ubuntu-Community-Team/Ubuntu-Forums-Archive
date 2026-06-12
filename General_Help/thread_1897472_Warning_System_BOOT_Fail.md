---
title: "**** Warning: System BOOT Fail ****"
date: 2011-12-19
forum: General Help
---

### Post by SuperFreak on 2011-12-19
I am getting a error message when I try to boot my computer.

**** Warning: System BOOT Fail ****
Your system last boot fail or POST interrupted.
Please enter setup to load default and reboot again.

Press F1 to continue, DEL to enter SETUP.


If I press F1, It boots into Grub menu and I can go into Ubuntu

I have a dual boot with Win XP.
I have an Asus M2N-E MB, 2 sata Western digital drives (1 TB and 2 TB both which come up under SMART attributes as healthy), I have 2 GB of Corsair RAM (which I have tested twice with MEM86+ and it passes without error
The RAM was replaced recently

---

### Post by seawolf167 on 2011-12-19
Do you get this message during every single boot attempt? If so, since you mentioned that you changed RAM in your machine, you may have to go into BIOS (hit [DEL] to enter setup/BIOS) and check or clear any warning messages that exist for it to boot without displaying it each time.

While in BIOS, check that your RAM timings and speed are correctly entered and/or auto-detected.

Otherwise, if it was a one-time message, its fine since it was just a warning saying that something stopped POST from completing the previous time.

---

### Post by SuperFreak on 2011-12-19
This seems to happen everytime I boot now but initially when I installed the RAM it did not happen for at least 3 weeks. I will check out the items you mention, but where in the BIOS settings would the warning messages be (I did on one occasion reset BIOS to default to no avail)?

Thanks for your reply

---

### Post by seawolf167 on 2011-12-19
A couple suggestions for you to try:

Clear and reset CMOS (i.e. pull battery or set jumper to reset mode), ensure that the battery is not dead

Reinstall the Windows & Ubuntu bootloaders/MBR:
Boot off the Windows XP cd, enter the recovery console and run [fixboot ]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixboot.mspx?mfr=true")and [fixmbr ]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true")- now see if Windows is able to start normally. Then reinstall Grub following [these ]("https://help.ubuntu.com/community/Grub2#Use_Boot-Repair_Graphical_Tool")instructions.

If its still not booting, try flashing your BIOS to a newer version if available. Search the manufacturer's website for your Mobo make/model # and check for BIOS updates.

---

### Post by SuperFreak on 2011-12-19
Seawolf On your first recommendations I have attached photos of my BIOS screens with regards to my RAM settings. It all seem to be set in auto. I can not find any page in BIOS that has warnings listed. There is one phot I posted that shows timings of RAM; they appear to be correct (The Corsair RAM I bought is 5-5-5-18 and it is 1.8 V) but there are more entries below that I don't understand as I only have the one stick installed(Image 1 and 2).

I am reticent to make changes to my Grub menu until I have backed up my drives and it may be a week or so before I can do that. I will repost later at that point if I have further issues thanks for your kind help

---

### Post by halw on 2011-12-19
Have you tried to reseat your memory modules?

---

### Post by SuperFreak on 2011-12-19
I looked at the RAM and it appeared seated correctly but I reinstalled it anyway.
I also cleared CMOS and reentered my BIOS settings and the clock . I rebooted and I did not have the error message. Time will tell if this corrected the matter.
I will consider running  fixboot and fixmbr and reinstalling Grub if I have further problems, but I need to back up data first. 


The computer is 6 years old and doesn't owe me any favours. In the Spring I intend to build a new system with the Ivy Bridge chip

---

### Post by seawolf167 on 2011-12-19
> **SuperFreak said:**
> I also cleared CMOS and reentered my BIOS settings and the clock . I rebooted and I did not have the error message.

POST probably hasn't been completing properly. Since the error didn't occur after the CMOS reset, go buy a new CMOS battery and I'd be willing to bet you won't see the error message again.

---

### Post by SuperFreak on 2011-12-19
Thanks, I will do that

---

