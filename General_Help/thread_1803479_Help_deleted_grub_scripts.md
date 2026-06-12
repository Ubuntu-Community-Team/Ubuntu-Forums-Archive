---
title: "Help deleted grub scripts"
date: 2011-07-13
forum: General Help
---

### Post by dschlic1 on 2011-07-13
I just upgraded to 11.4 and was trying to rearrange the GRUB menu. I have a dual boot system, Windows 7 and Ubuntu. I accidently deleted the script files in /etc/grub.d and haven't been able to get them back. I have tried to uninstall and re-install GRUB2 with no joy. Other then no script files it appears that everything works. Can some one point me to where I can get these script files.

---

### Post by sisco311 on 2011-07-13
You have to find out which packages have files installed in /etc/grub.d
```
dpkg -S /etc/grub.d
```

Then reinstall them:
```
sudo apt-get --reinstall install **packages**
```

---

### Post by seawolf167 on 2011-07-13
Just to check - are you sure you reinstalled Grub2 correctly? [Here ]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")are a couple methods for re-installation. If it is all correctly installed, take a look at sisco311's post for the specific package re-installation

---

