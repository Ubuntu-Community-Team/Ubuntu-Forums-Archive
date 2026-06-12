---
title: "Ubuntu 10.04 problem."
date: 2010-05-14
forum: General Help
---

### Post by manji_kun on 2010-05-14
I don't know if it's jsut me, like if i did something stupid, or if it's the "Upgrade" but today my upgrade manager told me "Ubuntu 10.04 is out!" and asked me if i wanted to upgrade to it, i said sure and began the download, it seemed to go just as fast (or slow) as any other OS i installed.

After a few minutes of watching the progress bar, i had to leave, a few hours later i came back and the install was done, saying that 9 files were deleted, i figured this was due to the new OS replacing them so i hit reboot.

now i get 

> Gave up waiting for rot device.        Common Problems: 76523acda04   
  - Boot args  (cat /proc/cmdline)
  - Check root= (did the system wait for the right device?)
-Missing modules (cat/proc/modules; Is /dev)
ALERT! /dev/disk/by-uuid/9b2022ef-8a17-4429-b64d-676523acda04 does not exist. Dropping to a shell!


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
 Did i do anything wrong by letting it auto load? or did i perhaps get a fake "upgrade" with this?

---

### Post by manji_kun on 2010-05-14
90 files, not 9, sorry for the typo.

---

### Post by paydaydaddy on 2010-05-14
do you know how to get into the recovery console during boot?
If so, try recovery. If not post back for more help.

---

### Post by manji_kun on 2010-05-14
it gets to the BIOS screen, then straight to this error.

---

### Post by elra92 on 2010-05-16
I just upgraded from Karmic and I am getting the same error message. I tried booting in recovery mode and got the same error message again after several minutes.

---

### Post by techunit on 2010-05-16
Alright well I hate having tell people this but upgrade often fail especially if they are done through the update manager... A clean install can help. I would recommend you boot from the live cd and see if you can recover anything from your hard drive. After that then you should finish the clean install. Um Hope this helps.

---

