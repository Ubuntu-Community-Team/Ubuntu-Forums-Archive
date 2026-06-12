---
title: "Broken Karmic System"
date: 2009-12-06
forum: General Help
---

### Post by ChrisB111 on 2009-12-06
I recently upgraded to ubuntu karmic from jaunty, I booted my system, it ran ok but then it hung, I restarted but since then it has never came back up properly. I've tried booting it a few times since then and it either, does a disk check then restarts, randomly restarts, shows a black screen with a mouse and a grey rectangle in the center. I have never reached the login screen. I tried using a jaunty iso to check the file system but gparted didn't say much and the report it gave wasn't very helpful (to me that is, someone who knows nothing about file systems or linux). The report is attached as a .txt file, rename as .htm to view.

Does anyone have any advice/help/pointers?, I don't want to go through all the trouble of reinstalling my system. I know I haven't been very helpful on the information front but if you need any more info just ask. 

System Info: 
 - 32 bit
 - NVidia Graphics Card
 - Root partition on a external usb hard drive

Thanks,

Chris

---

### Post by ChrisB111 on 2009-12-10
I think the problem might be to do with the login screen. I think I can get it to boot in to a root terminal, is there a command I can use to reinstall the packages used by the login manager?

Thanks,

Chris

---

### Post by ChrisB111 on 2009-12-11
My system is now up and running again, not sure what fixed it, booted up in safe mode and ran ```
apt-get install --reinstall gdm
``` and ```
apt-get dist-upgrade
``` in an attempt to fix the system, but something seams to have worked.

Chris

---

### Post by annabels on 2009-12-11
I think you have a typo and the 2nd line should read:
```
apt-get dist-upgrade
```
 
Unfortunately this still didn't solve my problem :(

---

### Post by 4Orbs on 2009-12-11
From what I have experienced, dist-upgrades don't always work well if the nvidia driver is still activated when the upgrade is initiated. Now, before I do an upgrade I first deactivate the nvidia driver, then set screen resolution back to default or auto, then run the upgrade, then after the upgrade and updates are completed, reactivate the nvidia driver. This may not be necessary in many cases, but I have found it to be the most reliable way to achieve a good upgrade.

If the proprietary driver happens to be the cause of your problems, you might be able to get back your desktop by removing the xorg.conf file. If you can login to recovery try this. First copy the problematic xorg.conf file to a different name as a backup:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.borked
```
Then remove the xorg.conf that you just copied:
```
sudo rm /etc/X11/xorg.conf
```
Then you should be able to reboot and get to the login screen (which won't be at your preferred resolution anymore). Then you can try reactivating the proprietary driver, which will write a new xorg.conf that should work now.

---

### Post by ChrisB111 on 2009-12-13
Apparently my fix only works for one session, I have booted up, got the black screen with a grey box, fixed the system (by booting to safe mode and reinstalling the gdm), booted ubuntu normally, used ubuntu and shutdown, several times now. It seams that the problem is in the gdm but I have no idea how to diagnose and fix it. Can anyone please help?

I have attached my attempt in gimp at drawing my login screen.

Chris

---

### Post by ChrisB111 on 2010-01-24
I tried the fix given by 4Orbs and it worked for a few boots, I re-enabled the nvidia drivers and only booted using to recovery mode, to launch the gdm manually using: ***gdm --debug*** to see if I could get some useful output, however it gives absolutely none. I have tried reinstalling it. The gdm does work with the nvidia drivers as I had them enabled when booting however this doesn't help much. Any ideas anyone?

Chris

---

### Post by luffy_chan_19 on 2010-01-24
i have one suggestion see if this works. try to press esc button right after the boot selector screen. i have a similar problem, and this seems to bypass a couple of the beginging stages of boot to the login screen

---

