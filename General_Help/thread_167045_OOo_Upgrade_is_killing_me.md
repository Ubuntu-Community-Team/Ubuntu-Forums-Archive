---
title: "OOo Upgrade is killing me"
date: 2006-04-27
forum: General Help
---

### Post by WoodyMahan on 2006-04-27
I am having a miserable time following the directions on Christoos post on upgrading OOo. [http://www.ubuntuforums.org/showthread.php?t=80392&highlight=howto+upgrade+openoffice](http://www.ubuntuforums.org/showthread.php?t=80392&highlight=howto+upgrade+openoffice)

1. deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./   
           This repository is gone.  I get errors anytime I try to add it to my sources.list

2. wget [ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m137/Build-2/OOo_SRC680_m137_LinuxIntel_install_en-US_deb.tar.gz](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m137/Build-2/OOo_SRC680_m137_LinuxIntel_install_en-US_deb.tar.gz)
         This link has been taken down so I cannot pull down the .deb files

3. Pulling from OOo website.
           I downloaded the .tar.gz file from the OOo website, and installed alien.
      1.  I cannot untar through the terminal because the terminal insists that the directory dos not exist unless I rename the download file to something short and sweet (OOoinstall.tar.gz for example).
      2. So I changed the name got the file to extract.  Now I cannot cd / to the extracted file because it is named (OOB680_m5_native_packed-1_en-US.9011)
      3. So I shorten the name on this as well.  (OOB680)
      4.  So I am finally in the rpms folder in the terminal and this happens when I try to alienate:
woody@WoodUB://media/storage/OOinstall/oob680/rpms$ sudo alien *.rpm Password:
Use of uninitialized value in die at /usr/share/perl5/Alien/Package/Deb.pm line 488, <GETPERMS> line 46.
Package build failed. Here's the log:
find: openoffice.org-base-2.0.2: No such file or directory
woody@WoodUB://media/storage/OOinstall/oob680/rpms$


sigh
Some days I think I picked the wrong career path.

Any ideas as to why alien keeps failing on me?

Thanks all.

---

### Post by MartinG on 2006-04-27
Try the following link instead of your number 2 (which is out of date):
[ftp://ftp.linux.cz/pub/localization/OpenOffice.org/latest/OOo_2.0.2_LinuxIntel_install_en-US_deb](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/latest/OOo_2.0.2_LinuxIntel_install_en-US_deb)

---

### Post by cjazz on 2006-04-27
[QUOTE=WoodyMahan]I am having a miserable time following the directions on Christoos post on upgrading OOo. [http://www.ubuntuforums.org/showthread.php?t=80392&highlight=howto+upgrade+openoffice](http://www.ubuntuforums.org/showthread.php?t=80392&highlight=howto+upgrade+openoffice)

1. deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./   
           This repository is gone.  I get errors anytime I try to add it to my sources.list

[/QUOTE]


This probably doesn't help you at all, but just for the record this repository  continues to work for me without errors.

---

### Post by christhemonkey on 2006-04-27
I got that error about the Package build failing and stuff when i tried to alien some rpms on my usbstick, to get it to work i had to move them all onto my computer in my home folder.

---

