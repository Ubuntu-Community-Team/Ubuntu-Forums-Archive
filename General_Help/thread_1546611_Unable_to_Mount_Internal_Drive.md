---
title: "Unable to Mount Internal Drive"
date: 2010-08-05
forum: General Help
---

### Post by gcndavidmn on 2010-08-05
I have 2 internal drives. One is for the OS and one is for the Data. I tried to get the Data drive to mount automatically at login using some crap I found on a linux blog. Safe to say it didn't work and now I can't mount it with the OS on the OS Drive. It mounts from a live CD and all the data is perfectly safe. When I try to mount the drive I get this error message:
"Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb1 on /media/data"

What have I done wrong and how can I make it mount again? Preferably this time at login.

---

### Post by ajgreeny on 2010-08-05
Can you let us see the output of ```
sudo blkid
sudo fdisk -l
cat etc/fstab
``` entered in terminal one line at a time.

---

### Post by gcndavidmn on 2010-08-05
Sorry, just sorted this issue by playing with fstab. Marvelous these things called 'friends'.

---

