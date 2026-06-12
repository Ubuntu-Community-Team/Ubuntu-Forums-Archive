---
title: "simple-scan segmentation fault"
date: 2010-06-13
forum: General Help
---

### Post by dinofelis on 2010-06-13
I have a problem with simple-scan.

I'm using Lucid on a 64-bit desktop, and I installed the UnifiedLinuxDriver from Samsung for my printer-scanner.  The printer works all right, but when I launch simple-scan now (it used to launch before the installation, but the scanner was not known), I obtain:

```

patrick@ACER-SALON:~$ simple-scan -d
** (simple-scan:2247): DEBUG: Starting Simple Scan 1.0.3, PID=2247
** (simple-scan:2247): DEBUG: Restoring window to 600x400 pixels
** (simple-scan:2247): DEBUG: sane_init () -> SANE_STATUS_GOOD
** (simple-scan:2247): DEBUG: SANE version 1.0.20
** (simple-scan:2247): DEBUG: Requesting redetection of scan devices
** (simple-scan:2247): DEBUG: Processing request
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Error inserting parport_pc (/lib/modules/2.6.32-22-generic/kernel/drivers/parport/parport_pc.ko): Operation not permitted
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
Segmentation fault


```

Any suggestions ?

thanks.

---

### Post by mickub on 2010-06-14
Hi dinofelis,
I'm using Lucid 32-bit and also installed the UnifiedLinuxDriver from Samsung for my printer, and noticed that simple-scan nor xsane will start in normal user-mode. 
If I started as root '$ sudo simple-scan' the program started, so I think there is a permission problem, but I couldn't figure out where. (Segmentation fault)

In the code from the '$ simple-scan -d'  we had information about the  /etc/modprobe.conf-file that explain that there shall not be any such file any longer, all config files shall be in the /etc/modprobe.d-directory.

Now I have uninstalled the Samsung UnifiedLinuxDriver and the scanner  program work in normal user-mode again.

No help but confirming your problems...

---

