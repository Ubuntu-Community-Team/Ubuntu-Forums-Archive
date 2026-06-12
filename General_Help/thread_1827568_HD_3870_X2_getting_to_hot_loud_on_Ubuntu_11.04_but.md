---
title: "HD 3870 X2 getting to hot/ loud on Ubuntu 11.04 but not on Windows"
date: 2011-08-18
forum: General Help
---

### Post by windozer101 on 2011-08-18
Hey guys, as the title says the HD 3870 X2 is getting very hot and loud on My **fresh** Ubuntu 11.04 (64bit) Installation.
But on Windows 7(64bit) it's running just fine

AFAIK there are 4 profiles saved in 3870's BIOS 
the BOOT Profile = Maximum performance and energy consumption (that i can hear at boot it is extreamly loud)

the 2D Profile = Medium Performance - lower energy consumption and quiet

the 3D Profile = Medium to Maximum Performance (on demand) Crysis2 = very Loud

the idle Profile = Low Performance and Low energy consumption (Windows Explorer/ Photoshop)

the problem is IMHO that the card doesn't switch to the default profile after the GUI booted.

so i disabled compiz/ desktop effects and stuff

the card kinda thinks i'm not in IDLE

catalyst is installed via Ubuntu's driver install program
3d acceleration works but i got a "AMD Unsupported product" Watermark in the right corner of my desktop, pretty anoying tho...

maybe something to do with the ACPI drivers ???

please help me :(

---

### Post by LowSky on 2011-08-18
this might help
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

best idea would be to find a newer more up to date driver and test it out.

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by windozer101 on 2011-08-31
> **LowSky said:**
> this might help
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

best idea would be to find a newer more up to date driver and test it out.

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

THX [LowSky]("http://ubuntuforums.org/member.php?u=330216")
unfortunately it didn't help
installed the newest one, and the problem is still there
its really sad that the ATI has got such a LAME support for linux :(

---

