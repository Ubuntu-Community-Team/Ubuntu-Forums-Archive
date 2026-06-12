---
title: "Ubuntu install on old Emachine"
date: 2010-06-24
forum: General Help
---

### Post by techforay on 2010-06-24
I am trying to install Ubuntu 10.4 on an old Emachine.  I use a flash drive to install on an old laptop and it worked fine.  The Emachine will not recognize the flash drive untill after windows loads and I have burnt the same file to a CD and it will not load.  I burned that iso file to cd and the lowest speed.  Does anyone have some help for me.

---

### Post by dv3500ea on 2010-06-24
Have a look here: [https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")
Also ensure you have actually burned the iso rather than copying it.

---

### Post by lytithwyn on 2010-06-24
Many older machines do not support booting to a USB flash drive.  This may be the case with your emachine.

The first things I would check are the following:

[LIST=1]
[*]Be certain the bios is set to boot to CD **before** the hard drive
[*]Do you have another bootable CD you can test with?  If it will boot to a different CD, you'll know it's a problem with your disc.
[*]Be sure to burn the ISO as a disc image, and don't just burn it onto the CD as a file (dv3500ea, you beat me to it :p)
[/LIST]

---

### Post by techforay on 2010-06-24
I used InfraRecorder to burn an image.  I selected the burn image option, selected the same iso file that I loaded to the zip drive (that worked to load the laptop) and used the default setings except the speed.  I have burned it twice and have not been able to get it loaded yet.  I have tried it on two pc's.  One I just get a I\O boot error (Emachine) The other pc, I see the ubuntu logo, then a bunch of script and is gets to a certain point and repeats the same command over and over.  My bios is set to boot before the hard drive on both machines.

---

### Post by lytithwyn on 2010-06-24
It sounds like something may have happened to the image. Can you run an md5 sum on the CD and/or your image file?  It should match the following page:
[https://help.ubuntu.com/community/UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")

If you need help with that, here is an md5 sum howto:
[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by techforay on 2010-06-26
I ran MD5 on the ISO file on the hard drive.  It is the same.  I ran it on all three of the disc's that I burned and all of them are different then the ubuntu hashes.  The strange thing is that all the disc's are the same as each other.  I burned them at the lowest speed I could. I am using default setting for InfraRecorder.  Do i need to change the settings?

---

