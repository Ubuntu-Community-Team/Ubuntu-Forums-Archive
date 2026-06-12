---
title: "Sync Tool for Media Backup"
date: 2009-12-28
forum: General Help
---

### Post by jamesisin on 2009-12-28
I have built a media server (music mostly) and I have the extra backup drive ready to go.  I would like to create a synchronizing script to update changes to the backup drive periodically.

I have been looking at rsync as one such possible utility:

[http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/)

Here is my wish list.  It may or may not need to do all of these tasks:

[LIST][*] mount backup drive
[*] check mount status
[*] sync data (replace if newer/copy changes)
[*] trash any deleted files
[*] check its work
[*] unmount drive
[/LIST]


Are there any recommendations on this sync tool (or another)?

---

### Post by jamesisin on 2009-12-30
I have also heard mention of grsync.

Anybody have anything to say?

---

### Post by CharlesA on 2009-12-30
rsync would work. Grsync is just a graphical front-end to rysync.

You could probably run a check to see if the device is mounted, but I am unsure what such a script would look like.

---

### Post by jamesisin on 2009-12-30
Ultimately what I'd like to do is create a backup script that would sync, say, once per week and follow the parameters set above.  I don't keep the backup drives mounted normally, but that is certainly something I could work into the script (as well as a mount test).

You have used rsync and grsync?

I am curious about its ability as relates to updating files where a tag has been changed (flac files) and minimizing the file transfers.  It is my understanding that rsync will only change the portion of the file which has actually changed (rather than copying the entire file when a part of it has changed).

If this is so, it would certainly seem like an excellent tool for this task.

---

### Post by CharlesA on 2009-12-30
I've not used it with FLAC files, but I know it updates permissions fine.

Good point about not keeping backup drives mounted all the time. I might have to change the script I use to do backups.

Thanks.

---

### Post by 3L33T on 2009-12-30
Been using rsync for quite some time now and it truly serves its purpose:  good reliable and fast backup utility.   It will do what you described with a little scripting.  

The first time you send an rsync backup to your rsync server, it will  backup everything in the path you specified.  The successive backups will ONLY backup changes in the folder but it will also delete files/folders you've deleted from the source.  Thats what the "--delete" switch does in the following rsync command:

```

  /usr/bin/rsync -av --delete --stats <path of your data folder to backup> <your.rsync.server>::<name of rsync share>

```

---

### Post by natravis on 2009-12-30
> **jamesisin said:**
> I am curious about its ability as relates to updating files where a tag has been changed (flac files) and minimizing the file transfers.  It is my understanding that rsync will only change the portion of the file which has actually changed (rather than copying the entire file when a part of it has changed).

If this is so, it would certainly seem like an excellent tool for this task.

I think this understanding is correct. I haven't used it to back up music before (kept on my windows box [ease of gaming is the only reason]), but metadata is just another part of the file so I see no reason that it would not work, and if no one can offer a confirmation, it should be rather simple to test it with just a couple files. I would imagine using it with GRsync would be easier till you get the hang of how rsync works.

---

### Post by CharlesA on 2009-12-30
Found something to check if something is mounted.

```
if ! mountpoint -q /mnt/backup;
then
    mount /mnt/backup
fi
```

EDIT: You can do it that way if there is an extry in fstab.

To do it without an entry in fstab you can use this:

```
if ! mountpoint -q /mnt/backup;
then
    mount -t filesystem /dev/device/or/uuid /mnt/backup
fi
```

EDIT2: I just wrote this up to run the backup.

```
if ! mountpoint -q /dvdback
then
   mount -t ext3 UUID=7f4d33af-29d5-4def-bbc8-bee5a817f26e      /dvdback
fi
rsync -ai --delete --progress /array/dvds /dvdback
umount /dvdback
```

---

### Post by jamesisin on 2009-12-30
Sounds great.  If any of you experienced folks would like to offer your scripts to get me started, I won't complain.

3L33T - Will that also work if I move a file or folder within the library?  For instance, let's suppose that originally I had the soundtrack for Sherlock Holmes in Various but decided I would rather have it in a folder called Soundtracks.  Will rsync understand that maneuver or will I have to take special action?  (I am guessing from what you said that rsync will copy the new folder at the new location and delete the old folder from the old location.)

