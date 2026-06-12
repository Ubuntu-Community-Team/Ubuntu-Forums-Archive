---
title: "Ubuntu 10.04 problem after trying backup software"
date: 2010-10-21
forum: General Help
---

### Post by vishnumrao on 2010-10-21
I tried sbackup and luckybackup on my 10.04 desktop install yesterday. I was trying to backup stuff to my DNS323 by using the ssh (or sftp) method in both the backup software. In both the cases since I was just playing around to see which backup method I liked, I interrupted the backup after a few minutes. I was using the default recommended backup directories in both cases.

Problem: After interrupting the backups, I was getting some error messages about not being able to find config files to become super user etc. I had to reboot and when the desktop came back to the login screen, It would default to, I think, a failsafe login. But the login fails and takes me to a text login. 

At this point, I did not suspect my backup programs were the culprits for the problems. Next I chose an older kernel and was able to login successfully as all looked normal. Naively, I repeated my mistakes of running the backups and interrupting them. Now I have no more good login options. 

Can someone help me understand what is the problem and a solution?

---

### Post by vishnumrao on 2010-11-03
Update: Solved. I googled up the error that I was getting and deleted the /var/backup directory where the backup was being created by human error. I thought I was backing up to the NAS, but I was doing to /var/backup. Deleting the backups fixed it.

---

