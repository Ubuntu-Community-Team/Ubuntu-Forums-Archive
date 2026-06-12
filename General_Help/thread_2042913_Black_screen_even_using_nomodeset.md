---
title: "Black screen even using nomodeset"
date: 2012-08-15
forum: General Help
---

### Post by syndicate0017 on 2012-08-15
I've been using ubuntu on my laptop for several months. I recently acquired a desktop and decided to put ubuntu on there. After the install, I loaded the Nvidia proprietary drivers and received a black screen. I've heard of this problem before so I simply set it to nomodeset and STILL won't boot. I booted to recovery and edited the grub line to "quiet splash nomodeset acpi_osi=Linux" and it booted! I logged out and logged back in several times to make sure that this was the configuration I needed. The X server started every time. Ready for the weird part? Even after:

```
sudo nano /etc/default/grub
```

And editing the line to "quiet splash nomodeset acpi_osi=Linux" and performing 

```
 sudo update-grub 
```

The X server won't start since I restarted it. Black screen and the monitor goes to sleep. I then booted back into grub and (performing nearly identical steps) edited the line to "nomodeset acpi_osi=Linux xforcevesa" and it booted! Yet again, after editing the /etc/default/grub file and updating grub, it fails to boot after a restart. I'm honestly lost and don't understand how that makes sense at all. I tried looking for my problem for well over an hour before posting and unfortunately couldn't come across my exact situation. I would appreciate any and all help.

And to further eliminate some solutions...I removed my Xorg.conf (since it seemed faulty) and regenerated a new one using

```
 nvidia-xconfig 
```

Immediately after doing so, it booted. To test the solution, I rebooted again, and it immediately hung on the black screen. I then went into recovery and removed xforcevesa from the line and it booted...this really makes no sense to me since it black screened again after another reboot.

---

### Post by syndicate0017 on 2012-08-16
Bump

---

### Post by syndicate0017 on 2012-08-17
Well, it's not really solved but the problem isn't there any more. Simply gave up on Ubuntu and went to Lubuntu just to see if it would work. I installed the x64 Lubuntu and installed the proprietary drivers without error. I had been installing the x86 version of Ubuntu and since my computer is AMD, that might have something to do with it, but I doubt it. At any rate, my desktop is up and running. I'll mark this thread "solved".

---

### Post by fromagegb on 2012-10-06
I don't think giving up is solved!

I had big problems with AMD A83870 APU (no graphics card) getting booted only after about 5 to 10 retries, and nomodeset fixed that.  The trouble then was although it booted, I had only unity 2D with the giant icons and not the shrinkable unity 3D.  I have now installed the recommended AMD driver from the AMD site (installed by downloading a .run file from AMD and double clicking in nautilus) and now it works first time every time in unity 3D, recognising my samsung monitor when previously it just gave "laptop".  So the driver works, and it does help.

Incidentally, I have never had a nvidia driver or whatever xorg is.

---

