---
title: "Failed backup attempt? or failing hard drive? Some advice or help please."
date: 2010-01-05
forum: General Help
---

### Post by Silvain on 2010-01-05
I made an attempt to backup my system (karmic koala) using this routine.
cd /
then

sudo tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

The process of backup went on for a very long time, which is probably normal. On returning to the computer in the morning, it was in suspend mode and would not power on via the usual method,tapping power button. So then I used the reset button, and after booting up a message appears on the top right that reports "Install problem! The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator."

 Is there something wrong with the  statement that was used for backing up the system? 
Also when I attempt to login it does not work now either, it eventually returns to the login user selection.

So is there a possibility the backup finished and then there may be a chance the system can be restored from the backup file?

I have tried booting up with a live cd and could use some advice on how to navigate with terminal to root of the system and see if the backup file exist even, have been unable to get to the root folder(where the backup would be) with the GUI method via live cd.

TIA,
Silvain

P.S. I have tried logging in with Xterm session and still cannot get into the system that way either.

---

### Post by Silvain on 2010-01-20
I gave up on fixing this sytem, ran gparted to delete all old partitions then did format and reloaded windowsxp operating system.

---

