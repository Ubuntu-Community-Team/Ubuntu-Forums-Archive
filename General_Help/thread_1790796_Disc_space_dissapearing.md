---
title: "Disc space dissapearing"
date: 2011-06-25
forum: General Help
---

### Post by tombeard on 2011-06-25
I am running 64 bit Lenny on an AMD processor. My root partition is 500GB. The system reported I was down to 1.7GB so I moved files to another partition till I had 25% (125GB) free. Next morning when I checked my drive was full again. I had email(none received) and a browser open but nothing should have consumed any storage. I used touch forcefsck and fsck ran w/o problems when I rebooted. I can boot to a shell with the recovery kernel but I can't run a desktop. 

Can anyone explain where my disc space went and if there is any option besides dd to a new drive?

---

### Post by Abir Valg on 2011-06-25
Could you run a tool called baobab and tell us of your findings?

---

### Post by tombeard on 2011-06-25
> **Abir Valg said:**
> Could you run a tool called baobab and tell us of your findings?

Baobab is not installed and won't install with apt-get. The message refers to gnome-utils but no luck with that. Before I rebooted to run fsck the Disk Usage Analyzer showed most of the files in my home folder, but it was reporting the drive full at something like 148GB after I umounted all the other drives, which is what prompted me to run fsck. I can't get to a desktop to run that now. df reports 100% in use at 474781296 blocks on sdb1.

---

### Post by hsweet on 2011-06-25
Check your log files. I had an overheating computer (loose cpu fan) that filled up the whole disk with warnings once.

Look at the file sizes in /var/log and if you see a hugemongous one, see if you have 5x10^12 repetitious messages.

---

### Post by Abir Valg on 2011-06-25
Try ncdu - terminal based disk usage analyzer.

---

### Post by tombeard on 2011-06-25
I added up the results of du on the root folders. Home,lib,usr and var were largest, contributing 126.8GB. du reports /media at 327GB and ncdu reports the same. /media was where I mounted the folder I moved files to yesterday. The above results were with all partitions except / umounted and ls shows no files in /media. If it helps know that I started moving files to /media/Home2 using natilus but stopped that when the files were taking 40-60 seconds each and with 95,000 files it would have taken 2 months. I used mv from a terminal to move the excess files from my home to /media/Home2 which freed up 25% of the drive, per System Monitor.

---

### Post by tombeard on 2011-06-25
> **Abir Valg said:**
> Try ncdu - terminal based disk usage analyzer.

Success! Thanks Abir, ncdu pointed the way. Moving the files triggered a full system backup. For some reason (more looking for me) backup stuck the full backup files in /media/backup instead of the external drive that was supposed to be mounted there. I sincerely appreciate your help, I have learned many things today.

---

### Post by Abir Valg on 2011-06-25
Kudos to ncdu developers.
BTW. I just compared ncdu and baobab speeds in processing my home directory -
ncdu was like 2 secs, whereas baobab took 20 secs.

---

### Post by tombeard on 2011-06-25
> **Abir Valg said:**
> Kudos to ncdu developers.
BTW. I just compared ncdu and baobab speeds in processing my home directory -
ncdu was like 2 secs, whereas baobab took 20 secs.

FWIW, it was apparently backup that caused the low disc error in the first place. I wasted a lot of time moving those files unnecessarily. I (just now) set a switch in backup so it no longer writes backups if the designated device is unavailable. Live and learn. Thanks again. I have a new tool if this happens again.

---

