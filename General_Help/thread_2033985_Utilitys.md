---
title: "Utilitys"
date: 2012-07-27
forum: General Help
---

### Post by mayagrafix on 2012-07-27
With Windows I use a set of utility programs (Defraggler, Ccleaner, Recuva and Speccy from Piriform.com) for general upkeep and maitenance of the HD and System. Are there similar programs in the Ubuntu world?

Speccy in particular is an information tool for the PC. Speccy will give you detailed statistics on every piece of hardware in your computer. Including CPU, Motherboard, RAM, Graphics Cards, Hard Disks, Optical Drives, Audio support. Additionally Speccy adds the temperatures of your different components, so you can easily see if there's a problem <=== Temperatures are important to know!

Thanks for any info and or help. Ubuntu with Unity ROCKS!:KS

---

### Post by Kirboosy on 2012-07-27
_cCleaner Like_
[Ubuntu Tweak]("http://ubuntu-tweak.com/")
[Bleachbit]("http://bleachbit.sourceforge.net/")

_Recuva Like_
[Data Recovery]("https://help.ubuntu.com/community/DataRecovery/")

_Defragler Like_
Not Needed really...

_Speccy Like_
[Sensors]("https://help.ubuntu.com/community/SensorInstallHowto")

Hope that helps! :)

---

### Post by Cheesemill on 2012-07-27
To get a full rundown on all of your hardware:
```
sudo lshw -html > lshw.html && firefox lshw.html
```

---