---

### Post by CharlesA on 2009-12-30
> **jamesisin said:**
> Sounds great.  If any of you experienced folks would like to offer your scripts to get me started, I won't complain.

3L33T - Will that also work if I move a file or folder within the library?  For instance, let's suppose that originally I had the soundtrack for Sherlock Holmes in Various but decided I would rather have it in a folder called Soundtracks.  Will rsync understand that maneuver or will I have to take special action?  (I am guessing from what you said that rsync will copy the new folder at the new location and delete the old folder from the old location.)

rsync will know that the file no longer exists at the location, so it will delete it and copy it over from the new location.

Do you have the UUID of the partition/drive you want to be mounted/unmounted and what directory you want it mounted to?

I can write up a script for you.

---

### Post by jamesisin on 2009-12-30
> **CharlesA said:**
> Do you have the UUID of the partition/drive you want to be mounted/unmounted and what directory you want it mounted to?

I can write up a script for you.

Thanks.  I can get them or you could just do something like [PLACEMOUNTPOINTHERE] and I can manage the remainder.

First, the drives are internal to the server (just not typically mounted).  This may change eventually, but for now this is what is.  They have specific mount points and I can make the persistent (which I haven't done as yet because of the lack of need).

About a month ago I copied the library to the backup drive anticipating this backup scheme.  Will rsync recognize the files and begin synking from that point forward?

---

### Post by phillw on 2009-12-30
Hi,

Cannot remember *why* but, when I was reading about rsyncing my ~home directory, it was advised to also use the -S option for sparse files. So I currently use ** rsync -aS */source/. /destination/.*** You may want to see if the -S option is applicable for your media files.

Regards,

Phill.

---

### Post by CharlesA on 2009-12-30
Do you want permissions kept? What is the file system of the backup drive?

```
if ! mountpoint -q /mountpoint
then
   mount -t filesystem /dev/partition /mountpoint
fi
rsync -ai --delete --progress /filestobackup /mountpoint
umount /mountpoint

```

Note rsync -a copies permissions, but will not copy the owner or group if you do not run it as root.

---

### Post by jamesisin on 2009-12-30
All of the drives are running ext3 I believe.  I would prefer to keep permissions.  They are to be rw for me and r and r for group and others.

I'm having this issue where Rhythmbox changes permissions when I re-tag anything (drops the r r).  IM or PM me if you want to discuss that.

---

### Post by CharlesA on 2009-12-30
The above script should be fine. You'd just need to put it in the root crontab with sudo crontab -e

---

### Post by jamesisin on 2009-12-30
I often appear smart, but could you tell me how to "put it in the root crontab with sudo crontab -e"?

---

### Post by CharlesA on 2009-12-30
> **jamesisin said:**
> I often appear smart, but could you tell me how to "put it in the root crontab with sudo crontab -e"?

Easy. Copy the above script into a file, make it executable.

Then type ```
sudo crontab -e
```into terminal, enter yer password and pick an editor (I use nano).

It'll bring you to the crontab of "root."

That's where you can setup scheduled tasks. Add the location of the script there with the time you want it to run.

Here's my system's root crontab.

```

#Sync RAID Array to External 1.5TB Drive hourly
0 */1 * * * /home/charles/docbk >/dev/null 2>&1
#Sync DVD folder to External 2.0TB Drive daily
0 0 * * * /home/charles/dvdbk >/dev/null 2>&1
#Update AV signatures for BitDefender
0 */8 * * * /home/charles/bdupdate >/dev/null 2>&1

```

Did you need help with the syntax of cron?

---

### Post by jamesisin on 2009-12-31
Well, some of it seems clear enough:

0 */8 * * * /home/charles/bdupdate >/dev/null 2>&1

????????  path/to/script >path/to/?? ?????

---

### Post by CharlesA on 2009-12-31
> **jamesisin said:**
> Well, some of it seems clear enough:

0 */8 * * * /home/charles/bdupdate >/dev/null 2>&1

????????  path/to/script >path/to/?? ?????

Ok I'll try to explain it as best I can.

> 1.  minute (from 0 to 59)
   2. hour (from 0 to 23)
   3. day of month (from 1 to 31)
   4. month (from 1 to 12)
   5. day of week (from 0 to 6) (0=Sunday)


Basically that update script is set to run at the 0 minute of every hour that is divisible by 8.

There's some more info on cron [here]("http://kevin.vanzonneveld.net/techblog/article/schedule_tasks_on_linux_using_crontab/").

As for the > /dev/null 2>&1 part. That redirects both standard and error output to /dev/null.

I ran the script a few times without using that, so it would record all that it did, but now that I know it works, I'm just letting it run without any output.

---

### Post by jamesisin on 2010-01-02
See next entry.  Clickhappy.

---

### Post by jamesisin on 2010-01-02
CharlesA -

Ok, so mine I want to run once per week.  Let's say Mondays at 4 AM.

0 4 * * 1 /home/[scriptpath] >/dev/null 2>&1

I guess I leave in the null bit and what follows?  I can look up crontab and see if I can figure out what it does later.

---

### Post by jamesisin on 2010-01-09
For anyone interested, I figured out what that last part was about:

0 4 * * 1 /home/[scriptpath] >/dev/null 2>&1

The 2>&1 routes the standard error (STDERR or 2) into the same location as the standard output (STDOUT or 1)&#8212;which in this case is /dev/null.  It could also be written as:

&>/dev/null

or

>&/dev/null

(without the 2>&1).

---

### Post by jamesisin on 2010-02-12
I wrote a /home folder backup based on advice received in this thread:

```
## Backup script for /home directory onto mounted drive

# check mount point (mount if necessary)

if ! mountpoint -q /media/MachinaMusica;
then
   mount /media/MachinaMusica
fi

# sync /home directory to mounted drive location (copy links; do not follow)

rsync -aSil --delete --progress /home /media/MachinaMusica/backups
```

Any obvious foibles?

---

### Post by CharlesA on 2010-02-12
> **jamesisin said:**
> I wrote a /home folder backup based on advice received in this thread:

```
## Backup script for /home directory onto mounted drive

# check mount point (mount if necessary)

if ! mountpoint -q /media/MachinaMusica;
then
   mount /media/MachinaMusica
fi

# sync /home directory to mounted drive location (copy links; do not follow)

rsync -aSil --delete --progress /home /media/MachinaMusica/backups
```

Any obvious foibles?

Looks good.

Is the device being mounted as /media/MachinaMusica in fstab? If it's not (external drive that isn't mounted all the time) you can run this:

