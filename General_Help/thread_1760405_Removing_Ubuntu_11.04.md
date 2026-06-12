---
title: "Removing Ubuntu 11.04"
date: 2011-05-16
forum: General Help
---

### Post by Mudi_ on 2011-05-16
Hi guys is there a way I can safely remove Ubuntu 11.04 64-bit? If you can guide me or point me to some step by step instructions I'd appreciate it. Thanks in advance.

---

### Post by Rubi1200 on 2011-05-17
How did you install in the first place? On a separate partition or **inside **Windows with Wubi?

Your answer determines our response.

Thanks.

---

### Post by Mudi_ on 2011-05-18
> **Rubi1200 said:**
> How did you install in the first place? On a separate partition or **inside **Windows with Wubi?

Your answer determines our response.

Thanks.

Sorry for the late reply, but I installed it inside windows.

---

### Post by Rubi1200 on 2011-05-18
You can use the instructions here to remove the Wubi install:
[https://wiki.edubuntu.org/WubiGuide#Uninstallation](https://wiki.edubuntu.org/WubiGuide#Uninstallation)

---

### Post by Mudi_ on 2011-05-18
Been there, done that, none of the ways work. There is no ubuntu-uninstall.exe, nor is it in the add/remove programs list. Also I tried using the CD but it doesn't give me an uninstall option. I used the CD to install 10.10 but I currently have 11.04, is that the problem?

---

### Post by Rubi1200 on 2011-05-18
There is also a link under the first image for the uninstall utility:
 [Uninstall-Ubuntu.exe]("https://wiki.edubuntu.org/WubiGuide?action=AttachFile&do=view&target=Uninstall-Ubuntu.exe")

Did you try the instructions to manually remove Wubi including removing registry entries?

Let me know what happens.

I don't think having the 11.04 CD would be the problem here.

---

### Post by Mudi_ on 2011-05-18
> **Rubi1200 said:**
> There is also a link under the first image for the uninstall utility:
 [Uninstall-Ubuntu.exe]("https://wiki.edubuntu.org/WubiGuide?action=AttachFile&do=view&target=Uninstall-Ubuntu.exe")

Did you try the instructions to manually remove Wubi including removing registry entries?

Let me know what happens.

I don't think having the 11.04 CD would be the problem here.

Ok I tried it, and it said WUBI has been uninstalled after it was done but the removal only took a few seconds. I rebooted by computer and the Ubuntu partition was still there, so I went on it and got this error:

Try (hd0,0): NTFS 5: No wubildr
Try (hd0,1): FAT 32: No WUBILDR
Try (hd0,2): invalid or null
Try (hd0,3): invalid or null
Try (fd0): invalid or null
Error: cannot find GRLDR in all devices. Press CTRL+ALT+DEL to restart.

---

### Post by Rubi1200 on 2011-05-19
I suspect the Wubi install has been removed but not the boot entry for it.

Depending on which version of Windows you are using, you need to edit the files according to these instructions:
> In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line. For Vista, you can use EasyBCD to edit the boot menu. Alternatively you can modify the boot menu via Control Panel > System > Advanced > Startup and Recovery and pressing "Edit".
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

