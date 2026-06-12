---
title: "Need help with backup script and setting up incrementals"
date: 2010-12-07
forum: General Help
---

### Post by dorlow on 2010-12-07
I have a backup script I use to backup all the stuff on my hard drive that's important to me.  The full backups work great.  Incrementals don't work at all.  It creates a full everytime.

Below is one backup command of my script... they're all the same... just different folders.

sudo tar -z --create \
         --file=/media/Backup/$(date +%y%m%d)_$(date +%H%M%S)_Desktop_Backup.tgz \
         --listed-incremental=/var/log/usr.snar \
         /home/david/Desktop/

In theory, what I need to do is just run this script everyday.  First backup should be a full backup and the rest should be incrementals until I delete the usr.snar file.  It doesn't work.  Everytime I run it, it performs full backups and doesn't backup only files that changed.  When I have over 300 GB of files to backup in a full backup, that's a big deal.  My full backups take about 10 hours.

---

### Post by CharlesA on 2010-12-07
I use rsync for backups, not tar, so I have no real experience with it doing incremental backups.

If you want to check it out, there is a page about it [here]("http://silverwav.wordpress.com/2010/01/15/rsync-local-backup/").

---

### Post by DaithiF on 2010-12-08
You say you're doing several backups each time, for various directories ... I hope you're using a different listed-incremental file for each one?  ie. you can't just use /var/log/usr.snar each time.

---

### Post by dorlow on 2010-12-08
Nope... I'm a newbie in that area.  I didn't know I was supposed to.  What I'm suprised is that the linux filing system doesn't have an archive bit, like ntfs does.  I can't believe that slipped the linux software engineers.

---

### Post by dorlow on 2010-12-08
Here's a script I call "backup_script"

sudo tar -z --create \
--file=/media/Backup/$(date +%y%m%d)_$(date +%H%M%S)_Desktop_Backup.tgz \
--listed-incremental=/var/log/usr.snar \
/home/david/Desktop/

This is just one excerpt of the file. I have about 10 lines like this backing up different folders. Everytime I run it, I have to type sudo backup_script and it asks me for a password. I can't figure out how to make it a trusted script file so then I could just use cron to schedule it and it won't prompt for a password.

---

### Post by DaithiF on 2010-12-08
> **dorlow said:**
> Nope... I'm a newbie in that area.  I didn't know I was supposed to.  What I'm suprised is that the linux filing system doesn't have an archive bit, like ntfs does.  I can't believe that slipped the linux software engineers.

I've always thought the windows archive bit was a dumb idea actually, and shows-up windows origin as a single user-centric OS.  What if there are multiple backup schemes in place?  e.g. maybe the sys-admin has a system-wide backup scheme but individual users also have their own backup mechanisms for their own files.  One archive bit can't help there.  Much more sensible would be to use file modification times to decide what gets archived.

---

### Post by matt_symes on 2010-12-08
My reply below does not make as much sense without the context of the question it was meant to answer, so this is from the other thread...

So for clarification...

> I fixed it yesterday by running the live cd.  I figured out what I did  wrong though.  I put my script in the /etc/sudoers.d folder.  It was  trying to read it as a source file or something like that.  I was  thinking at that moment when I dropped the script in that folder that  everything in that folder was a trusted folder and maybe it wouldn't  prompt for the sudo password for files in that folder... I was wrong.

Does anyone know how I can run this script without supplying the  password?  I've seen so many people post about it and I can't find a  straight post on how to do it.  I see everyone says you need to add the  user to the sudoers... but not one post I've come across has explained  how to do it.  I've screwed up my system once trying to figure it out,  so I hope someone will please just spell it out in plain english as if  I'm a complete dummy.

Here's a script I call "backup_script"

sudo tar -z --create \
         --file=/media/Backup/$(date +%y%m%d)_$(date +%H%M%S)_Desktop_Backup.tgz \
         --listed-incremental=/var/log/usr.snar \
         /home/david/Desktop/

This is just one excerpt of the file.  I have about 10 lines like this  backing up different folders.  Everytime I run it, I have to type sudo  backup_script and it asks me for a password.  I can't figure out how to  make it a trusted script file so then I could just use cron to schedule  it and it won't prompt for a password.
Original post.

Hi

```
sudo tar -z --create \
         --file=/media/Backup/$(date +%y%m%d)_$(date +%H%M%S)_Desktop_Backup.tgz \
         --listed-incremental=/var/log/usr.snar \
         /home/david/Desktop/
```Is there any reason the incremental file has to be in /var ? 

If you had it somewhere in your home directory (maybe in a hidden folder) and made sure that folder was not part of the backup, you could remove the sudo command from the front of each tar command. 

It is accessing the file /var/log/usr.snar that is requiring root permissions and that file does not have to be in /var.
[FONT=monospace]
[/FONT]```
tar -z --create \[FONT=monospace]
[/FONT] --file=/media/Backup/$(date +%y%m%d)_$(date +%H%M%S)_Desktop_Backup.tgz \[FONT=monospace]
[/FONT] --listed-incremental=/home/david/.log/usr.snar \[FONT=monospace]
[/FONT] /home/david/Desktop/
```Just remember to create the .log directory or tar will fail.

Kind regards

---

