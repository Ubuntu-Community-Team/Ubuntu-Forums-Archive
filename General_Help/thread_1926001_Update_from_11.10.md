---
title: "Update from 11.10"
date: 2012-02-15
forum: General Help
---

### Post by DoctorVell on 2012-02-15
I am just wondering when there is a new update to 12.04 and I currently use the WUBi installation method as a dual boot for my system, do I need to do a fresh install or will an update work perfectly fine?

Thanks

---

### Post by bcbc on 2012-02-15
12.04 will be released in April (the release number indicates the date 2012/April). 

Release upgrades are tested extensively during the development phase, however, in practice there are many upgrade failures. Wubi installs can be upgraded the same as a normal dual boot (there are slightly different potential problems with a wubi upgrade but unless there is a regression it this will not an issue). I strongly recommend a full backup prior to upgrade... what this means is simply backing up your C:\ubuntu\disks directory from Windows (change drive letter as appropriate), as well as the C:\wubildr file.

Then if the upgrade fails you can just copy back the old virtual disks and the wubildr to restore the 11.10 version.

While it is possible to upgrade prior to the April release, it's not recommended on your main computer, unless you are prepared for potential breakage. Refer to the [Precise (Ubuntu+1) forum]("http://ubuntuforums.org/forumdisplay.php?f=412") for more info.

Edit: I forgot to add - it's important to read the Release Notes thoroughly prior to upgrading as they document any known issues, and it's important to check whether any of these apply to your setup.

---

