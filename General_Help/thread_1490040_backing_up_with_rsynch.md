---
title: "backing up with rsynch"
date: 2010-05-21
forum: General Help
---

### Post by paulgault on 2010-05-21
I've got a lot of photos, home movies, documents, etc on my machine (currently running with ubuntu-10.04-desktop-amd64) and i've had issues in the past with hard drives failing. 

fortunately i've not lost anything substantial as all the important stuff was recovered from backups i had made with blank DVDs.

my last desktop rebuild was about 2 years ago and i decided that using blank DVDs to back things up was no longer practical as they're too small and the amount of data i need to backup is too large.

hard drive storage used to be quite expensive but they're getting cheaper and cheaper all the time. i bought 2 pretty large, identical drives for £50 ($70) each.

my machine has 3 hard drives in it. the first is a small solid state drive with the operating system on it, the second has all my data on it (mount point is /data) and a third to backup the stuff i don't want to lose (mount point is /backup).

i use the following script to automatically make another copy of all the stuff i want to backup onto a second drive.

```
#!/bin/sh

rsync -av --progress --delete --log-file=/home/paul/.backup_logs/rsync.home.$(date +%Y%m%d).log --exclude "/home/*/.gvfs" /home /backup/HomeBackup
chown paul /home/paul/backup_logs/rsync.home.$(date +%Y%m%d).log

rsync -av --progress --delete --log-file=/home/paul/.backup_logs/rsync.data.$(date +%Y%m%d).log /data /backup/DataBackup
chown paul /home/paul/backup_logs/rsync.data.$(date +%Y%m%d).log
```

this is automatically run at 9pm every night as a root cron job.

the 2 lines that begin with "rsynch" do the actual work of backing up my data. the 2 lines that begin with "chown" are just for convenience. they change the owner of the backup log to myself so i can easily delete them without being hindered by ownership issues (the script is run as ROOT so the logs are created, and therefore owned by ROOT).

i originally used [this article]("http://goinglinux.com/articles/Rsync-Bash-Cron-Backups.html") to help set it up in the first place. it explains the process with a good degree of clarity and i can recommend it to anyone who would like more info on this technique.

i'm not too worried about losing my system as all the configuration files in the home directory are backed up. it doesn't take too much effort to rebuild the system but it's the personal data that is much harder to replace. 

if the data drives fails i will be able to replace it and restore the data from the backup drive. if the backup fails i can just throw it away and make another backup. 

this whole strategy is designed to guard against a total drive failure. it offers no protection against accidental deletion of files except for the small window between the deletion and when the script is run (anything deleted from the data is also deleted from the backup the next time the script is run).

i've only really experienced hard drive failiure 3 or 4 times. the last time the computer started doing all sorts of wierd stuff and i didn't understand the issues involved.

i would appreciate anyones insight or experience on this.

i would like to know if anyone could point out any potential problems i have overlooked?

---

### Post by ragtag on 2010-05-21
You could pretty easily add incremental saving to that, so you have more than a days window, in case you accidentally delete something. I posted a script [here]("http://ubuntuforums.org/showthread.php?t=958695") a couple of years ago that can give you some ideas. It uses hard linking and the --link-dest option for rsync. This means that each incremental copy only takes about as much space as the files that have been changed since the last copy was made.

What you might also want to add is something that captures the error codes from your the rsync, and lets you know by mail if things didn't go as expected. My script doesn't do this. :)

---

### Post by paulgault on 2010-05-21
thanks ragtag. that looks like a pretty nifty script. i'll study it detail tomorrow. will definitely be able to incorporate it into the new backup scheme.

my main concern with my existing scheme is that any files or folders that disappear from a faulty data drive will also be deleted by the script from the backup also. this would not be good.

if i omit the --delete switch from the script then my backup drive will just fill up in no time.

is there any way to allow the backup device to fill up, and once it's full remove the files that were deleted from the original in age order?

to me it sounds like a pretty complicated script but does anyone out there know how to do it?

---

### Post by ragtag on 2010-05-23
The --link-dest option for rsync kind of solves that problem. It means that you're not overwriting the previous copy, just making hardlinks to it, and copying the files that have changed. So if you go to one of the older copies, files you have deleted will still be there. If you want to clear out older copies, you can simply delete the oldest copies from disk.

Hard links are actually pretty clever. When you create a file on your disk, such as a jpg image, the data is stored on the disk and a pointer that points to it. The pointer simply says where on the disk to find the data and is what you use to access it. When you delete the file, the pointer is generally the only thing that's deleted (which is why recovering deleted files actually works). Now, a hard link, is simply a second such pointer to the same data. So you may have a /home/me/me.jpg and /home/me/nice_photo.jpg, both pointing to the same data on disk. Changing one will change both, while deleting one will only delete that pointer, not the data. It's only when you delete all pointers to the data, that it's actually gone.

So what you can do with --link-dest, is say: copy my files from A to B, but if you find a copy of any file in C, that hasn't been changed, simply hard link to that instead. Where A is your main disk, B is where you're making a new backup, and C is your previous backup. 

Hope that made some sense. :)

---

### Post by BoneKracker on 2010-05-23
ditto what ragtag says about using hard links.

You ought to look at rsnapshot.
[http://rsnapshot.org/](http://rsnapshot.org/)

It uses rsync and makes it quite easy to set up a sophisticated rotation scheme utilizing hard links (so every "incremental" is in fact a full backup, without taking up any more space than a typical "full + incrementals" scheme.

It's so efficient I synchronize all the files I'm backing up hourly, and then I have a daily/weekly/monthly rotation scheme.  (And it all takes up no more resources than a single full backup plus incrementals.)

If you prefer to use your own script, you still ought to look at how this works to get ideas.

---

