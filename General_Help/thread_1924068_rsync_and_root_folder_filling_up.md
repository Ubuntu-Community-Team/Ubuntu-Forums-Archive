---
title: "rsync and root folder filling up?"
date: 2012-02-11
forum: General Help
---

### Post by nslegacy163 on 2012-02-11
Hi gang, 

 Here's the plan I ran: Last night I wanted to copy my files (79GB) from one external drive to another using rsync strictly for backup. Then I thought it would be rad to make this an automated cron job. Did some light reading on how to make it all happen and made it happen. 

 Here was the problem: It worked well until I woke up this morning, letting it run all night. The sync didn't complete which was disappointing but I could always run it again. But when I rebooted my computer I received an error "**INSTALL PROBLEM!** The configuration defaults for GNOME Power Manager have no been installed correctly...." Which I read up on and fixed fine. Turned out my OS disk drive for Ubuntu was full! I think it had everything to do with my rsync. The directory was full of a 1TBBACKUP (which you'll see below in my command, is the destination dir).

Here is my question: This is my command for the sync: ```
sudo rsync -azvu --include=".*" --exclude="/*/.gvfs" /media/FileShare/MyDocuments /media/1TBBACKUP
``` 
 I think I remember there being a "delete" option but I didn't throw it in the command because I assumed it meant to delete the origin files which I do not want. But does it actually mean to delete the copied files that are temporarily stored? Is there more I need to figure out? 
 
 My temporary solution was to delete the cron job for now until I can figure it out. 

 Thank you in advance.

---

### Post by savanna on 2012-02-11
The **--delete** option deletes files that are in the destination directory, but **not** in the source directory ie you do an rsync, you remove some files from the destination, then do an rsync again with **--delete** - those files removed from the source will get removed from the dest.

You're probably going to add to the **--exclude** to exclude the 1T backup file - therefore in addition to **--delete**, add the flag **--delete-excluded** - it will delete from the target any files you have excluded from the source.

HTH.

---

### Post by Paqman on 2012-02-12
Make sure that the target drive is actually mounted before the rsync job runs, otherwise (as you've discovered) it'll dump it all onto your root partition. If you're launching the rsync from a script in one of the anacron folders then just modify the script so it checks that the drive is mounted before running.

---

### Post by jamesisin on 2012-02-12
What Paqman says about mounting is important.  Have a look at this example backup script I published:

[http://jamesisin.com/a_high-tech_blech/index.php/2010/08/backup-script-a-love-story/](http://jamesisin.com/a_high-tech_blech/index.php/2010/08/backup-script-a-love-story/)

You will note that at the top of each section in the script there is a mount test.

---

