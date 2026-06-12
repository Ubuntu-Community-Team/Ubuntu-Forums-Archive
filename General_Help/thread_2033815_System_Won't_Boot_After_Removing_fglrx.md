---
title: "System Won't Boot After Removing fglrx"
date: 2012-07-27
forum: General Help
---

### Post by Xplorer4x4 on 2012-07-27
I installed the latest drivers from the amd site,  and wanted to revert to the xorg drivers. I removed fglrx using apt rather then the uninstaller provided with the drivers and after trying to reboot the system won't load KDE. I can access rescue mode, but not sure where to go from here.

---

### Post by Xplorer4x4 on 2012-07-27
Not sure if it helps but here is the out put from boot-repair: [http://paste.ubuntu.com/1113275/](http://paste.ubuntu.com/1113275/)

---

### Post by robtygart on 2012-07-27
Will it load to the login screen? 

If so, one of the buttons (Depending on your login theme) will allow you to log in in Failsafe mode.  

If it loads download your drivers, then log out and change your login back to normal graphics, then sing in...

---

### Post by Xplorer4x4 on 2012-07-27
Thats a negative on the log in screen. Right before the log in would usually show,  my monitor button turns from green to orange as if it went to sleep. I have tried to update grub from cli and tried the boot-repair app. Niether fixed. I also tried booting previous kernels from grub but no luck.

---

### Post by Lyfang on 2012-07-27
I don't know if this would work: Boot into GRUB Recovery Mode "(recovery mode)" & find the uninstaller:
```
sudo /usr/share/ati/fglrx-uninstall.sh
```

---

### Post by Xplorer4x4 on 2012-07-27
says the file system is read only. I assume it needs to be mounted, but I am not familiar with the mount command.

---

### Post by Xplorer4x4 on 2012-07-27
i found this command. ```
 mount -o remount,rw /
``` fixed the read only issue. I tried to run the uninstaller, but it failed. I checked the log it referenced and it didnt like that some of the files had been removed so I had to use ```
 sudo /usr/share/ati/fglrx-uninstall.sh.--force
``` and it said I could check the log for details. At the end of the log it says it reverted to the old configuration and system boots fine now! Thanks!

---

### Post by Lyfang on 2012-07-27
You're Welcome! I filed a bug report: [Unable to remove fglrx AMD driver properly using apt]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1029898")

---

### Post by Xplorer4x4 on 2012-07-27
> **Lyfang said:**
> You're Welcome! I filed a bug report: [Unable to remove fglrx AMD driver properly using apt]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1029898")

thanks, I will try to keep an eye on the bug and see if there is anything more I can contribute to help it get fixed.

---

### Post by QIII on 2012-07-27
For future reference...

When you install from the AMD website and use their wizard, do this to uninstall:

```
sudo aticonfig --uninstall
```

---

### Post by Xplorer4x4 on 2012-07-27
> **QIII said:**
> For future reference...

When you install from the AMD website and use their wizard, do this to uninstall:

```
sudo aticonfig --uninstall
```

Thanks but I kinda figured that out the hard way.

---

### Post by deadflowr on 2012-07-27
This link will give you the commands to purge and reinstall the open source drivers.

[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

Scroll down to Problem:need to purge -fgrlx

---

### Post by Xplorer4x4 on 2012-07-27
> **deadflowr said:**
> This link will give you the commands to purge and reinstall the open source drivers.

[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

Scroll down to Problem:need to purge -fgrlx

Thanks but problem solved already. AMDs driver restores the previous config.

---

