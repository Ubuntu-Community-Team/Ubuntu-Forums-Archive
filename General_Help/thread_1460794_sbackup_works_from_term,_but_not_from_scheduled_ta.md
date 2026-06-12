---
title: "sbackup works from term, but not from scheduled task"
date: 2010-04-23
forum: General Help
---

### Post by 98cwitr on 2010-04-23
Had worked fine until I installed updates from the 9thish on 10.04. I click on Backup Now in the GUI and it starts the process and in System Monitor the process is listed as Zombie and n/a memory usage, then it terminates. From terminal though, it works fine. What gives? I have sbackup scheduled to run incrementals once a week, but no joy.

---

### Post by 98cwitr on 2010-04-26
tried to run a restore on a new image yesterday, not only did it take FOREVER to restore, it really didnt do what I thought it was going to do. I couldnt get APTonCD to work like I had imagined either. 

This was a 9.10 image on 10.04 backups though...so I'll lay a fresh 10.04 install down and see what happens. 

Is there one app that will backup my entire machine? Including all the settings in /etc?

---

### Post by SSP6007 on 2010-05-07
Not sure I'm in the right spot, but I have not been able to get sbackup to run since upgrading to 10.04. After 24 hours and being unable to unmount the ext. hd I wanted to backup to, I just shut down. Any suggestion would be welcome. Not having a backup is making me nervous. Thanks.

---

### Post by 98cwitr on 2010-05-10
it's working now...i think it was due to when I upograded, my external drive got an underscore appended to it...sbackup couldnt see the mount.

---

