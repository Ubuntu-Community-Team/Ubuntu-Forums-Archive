---
title: "Problem with Ubuntu 11.10"
date: 2011-11-09
forum: General Help
---

### Post by twuffysboy on 2011-11-09
Recently I upgraded from Ubuntu 11.04 to Ubuntu 11.10, however something seems to have gone wrong. Upon startup I receive the message "The disk drive for /dev/mapper/cryptswap1 is not yet ready or present. Continue to wait, or press s to skip mounting or M for manual recovery." Pressing M, or S does not fix this and it goes directly to the login screen. Also, none of the apps show up in the Dashboard. Clicking anything in the Dashboard does nothing. Whenever I attempt to open the software center a window appears and then quits within a matter of seconds. I have tried to install Ubuntu 11.04 again via a USB stick however when I reach the boot screen and select the USB drive it boots as normal into 11.10. Ideally I would like to find a way to downgrade to 11.04 again, however if anyone knows a way to fix this problem it would be much appreciated. Fixing it may be a problem as I can not access Terminal or software center. 
Thank you.

---

### Post by notgary on 2011-11-10
Unfortunately I can't help you with the disk mount problem, but as for downgrading, [this]("http://askubuntu.com/questions/5551/clean-install-from-ubuntu-10-04-to-lubuntu-10-10-without-losing-data/5627#5627") may be of help to you. One thing to bear in mind that with a downgrade, some of the application configuration data hidden away in your home directory may need to be manually deleted since some of them may refuse to use data that was created in a newer version of the program. I know for a fact that Miro is one such app, so you may have a bit of housekeeping when you complete the downgrade.

---

### Post by BillyBoa on 2011-11-10
> **twuffysboy said:**
> Recently I have tried to install Ubuntu 11.04 again via a USB stick however when I reach the boot screen and select the USB drive it boots as normal into 11.10. 
Thank you.
First you should format the /home directory to avoid the resurrection of 11.10.
Second with the USB installation sometimes you have problems because the .iso is corrupted during the attempts. So better use a CD.

---

