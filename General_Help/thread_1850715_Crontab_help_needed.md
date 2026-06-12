---
title: "Crontab help needed"
date: 2011-09-27
forum: General Help
---

### Post by egrimisu on 2011-09-27
Hi guys,

i have added a cron job using crontab -e and i want that every saturday night at 21:00 a script to run, so i have added the folowing line:
```

# Misu WakeOnLan
0 21 * * 5 /etc/backuppc/wolmisu.sh

```
and the error logs:
```

Sep 24 21:00:01 BackupPC CRON[14196]: (myuser) CMD (etherwake 00:16:e6:35:cx:xx # JOB_ID_1) 
Sep 24 21:00:01 BackupPC CRON[14194]: (CRON) error (grandchild #14196 failed with exit status 127)
Sep 24 21:00:02 BackupPC postfix/pickup[14140]: 0573D30A0396: uid=1000 from=<myuser>

```
The strange thing is that the folowing mac : [noparse]00:16:e6:35:cx:xx[/noparse] is not present in wolmisu.sh script but is present in the ethers file located in /etc/ 

shall i empty ethers and try again?

---

### Post by egrimisu on 2011-09-28
> **zackwasa said:**
> try changing the cronjob to:
```

0 21 * * 5 cd /etc/backuppc; ./wolmisu.sh

```

Hi, i have done that replace day 5 with 2 to run tusday night(last night) and here we are:

Sep 27 21:00:01 BackupPC CRON[3360]: (root) CMD (cd /etc/backuppc; ./wolmisu.sh)
Sep 27 21:00:01 BackupPC CRON[3358]: (CRON) error (grandchild #3360 failed with exit status 127)

the content of wolmisu.sh:

#!/bin/bash

#CORATREND
#or-dornerlorand
etherwake 00:11:2f:b1:xx:xx

#DEPOZIT
#Or-Fact-Depozit
etherwake 00:10:5c:dc:xx:xx

#RELATII CLIENTI
#Or-SteflikGhizela
etherwake 00:15:58:9a:xx:xx
#Or-VisoiuAdriana
etherwake 00:10:5c:f1:xx:xx
#Or-ArdeleanCrina
etherwake 00:10:5c:dc:xx:xx
#Or-ZetenyiLaszlo
etherwake 00:10:5c:dc:xx:xx
#Or-CserRozalia
etherwake 00:10:5c:e6:xx:xx
#Or-DobosCamelia
etherwake 00:1a:4d:8c:xx:xx

#LOGISTICA
#Or-SacuiMiha
etherwake 00:12:3f:7d:xx:xx
#Or-RaducanuOana
etherwake 00:1e:33:04:xx:xx
etherwake 00:16:44:9b:xx:xx
#Or-MosIldiko
etherwake 00:1a:4d:77:xx:xx
#Or-BalintffyEduard

---

