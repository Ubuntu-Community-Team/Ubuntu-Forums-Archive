---
title: "Rsync sh file don't work with cron"
date: 2011-03-25
forum: General Help
---

### Post by Ghost_Mazal on 2011-03-25
Lo Guys ,

I have a backup sh file that I have been using for a long time. It has always worked. 2 Days back I switched to a different pc and now suddenly the script don't work.

If I run it manually in the terminal it works. But when it execute with cron it doesn't copy any files to the backup destination. It starts but doesn't copy anything.

Can someone help me as to why it works manually but not with cron ?

```
#!/bin/bash
killall evolution
sleep 3
killall rainlendar2
sleep 3
rsync -a -v /home /media/Media_Drive/uebackup64
```

---

### Post by SeijiSensei on 2011-03-25
Does the script have a .sh extension?  [Debian-based distros won't run scripts with extensions from cron]("https://bugs.launchpad.net/ubuntu/+source/debianutils/+bug/38022").

---

### Post by Ghost_Mazal on 2011-03-25
Yes it has an .sh extension

---

### Post by CharlesA on 2011-03-25
How do you have it set up to run in cron? Using a crontab or putting it in /etc/cron.daily ?

---

### Post by SeijiSensei on 2011-03-25
> **Ghost_Mazal said:**
> Yes it has an .sh extension

Just remove it then. Rename it to "script" rather than "script.sh".  I bet this was running on a RedHat-flavored distro where this limitation doesn't apply.  It drove me crazy at first when a couple of scripts I had run on a CentOS box failed to work with Ubuntu.

*nix doesn't pay attention to file extensions the way Windows does.  For scripts, what matters is the top line "#!/bin/bash" which tells the OS which interpreter to use.

---

### Post by Ghost_Mazal on 2011-03-25
> **CharlesA said:**
> How do you have it set up to run in cron? Using a crontab or putting it in /etc/cron.daily ?

It is setup with my own crontab entry. (crontab -e)

> **SeijiSensei said:**
> Just remove it then. Rename it to "script" rather than "script.sh".  I bet this was running on a RedHat-flavored distro where this limitation doesn't apply.  It drove me crazy at first when a couple of scripts I had run on a CentOS box failed to work with Ubuntu.

*nix doesn't pay attention to file extensions the way Windows does.  For scripts, what matters is the top line "#!/bin/bash" which tells the OS which interpreter to use.

No that can't be it. The same script with the same name ran on this same version of Ubuntu on my previous machine without any problems.

I have searched through everything on here and kind find any thread that helps me as to why it suddenly isn't working

---

### Post by ajgreeny on 2011-03-25
I use lots of script.sh files to do things with cron and gnome-schedule without a problem, so I think the link about debian not being able to use .sh scripts must be incorrect for ubuntu.

---

### Post by CharlesA on 2011-03-25
> **ajgreeny said:**
> I use lots of script.sh files to do things with cron and gnome-schedule without a problem, so I think the link about debian not being able to use .sh scripts must be incorrect for ubuntu.
That only applies to files placed in /etc/cron.*

Does the script work fine if you run it manually?

---

### Post by Ghost_Mazal on 2011-03-26
> **CharlesA said:**
> That only applies to files placed in /etc/cron.*

Does the script work fine if you run it manually?

Yes when I tun it manually in the terminal it works 100%.

I have added some more commands to the script and now it gets really strage. The script executes and ALL the other commands work 100% , even the other 2 rsync commands. It is still just the first rsync command (the /home one) that doesn't work. It still doesn't copy the changed or added files to the backup destination.

```
#!/bin/bash
killall evolution
sleep 3
killall rainlendar2
sleep 3
rsync -a /home /media/Media_Drive/uebackup64
rsync -a /home/mazal/Documents/Linux_Docs/ /media/4D84-E758/Linux_Docs/homepc
rsync -a /var/www /media/Media_Drive/uebackup64/html
mysqldump --user=root --password=bluestreak achieve > /media/Media_Drive/uebackup64/mysql/achieve.sql
mysqldump --user=root --password=bluestreak flieks > /media/Media_Drive/uebackup64/mysql/flieks.sql
mysqldump --user=root --password=bluestreak groceries2 > /media/Media_Drive/uebackup64/mysql/groceries2.sql
mysqldump --user=root --password=bluestreak laprecords > /media/Media_Drive/uebackup64/mysql/laprecords.sql
mysqldump --user=root --password=bluestreak telefoonlys > /media/Media_Drive/uebackup64/mysql/telefoonlys.sql
```

---

### Post by dcstar on 2011-03-26
> **Ghost_Mazal said:**
> Yes when I tun it manually in the terminal it works 100%.

I have added some more commands to the script and now it gets really strage. The script executes and ALL the other commands work 100% , even the other 2 rsync commands. It is still just the first rsync command (the /home one) that doesn't work. It still doesn't copy the changed or added files to the backup destination.
.........

Running the script in a **user** shell may well be different to running it under cron.

What user is running the script?, does that user have full rights to the /home folder **and** the destination?

---

### Post by Ghost_Mazal on 2011-03-26
> **dcstar said:**
> Running the script in a **user** shell may well be different to running it under cron.

What user is running the script?, does that user have full rights to the /home folder **and** the destination?

My own user is running the script.(not root) It is in my crontab entry. (not root's)
And yes I do have full rights to my home folder and the destination. Rsync job 3 runs to the same destination without problems.

Just to make sure the problem is not at destination side I have re-partitioned and formatted the destination drive (external hdd) and are busy putting back my data to it before I can test after the format. Will let you guys know if that worked or not. (600gig of data that must get back onto the drive first so will be much later)

---

### Post by dcstar on 2011-03-26
> **Ghost_Mazal said:**
> My own user is running the script.(not root) It is in my crontab entry. (not root's)
And yes I do have full rights to my home folder and the destination. Rsync job 3 runs to the same destination without problems.


Move that first rsync to the end of the others and see if it still fails.

---

### Post by Ghost_Mazal on 2011-03-26
Ok eventually all my data is back after the partition and reformat. tested it now again and now it works.

So the repartitioning and format of the destination has worked.

Still don't know why it happened , but it's working now.

---

