---
title: "Cannot uninstall Ubuntu please help"
date: 2011-07-30
forum: General Help
---

### Post by arronbartle on 2011-07-30
Hey guys, It will not let me uninstall Ubuntu, please can someone help? it comes up with error report : 

An error occured:

The file or directory is corrupted and unreadable removing C:\ubuntu

for more information, please see the log file c\docume~....

thanks, Arron.




also not sure if you guys can help, but when i rebooted my computer with xp, I seemed to replace everything but I still have 110gb / 240gb used memory?

---

### Post by arronbartle on 2011-07-30
bump

---

### Post by grahammechanical on 2011-07-30
May I suggest that you look through the Wubi mega thread sticky at the top of the section?

As a guess, it seems to me that you have removed Ubuntu but not removed Wubi from Windows. It is still there taking up the space that you allocated to it when you installed Ubuntu using Wubi in Windows. I cannot advise how to uninstall Wubi. Perhaps using Add/Remove programs? This is just a guess.

Regards.

P.S. Do not expect instant replies to your posts. It is customary to allow 24 hours for someone to help before bumping.

---

### Post by bcbc on 2011-07-30
You need to run chkdsk if the \ubuntu directory is corrupted.

go to My computer, right click on C:, Properties, Tools, check disk for errors, click on Fix automatically. Since it's on the C: drive it will tell you it needs to schedule it for the next boot. Accept, and reboot and let it complete. 

Then check [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation) for all uninstallation instructions.

---

