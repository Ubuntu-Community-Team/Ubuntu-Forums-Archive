---
title: "Ubuntu grub after windows doesm't work"
date: 2010-07-23
forum: General Help
---

### Post by JCM_Pico on 2010-07-23
Hello there,
I recently installed win7 in a small partition just for playing some games, then I reinstalled the Ubuntu grub from a live cd, with out any problem (I followed the tutorial from the ubuntu community [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) ). But after the reboot, ubuntu starts with out appearing the OS selection.
Does any body know how can I solve this

Thank you

---

### Post by drs305 on 2010-07-23
Try opening up /etc/default/grub and make sure this line has a # symbol at the start of the line.
Open the file:
```
gksu gedit /etc/default/grub
```
Make sure these lines look like this:
> #GRUB_HIDDEN_TIMEOUT=0
GRUB_TIMEOUT=10

You can change the 10 to a lower value if desired. 10 = 10 seconds.

Save the file and update-grub:
```
sudo update-grub
```
Reboot and see if the menu now appears.

Running the update-grub command should also find the Windows OS and place it in your menu.

If Grub2's menu still doesn't display, you may be able to see it by holding down the SHIFT key as the system first starts to boot.

---

### Post by JCM_Pico on 2010-07-23
Thank you very much, it work.  It was very simple


> **drs305 said:**
> Try opening up /etc/default/grub and make sure this line has a # symbol at the start of the line.
Open the file:
```
gksu gedit /etc/default/grub
```Make sure these lines look like this:

You can change the 10 to a lower value if desired. 10 = 10 seconds.

Save the file and update-grub:
```
sudo update-grub
```Reboot and see if the menu now appears.

Running the update-grub command should also find the Windows OS and place it in your menu.

If Grub2's menu still doesn't display, you may be able to see it by holding down the SHIFT key as the system first starts to boot.

---