mount -t filesystem /dev/device /mountpoint.

I use UUIDs for mounting devices, that way if the device name changes there is no problem.

---

### Post by jamesisin on 2010-02-12
No.  The backup is on a second internal hard drive (fstab).  I just thought it wise to include that check.

---

### Post by jamesisin on 2010-02-17
I have discovered a wee problem with Samba as concerns my script:

[http://ubuntuforums.org/showthread.php?p=8839564](http://ubuntuforums.org/showthread.php?p=8839564)

---

### Post by jamesisin on 2010-05-23
Would you mind reviewing my code again?  This is the backup script for my media server.  As you can see there are still some substitutions to do in the script (in []) but do you see any issues at this stage?

```
# redirect from script --> sends all STDERR to log file

exec 2> /path/to/error_log # use dated folder on desktop



## backup Tunage


if ! mountpoint -q /media/TuangeBU
then
   mount -t [filesystem] -U [UUID] /media/TunageBU
fi

# Note rsync -a copies permissions but will not copy owner:group if not run as root

rsync -ailS --delete --progress /media/Tunage/iTuna /media/TunageBU

umount /media/TunageBU


## backup Tonage


if ! mountpoint -q /media/TonageBU
then
   mount -t [filesystem] -U [UUID] /media/TonageBU
fi

# Note rsync -a copies permissions but will not copy owner:group if not run as root

rsync -ailS --delete --progress /media/TonageBU/Zoom /media/TonageBU
rsync -ailS --delete --progress /media/TonageBU/BB /media/TonageBU

umount /media/TonageBU
```

---

