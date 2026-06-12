---
title: "Install via WINE"
date: 2010-09-06
forum: General Help
---

### Post by borth92 on 2010-09-06
install game from cd thru wine?

i would like to run install disks via WINE, but there is a problem. the CD's are by default not executable, and the cd is read only, so when I try to change that I cant. Any ideas?

---

### Post by t0p on 2010-09-06
Maybe you can copy the CD, then burn the disk image/files to another CD which you can make executable.  Or run it straight from the hard drive.

---

### Post by pbrane on 2010-09-06
You should be able to run the installer from the CD if you can see the CD in wine. The installer ( setup.exe or whatever it's called ) should be executable. Basically you would run them just like in windows. I don't have wine installed at the moment but I have done this in the past.

The CD itself is not an executable file. It's a storage medium. The fact that it is read only has no bearing on the stored files being executable or not. Just write-able.

---

### Post by mc4man on 2010-09-06
This is a result of a well intended but incredibly  mis-implemented security policy starting in lucid 
This is compounded for cdrom's by having no fstab entry which would override the policy.

See here post 10 for 3 different ways - if you wished to revert the policy for wine then post 13 tells you where to edit the launch command

for your current use method 2 (custom launcher) will be fine and easiest
[http://ubuntuforums.org/showthread.php?t=1467914](http://ubuntuforums.org/showthread.php?t=1467914)

---

