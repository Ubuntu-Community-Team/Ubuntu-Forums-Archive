---
title: "Crontab Permissions"
date: 2011-04-17
forum: General Help
---

### Post by RadiusD on 2011-04-17
Hello I am trying to setup a crontab that will do a mysqldump into a file on a different backup server. My command works perfectly in terminal but crontab returns a permission denied error when it tries to create the file on the backup server. How do I give crontab all the permissions that terminal normally has? Thank You.

---

### Post by blueridgedog on 2011-04-17
Did you create it in the system crontab (runs as root) or in your crontab (runs as you)?

---

### Post by RadiusD on 2011-04-18
i tried it in both and neither worked.

---

### Post by Ghost_Mazal on 2011-04-18
Is it an executable script with the mysqldump command in that you are trying to run with crontab ?

---

### Post by blueridgedog on 2011-04-18
> **RadiusD said:**
> i tried it in both and neither worked.

When you run it from the command line it works, but in your crontab it has permissions issues.  How did you determine that it was permissions issues?  

Can you try specifying user credentials in the script?

Is every element of your paths in the script referenced by an absolute path?

---

### Post by RadiusD on 2011-04-18
> **Ghost_Mazal said:**
> Is it an executable script with the  mysqldump command in that you are trying to run with crontab ?

yes the script is executable.

> **blueridgedog said:**
> When you run it from the command line it works, but in your crontab it has permissions issues.  How did you determine that it was permissions issues?  

Can you try specifying user credentials in the script?

Is every element of your paths in the script referenced by an absolute path?

So I have a .sh script located on my desktop.

Here are its general contents.

#!/bin/bash

mysqldump -uroot -pmypass radius > /home/server/.gvfs/shared\ on\ backupserverip/SQL\ Backup/`date +\%m-\%d-\%Y`-backup.sql

Then in my crontab (running as root)

15 9 * * * /home/server/Desktop/scripts/sqlbackup.sh >> /home/server/Desktop/scripts/cronerrors.log 2>&1

---

### Post by SeijiSensei on 2011-04-18
> **RadiusD said:**
> Then in my crontab (running as root)

15 9 * * * /home/server/Desktop/scripts/sqlbackup.sh >> /home/server/Desktop/scripts/cronerrors.log 2>&1

What do you mean "my crontab (running as root)?"

There are two crontab files that run with root privileges.  One is /etc/crontab, the other is /var/spool/cron/root.  Are you using one of these? 

If you're running the file from /etc/cron.daily/, you need to remove the .sh from the script's filename.  This is [an Ubuntu/Debian issue]("https://bugs.launchpad.net/ubuntu/+source/debianutils/+bug/38022").

---

### Post by RadiusD on 2011-04-18
When I run crontab I first do 
>> sudo su

and then 
>> crontab -e

is that not the proper way to run crontab?

---

### Post by blueridgedog on 2011-04-18
So, if you become root (since that is the user you are using to run the script), what happens when you run it that way?

```
sudo su
/home/server/Desktop/scripts/sqlbackup.sh
```

Could the script be owned by you, execuatable by you, but not executable by "others" which root would be one of?

Try (as you):

```
chmod 711 /home/server/Desktop/scripts/sqlbackup.sh
```

That will make the file fully accessible to you, but executable to others.


More errors would help determine what is working.  Is there anything in the logs of the server?

---

### Post by RadiusD on 2011-04-18
Thanks blueridgedog__ looks like I got it. It was a stupid error on my part. When I ran sudo su and tried to execute the script I got the same error. 

I then noticed that when I ran crontab from the logged in user I used sudo to run it. So I was always in the root crontab. I opened the crontab as the user and it worked perfectly. 

Thanks a lot for everyones help. Ubuntu has an awesome community.

---

