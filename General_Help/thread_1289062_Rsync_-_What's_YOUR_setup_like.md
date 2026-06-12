---
title: "Rsync - What's YOUR setup like?"
date: 2009-10-12
forum: General Help
---

### Post by Roasted on 2009-10-12
Just a general question. I use rsync on my system because I have two pairs of drives I like to keep redundant. I have two 500gb drives (1 is mine, 1 is backup) and two 250gb drives for samba network storage where I keep backups of the windows machines on the network (1 main, 1 backup).

I mount the drives by fstab when the system boots. The mount points when unmounted are owned by root, whereas they are owned by me when mounted. As a result, I decided to avoid using the -a switch which requires root access, that way when I would auto run these backups via crontab, if the drive happened to be down due to hardware failure, the lack of root access wouldn't force the files to go to the mount point.

Because the trick is - If /storage drive dies, /media/storage still exists, and root permissions will push all of my data to that folder, which would then reside on my root partition, therefore definitely maxing it out.

Anyway - What's your setup like? Is my setup in need of some work? Should I use the -a command to keep permissions on the files/folders, etc all the same?

What do you think and what's your backup situation like?

---

### Post by StuartN on 2009-10-12
> **Roasted said:**
> What's your setup like?

I use the remote rsync daemon on the backup box and I find that a) it keeps the process alive even on really bad wireless connections and b) it is a lot faster than mounting the BackupBox drives locally. One line of my backup script is:

```
rsync -i -avh --delete ~/Documents/ rsync://BackupBox.local:/Stuartn/Documents/ >> backup.log
```

BackupBox is a big disk and a tiny processor running Linux. My username Stuartn is also configured as a module name in rsyncd.conf on BackupBox.

---

### Post by Roasted on 2009-10-13
See, I love Linux and all but that kind of command you use there confuses the crap out of me.

Is there a GUI application that runs on rsync that does the same thing you're doing via command line?

---

### Post by StuartN on 2009-10-13
> **Roasted said:**
> Is there a GUI application that runs on rsync that does the same thing you're doing via command line?

Why would you want a GUI for something that runs so well? Just save it in a command file with comments on your command-line options. If you must, then Grsync is a front-end for rsync.

My rsync uses -i (itemize all changes in detail) -a (archive settings, which includes permissions etc) -v (verbose, tell you what its doing) -h (human-readable numbers, like 1 GB) and --delete to delete anything on the destination that has been deleted on the source. I also send the output to a text file (> backup.log) where I can see when and what I last backed up.

---

### Post by Lars Noodén on 2009-10-13
> **Roasted said:**
> See, I love Linux and all but that kind of command you use there confuses the crap out of me.

Is there a GUI application that runs on rsync that does the same thing you're doing via command line?

Think of it as scripting, that's what you are really doing.

Anyway, in most cases the GUI is just a crippled front-end for the regular program.  

And to answer the original question, here's an older rsync script:

```

rsync --exclude '*.AppleDouble*' --exclude '*~' --exclude 'gz.?' -tavv \
   -e "ssh -i /Users/me/.ssh/mykey" \
   /Users/me/Files/Projects/2B1202/ me@$HOST:/home/me/Desktop/Projects/2B1202/
```

If [bourne shell](http://www.softpanorama.org/People/Shell_giants/introduction.shtml) is to foreign, then try perl or python.

---

### Post by Lars Noodén on 2009-10-13
[Steve's Bourne / Bash shell scripting tutorial](http://steve-parker.org/sh/sh.shtml) for demystification of the shell:
[http://steve-parker.org/sh/sh.shtml](http://steve-parker.org/sh/sh.shtml)

---

### Post by Roasted on 2009-10-13
Going back to a side question I had listed above, do I kind of have a goofy setup for my rsyncing? 

Take this for example. /media/localbackup is a 2nd 500gb drive in my system which backs up data from my primary drives home directory. Okay, fine. But when I rsync, I don't run it as root and I don't run it with the -a command. So it'll sync everything, but not with permissions.

My thinking was this. /media/localbackup is a mount point for the 500gb backup drive. That mount point is owned by me. If the drive is not mounted, it is owned by root. Therefore, if there's no root permissions, and the drive isn't mounted, the drive doesn't get synced. That's good.

The problem comes into play when I DO decide to use root, because if I run my crontab entry as root, and my backup drive isn't mounted due to hardware failure or something, then /media/localbackup becomes a folder on my root partition of my primary drive.

Have you guys ever tried to push 380gb of data into a 20gb spot? I can only imagine my system would be so slow it'd be nearly unusable, and if I'd reboot - unable to log in due to the space being maxed.

Any advice in this scenario?

---

### Post by zhanglini on 2009-10-13
> **Roasted said:**
> See, I love Linux and all but that kind of command you use there confuses the crap out of me.

Is there a GUI application that runs on rsync that does the same thing you're doing via command line?

Yes it is called Grsync I believe that you can install from Synaptic.

---

### Post by Penguin Guy on 2009-10-13
Mine's complicated, I found that rsync was taking ages to back up while the partition being backed up was in use. So I have a separate OS to take care of backups and general maintenance. I have a backup program made up of three files, here it is:

**[BASH]** *- /usr/local/bin/backup*
[PHP]
#!/bin/bash

##### CONSTANTS #####
NAME="${0##*/}"
DESCRIPTION=
VERSION=0.2
LOCATION="$(readlink -f $0)"
LOCATION="${LOCATION%$NAME}"
EXCLUDE="${LOCATION}exclude-list"
WRITE='/media/backup'  # WARNING: Directory specified will be overwritten
READ='/media/system'  # WARNING: Directory specified may be overwritten
BACKUP_NAME='Backup'

##### MAIN CODE #####
if [ "$UID" != 0 ]; then     # If you are not root
	exec sudo $0     # Ask for authentication
fi
if [ "$1" == '-a' ]; then     # If used with an -a flag: Mount partitions
	mount /dev/sda6 "$READ" || exit 1
	mount /dev/sda5 "$READ/boot" || exit 1
	mount /dev/sda7 "$READ/home" || exit 1
fi
if [ ! -d "$WRITE" ]; then     # If backup folder does not exist
	echo >&2 "Please mount backup device at $WRITE and press [ENTER] to continue.
Press [ESC] to do backup later."
fi
while [ ! -d "$WRITE" ]; do
	if [ "$(wait-keypress 
)" == '' ]; then  # Escape/Enter
		exit 0
	fi
done
echo 'The backup may take some time, please be patient...'
rsync -acv --del "$READ/" "$WRITE/$BACKUP_NAME/" --exclude-from="$EXCLUDE"

if [ "$?" == 0 ]; then
	echo "Backup completed successfully!"
	exit 0
else 
	echo "Backup did not complete successfully."
	exit 1
fi
[/PHP]


*/usr/local/bin/exclude-list*
```

+ /home/*/.themes
+ /home/*/.icons
+ /home/*/.backgrounds
+ /home/*/.wallpapers
- /root/.gvfs
- /home/*/.gvfs
- /root/.local/share/Trash/
- /home/*/.local/share/Trash/
- lost+found/
- /tmp/
- /cdrom/
- /media/
- /mnt/
- /proc/
- /sys/

```


**[BASH]** *- /usr/local/bin/wait-keypress*
[PHP]
#!/bin/bash
while (true); do
	stty cbreak -echo; key=$(dd bs=1 count=1 2>/dev/null); stty -cbreak echo
	if [ "$@" == '' ]; then     # If enter key is pressed
		echo -n "$key"
		exit 0
	elif [[ "$@" =~ "$key" ]]; then     # If a trigger key is pressed
		echo -n "$key"
		exit 0
	fi
done
[/PHP]

---

### Post by Penguin Guy on 2009-10-13
> **Roasted said:**
> Going back to a side question I had listed above, do I kind of have a goofy setup for my rsyncing? 

Take this for example. /media/localbackup is a 2nd 500gb drive in my system which backs up data from my primary drives home directory. Okay, fine. But when I rsync, I don't run it as root and I don't run it with the -a command. So it'll sync everything, but not with permissions.

My thinking was this. /media/localbackup is a mount point for the 500gb backup drive. That mount point is owned by me. If the drive is not mounted, it is owned by root. Therefore, if there's no root permissions, and the drive isn't mounted, the drive doesn't get synced. That's good.

The problem comes into play when I DO decide to use root, because if I run my crontab entry as root, and my backup drive isn't mounted due to hardware failure or something, then /media/localbackup becomes a folder on my root partition of my primary drive.

Have you guys ever tried to push 380gb of data into a 20gb spot? I can only imagine my system would be so slow it'd be nearly unusable, and if I'd reboot - unable to log in due to the space being maxed.

Any advice in this scenario?
Yes, run it as root, and make sure the permissions get preserved, but do a check to make sure the drive is mounted. As for how you do that, I'm not totally sure: [google]("http://www.google.com/") it.

---

### Post by StuartN on 2009-10-13
> **Penguin Guy said:**
> Yes, run it as root, and make sure the permissions get preserved, but do a check to make sure the drive is mounted. As for how you do that, I'm not totally sure: [google]("http://www.google.com/") it.

This cludge will check if something is mounted:

```
cat /proc/mounts | grep /media/BigBadBackup
if [ $? -eq 1 ] ; then
  # BigBadBackup is mounted, so we can rsync to it
fi
```

But if you don't need to rsync as root, then don't run it as root. Using the minimum permission to get the job done is safer. You should use -a which is equivalent to all of -r recurse; -l copy symlinks as symlinks; -ptgo permissions, times, group and owner; and -D preserve device / specials if superuser. Using -a means your backup is pretty much identical to your original, and will function the same if restored.

---

### Post by Roasted on 2009-10-13
> **StuartN said:**
> Using -a means your backup is pretty much identical to your original, and will function the same if restored.

That's actually kind of what I want, to be honest. 

Is there any way we can break down that grep command so I understand it easier? I have 4 drives in my system, 2 of which are backups. 500/500gb and 250/250gb... the 500s are mine + backup and the 250s are samba network file storage + backup.

The mount points are:

/media/localbackup
/media/storage
/media/storagebackup

Each command is:

rsync -a --progress --delete /source /destination

How would I incorporate that grep command into each individual rsync command, seeing as though I'm running 3 commands in a bin/bash script.

---

### Post by StuartN on 2009-10-13
> **Roasted said:**
> Is there any way we can break down that grep command so I understand it easier?

The first part, cat /proc/mounts, is a list of currently mounted filesystems - you could equally use the mount command. The output is piped into grep to search for a particular mountpoint.

*Note that your second mount at /mount/storage would also match your third at /mount/storagebackup, so add the -w (whole word) option to grep.*

The variable $? is (I think) a success flag. Whatever it is, echo $? shows you 0 if a command returned a result, or 1 if it did not - most commands return 0. Grep returns 0 if the string was matched and 1 if it was not.

So we just check each mountpoint in turn and run rsync if it is present.

```
cat /proc/mounts | grep -w /media/localbackup
if [ $? -eq 0 ] ; then
  rsync -a --progress --delete source1 /media/localbackup
fi

cat /proc/mounts | grep -w /media/storage
if [ $? -eq 0 ] ; then
  rsync -a --progress --delete source2 /media/storage
fi

cat /proc/mounts | grep -w /media/storagebackup
if [ $? -eq 0 ] ; then
  rsync -a --progress --delete source3 /media/storagebackup
fi
```

I have my backup script on the desktop to click whenever I want to feel like I have done something important. I could add it to crontab, but that would be too organized.

---

### Post by Roasted on 2009-10-14
Well, geez. I'm not exactly a programmer but that still is confusing to me.

I just thought there would be an easier command to execute which first checks the mount point then pipes it to run. That was just my assumption though... something like:

sudo if /media/localbackup exists | rsync -a --progress --delete /home/jason /media/localbackup

---

### Post by StuartN on 2009-10-14
> **Roasted said:**
> Well, geez. I'm not exactly a programmer but that still is confusing to me.

My apologies, I made a mistake in that example. The tests should all be **[ $? -eq 0 ]**, that is run the rsync if the grep was successful and not **[ $? -eq 1 ]** which would run rsync if the grep failed (did not return any matches).

*NB: $? is set by every command, so echo $? is zero if the last command "succeeded", e.g. it is not zero after **ls this_file_does_not_exist**, which can be very useful.*

---

### Post by Roasted on 2009-10-15
> **StuartN said:**
> My apologies, I made a mistake in that example. The tests should all be **[ $? -eq 0 ]**, that is run the rsync if the grep was successful and not **[ $? -eq 1 ]** which would run rsync if the grep failed (did not return any matches).

*NB: $? is set by every command, so echo $? is zero if the last command "succeeded", e.g. it is not zero after **ls this_file_does_not_exist**, which can be very useful.*

LOL. I wouldn't have known the difference any other way.

So, say I didn't come here and get this help from you guys. What should I do then? Should I just run the script with root and just bank on hoping the drives stay active? 

I guess worst case scenario, if a drive DOES go down and the script kicks in anyway, it would just kick 300gb of data to the empty mount point, which would just dump it on my root partition and max it out. At that point all I should need to do is delete the data, or at worst - boot to a LiveCD and remove it from the unmounted mount point.

Is my train of thought correct?

---

### Post by Roasted on 2009-10-16
New question - Is it possible to rsync to the drive itself rather than its mount point?

/dev/sdb1 gets mounted to /media/localbackup

I can rsync to /media/localbackup, I got that.

But can I run my rsync to /de/sdb1?

I was just thinking, if /dev/sdb1 goes down, it's gone, so if the rsync script kicks in, it won't see it, whereas it'll see /media/localbackup regardless of whether or not it's mounted cause it's still a folder where data can be put into.

---

### Post by StuartN on 2009-10-16
> **Roasted said:**
> New question - Is it possible to rsync to the drive itself rather than its mount point?

I am sure someone will correct me if I am wrong, but I would not think that rsync can handle a raw device. If the device has not been mounted then there is no protocol to write to it - i.e. rsync would have no knowledge of the filesystem, let alone any paths or access permissions.

---

### Post by Roasted on 2009-10-16
> **StuartN said:**
> I am sure someone will correct me if I am wrong, but I would not think that rsync can handle a raw device. If the device has not been mounted then there is no protocol to write to it - i.e. rsync would have no knowledge of the filesystem, let alone any paths or access permissions.

/dev/sdb1 = /media/localbackup

I tried my rsync script, but plugged in /dev/sdb1 for /media/localbackup and it barfed out a bunch of errors. So I guess the answer to that is a "no." 

Question - if I would utilize a program such as GRsync, would that program be able to detect if a HDD is active/mounted prior to executing the command? I'm just trying to find a more automated way to handle this, mostly because I want to make sure I do it right and these commands are kind of "whoa, wtf??" to me.

---

### Post by CharlesA on 2009-10-16
I don't know if it will know if a device is mounted or not. What I did was mount my external to something like /sync and then run something like this:

```
rsync -ar /storage /sync
```

-a = archive, copies all permissions and whatnot
-r = recursive, copying everything recursively

---

### Post by Roasted on 2009-10-17
> **CharlesA said:**
> I don't know if it will know if a device is mounted or not. What I did was mount my external to something like /sync and then run something like this:

```
rsync -ar /storage /sync
```

-a = archive, copies all permissions and whatnot
-r = recursive, copying everything recursively

So you run that as root, I take it? Since -a requires root to get passed over properly. Otherwise it's just a null switch.

---

### Post by StuartN on 2009-10-17
> **Roasted said:**
> So you run that as root, I take it? Since -a requires root to get passed over properly. Otherwise it's just a null switch.

I never run rsync as root. The -a archive option works as long as there are sufficient permissions to read the source and read / write the destination. It is never a null switch, but it will fail when there is insufficient permission. The --itemize-changes and --verbose (or even --verbose --verbose for extra messages) will give plenty of explanation of what changes are made / skipped.

---

### Post by CharlesA on 2009-10-17
> **Roasted said:**
> So you run that as root, I take it? Since -a requires root to get passed over properly. Otherwise it's just a null switch.

I run it with cron. Even when running it manually, it copies it over, but changes the owner, but not the group or permissions. Not quite sure if there is a way to fix that since I've been running rsync as my user account.

Would running as root fix that?

---

### Post by StuartN on 2009-10-17
> **CharlesA said:**
> I run it with cron. Even when running it manually, it copies it over, but changes the owner, but not the group or permissions. Not quite sure if there is a way to fix that since I've been running rsync as my user account.

Would running as root fix that?

Cron runs as root. There is no reason why, in a properly mounted set of filesystems, the ownership would change. If you look then you will probably find you have lost file timestamps too.

---

### Post by CharlesA on 2009-10-17
> **StuartN said:**
> Cron runs as root. There is no reason why, in a properly mounted set of filesystems, the ownership would change. If you look then you will probably find you have lost file timestamps too.

How would I check for those?

This is what I get when I check the original:

```

charles@thor:/array/clone/Osiris_Windows7RC$ ls -l
total 5110572
-rw-rw---- 1 clone clone          4 2009-10-14 20:18 disk
-rw------- 1 clone clone    8904357 2009-10-14 20:05 hda1.ntfs-ptcl-img.gz.aa
-rw------- 1 clone clone 2097152000 2009-10-14 20:10 hda2.ntfs-ptcl-img.gz.aa
-rw------- 1 clone clone 2097152000 2009-10-14 20:16 hda2.ntfs-ptcl-img.gz.ab
-rw------- 1 clone clone 1023773945 2009-10-14 20:18 hda2.ntfs-ptcl-img.gz.ac
-rw-rw---- 1 clone clone         37 2009-10-14 20:05 hda-chs.sf
-rw-rw---- 1 clone clone    1048064 2009-10-14 20:05 hda-hidden-data-after-mbr
-rw-rw---- 1 clone clone        512 2009-10-14 20:05 hda-mbr
-rw-rw---- 1 clone clone        323 2009-10-14 20:05 hda-pt.parted
-rw-r----- 1 clone clone          0 2009-10-14 20:05 hda-pt.sf
-rw-rw---- 1 clone clone      13262 2009-10-14 20:18 Info-dmi.txt
-rw-rw---- 1 clone clone      16877 2009-10-14 20:18 Info-lshw.txt
-rw-rw---- 1 clone clone        285 2009-10-14 20:18 Info-packages.txt
-rw-rw---- 1 clone clone         10 2009-10-14 20:18 parts
charles@thor:/array/clone/Osiris_Windows7RC$

```Backup:

```
charles@thor:/array/clone/Osiris_Windows7RC$ ls -l /sync/clone/Osiris_Windows7RC
total 5052060
-rw-rw---- 1 charles clone          4 2009-10-14 20:18 disk
-rw-rw---- 1 charles clone    8971058 2009-10-10 20:26 hda1.ntfs-ptcl-img.gz.aa
-rw-rw---- 1 charles clone 2097152000 2009-10-10 20:34 hda2.ntfs-ptcl-img.gz.aa
-rw-rw---- 1 charles clone 2097152000 2009-10-10 20:41 hda2.ntfs-ptcl-img.gz.ab
-rw-rw---- 1 charles clone  963849232 2009-10-10 20:45 hda2.ntfs-ptcl-img.gz.ac
-rw-rw---- 1 charles clone         37 2009-10-14 20:05 hda-chs.sf
-rw-rw---- 1 charles clone    1048064 2009-10-14 20:05 hda-hidden-data-after-mbr
-rw-rw---- 1 charles clone        512 2009-10-14 20:05 hda-mbr
-rw-rw---- 1 charles clone        323 2009-10-14 20:05 hda-pt.parted
-rw-r----- 1 charles clone          0 2009-10-14 20:05 hda-pt.sf
-rw-rw---- 1 charles clone      13262 2009-10-14 20:18 Info-dmi.txt
-rw-rw---- 1 charles clone      16877 2009-10-14 20:18 Info-lshw.txt
-rw-rw---- 1 charles clone        285 2009-10-14 20:18 Info-packages.txt
-rw-rw---- 1 charles clone         10 2009-10-14 20:18 parts
```Is there any way to track down why it's changing the owner?

EDIT: So far only the clone folder is the one with the permissions changing. Other then that, the permissions are fine minus the owner.

EDIT2: Looks like the -o option only works as superuser aka root. That must be why the owner is changing.

---

### Post by StuartN on 2009-10-17
> **CharlesA said:**
> How would I check for those?
```
charles@thor:/array/clone/Osiris_Windows7RC$ ls -l -rw-rw---- 1 charles clone    8971058 2009-10-10 20:26 hda1.ntfs-ptcl-img.gz.aa
-rw-rw---- 1 charles clone 2097152000 2009-10-10 20:34 hda2.ntfs-ptcl-img.gz.aa
-rw-rw---- 1 charles clone 2097152000 2009-10-10 20:41 hda2.ntfs-ptcl-img.gz.ab
-rw-rw---- 1 charles clone  963849232 2009-10-10 20:45 hda2.ntfs-ptcl-img.gz.ac

```

These four directories in the backup are newer than the source. The most likely issue is the ownership of the source, the destination and the user running rsync do not match. How do you have the partitions mounted?

The commands **mount** and **ls -ld <mountpoint>** (where <> contains the path to your mountpoint) should tell you all you need.

---

### Post by CharlesA on 2009-10-17
> **StuartN said:**
> These four directories in the backup are newer than the source. The most likely issue is the ownership of the source, the destination and the user running rsync do not match. How do you have the partitions mounted?

The commands **mount** and **ls -ld <mountpoint>** (where <> contains the path to your mountpoint) should tell you all you need.

Thanks. Here's what I get when I run ls -ld /array:

```
charles@thor:/$ ls -ld /array
drwxr-xr-x 14 charles charles 4096 2009-10-11 02:37 /array

```and ls-ld /sync:

```
charles@thor:/$ ls -ld /sync
drwxrwxr-x 13 charles charles 4096 2009-10-11 03:00 /sync

```The owner is the same one that is doing the rsync.

The results for those two mount points in mount is this:
```
/dev/sdb1 on /array type ext3 (rw)
/dev/sdc1 on /sync type ext3 (rw)


```

Since the group doesn't have write access on /array, is that what is causing the problem?

Thanks!

---

### Post by Roasted on 2009-10-17
> **StuartN said:**
> Cron runs as root. There is no reason why, in a properly mounted set of filesystems, the ownership would change. If you look then you will probably find you have lost file timestamps too.

No, it does not, unless you specify to run as root.

I know this because I use cron with rsync, and it runs as user "jason" (me) and does not transfer all group ownerships and everything else as the full -a switch does.

I forgot how many functions -a has, but without running -a as root, you're not maximizing it for everything it's capable of.

Question - When using -a without root priviledges, do the permissions themselves get carried over, and just not the group ownerships?

EDIT - Another Question - I have a group set up called sambashare, where I added myself + all other users to the group simply so on my machine here, I can access their files if need be. They on the other hand do not need to access each others files, despite them all being in the sambashare group and sambashare being the group assigned to the samba network shares. So technically, on my machine, they could log in as themselves and get to everybody's stuff. But Samba permissions on each share prevents them from opening the shares, so that's okay there.

Question is, being that the only reason I have the group in place is so I (jason) can hit all of the shares on my drives, would it make more sense to just assign jason as the group to each share? Because I have the shares owned by the user who utilizes them, but of course I have the group assigned too... aka... fred:sambashare. With each user, there's a group that exists with the same name, right? Should I just assign fred:jason instead of fred:sambashare? I'd get the same results, wouldn't I?

---

### Post by CharlesA on 2009-10-17
> **Roasted said:**
> 
Question - When using -a without root priviledges, do the permissions themselves get carried over, and just not the group ownerships?

When I checked the permissions, they were correct outside of the "clone" folder but I'm still not sure why those perms are screwed up.

Basically to run rsync as root with cron would look something like this, right?

```
* * * * * root rsync -a /array/* /sync
```EDIT:

> **Roasted said:**
> 
Question is, being that the only reason I have the group in place is so I (jason) can hit all of the shares on my drives, would it make more sense to just assign jason as the group to each share? Because I have the shares owned by the user who utilizes them, but of course I have the group assigned too... aka... fred:sambashare. With each user, there's a group that exists with the same name, right? Should I just assign fred:jason instead of fred:sambashare? I'd get the same results, wouldn't I?

Each user has a group created for them, yes. I believe that's how I have mine set up. me (charles) is a member of the other user's groups as well, so I have the same access as they do.

---

### Post by scouser73 on 2009-10-17
For backing up I use [[COLOR="Red"]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html"), the tutorial shows you how to use it and in my opinion I think it's an excellent program for backing up data.

---

### Post by StuartN on 2009-10-17
> **CharlesA said:**
> Basically to run rsync as root with cron would look something like this, right?

```
* * * * * root rsync -a /array/* /sync
```EDIT:

No, cron runs as a root process. It runs jobs in root's crontab as root and jobs in each user's crontab as that user. To list your jobs run **crontab -l** and to see root's run **sudo crontab -l**.

rsync should run correctly and preserve all ownership, permissions etc (-a is equal to  -rlptgoD, recurse, symlinks, permissions, time, group, owner, devices) when run as a normal user, so long as that user has permission to read the source and both read and write the destination.

You (charles) are copying files owned by clone from /clone onto /array, which is owned by charles, group charles. Nobody else is a member of group charles. clone's files are written by charles but ownership can not be assigned to clone because clone has no write permission, so they remain charle's property. Adding the -i (--itemize-changes) option to rsync would show the precise details of what happens, i.e. there will be an entry for each file ownership was not reassigned.

---

### Post by CharlesA on 2009-10-17
Actually copying them from /array to /clone.

Does /sync need write access for "everyone else," or can I just setup a group that gives write access to the user "clone" (and me)?

I'm trying rsync with the -i switch, to see what happens.

If I run rsync as root:

```
sudo -s
Root # rsync -a --progress /array/clone /sync
```It copies the permissions and preserves the owner.

When I run rsync as me, it changes the owner and displays this error at the end:

rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1058) [sender=3.0.5]

Previous errors were:

```
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372971": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372972": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372973": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372974": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372975": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372976": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372977": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372978": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372979": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372980": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372981": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372982": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372983": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372984": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372985": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372986": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372987": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372988": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372989": Permission denied (13)
rsync: send_files failed to open "/array/clone/Osiris_KDE_Ubuntu/.lvm_debian_4200_957372990": Permission denied (13)

```Which would explain why it wouldn't copy those.

The permissions for those are:

```
charles@thor:/array/clone/Osiris_KDE_Ubuntu$ ls -la
total 1080580
drwxrwx--- 2 clone clone       4096 2009-10-16 20:04 .
drwxrwx--- 8 clone clone       4096 2009-10-16 20:04 ..
-rw-rw---- 1 clone clone          4 2009-10-16 20:04 disk
-rw------- 1 clone clone   12842035 2009-10-16 20:00 hda5.ext2-ptcl-img.gz.aa
-rw-rw---- 1 clone clone         37 2009-10-16 20:00 hda-chs.sf
-rw-rw---- 1 clone clone      31744 2009-10-16 20:00 hda-hidden-data-after-mbr
-rw-rw---- 1 clone clone        512 2009-10-16 20:00 hda-mbr
-rw-rw---- 1 clone clone        424 2009-10-16 20:00 hda-pt.parted
-rw-r----- 1 clone clone          0 2009-10-16 20:00 hda-pt.sf
-rw-rw---- 1 clone clone      13262 2009-10-16 20:04 Info-dmi.txt
-rw-rw---- 1 clone clone      16821 2009-10-16 20:04 Info-lshw.txt
-rw-rw---- 1 clone clone        285 2009-10-16 20:04 Info-packages.txt
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372971
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372972
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372973
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372974
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372975
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372976
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372977
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372978
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372979
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372980
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372981
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372982
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372983
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372984
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372985
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372986
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372987
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372988
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372989
-rw------- 1 clone clone          0 2009-10-16 20:00 .lvm_debian_4200_957372990
-rw-rw---- 1 clone clone        257 2009-10-16 20:00 lvm_logv.list
-rw-rw---- 1 clone clone         56 2009-10-16 20:00 lvm_vg_dev.list
-rw------- 1 clone clone 1092459705 2009-10-16 20:04 osiris-root.ext3-ptcl-img.gz.aa
-rw-rw---- 1 clone clone         10 2009-10-16 20:04 parts
-rw-rw---- 1 clone clone         53 2009-10-16 20:04 swappt-osiris-swap_1.info

```*sigh* The only directory I am having problems with is the clone directory and that's the one I use with Clonezilla...

EDIT: I am listed as a user in the clone group.

Sorry for going so off topic.

---

### Post by StuartN on 2009-10-17
> **CharlesA said:**
> Actually copying them from /array to /clone.

Does /sync need write access for "everyone else," or can I just setup a group that gives write access to the user "clone" (and me)?

Sorry, I got confused there. You (charles) are copying files owned by clone from /array (owned by charles:chales) to /sync (owned by charles:charles). It is still the case that only charles and members of the charles group (just charles) can write to /sync.

You need to change ownership to charles:<some_group> where clone is a member of <some_group> and be sure that /sync has group rw permission.

---

### Post by CharlesA on 2009-10-17
> **StuartN said:**
> Sorry, I got confused there. You (charles) are copying files owned by clone from /array (owned by charles:chales) to /sync (owned by charles:charles). It is still the case that only charles and members of the charles group (just charles) can write to /sync.

You need to change ownership to charles:<some_group> where clone is a member of <some_group> and be sure that /sync has group rw permission.

Thank you!

I changed the perms on /array and /sync to 

drwxrwx--- 14 charles raid 4096 2009-10-11 02:37 /array

where the group "raid" has members charles and clone in it.

I'll see if that fixed the problem with clonezilla when I get home.

Hopefully that was what the problem was, since I was copying to a Samba share.

---

### Post by CharlesA on 2009-10-17
Tried running rsync -ai 

Worked without any problems. Unfortunately it changed the owner as well. I'm figuring I'll just have to run it as root.

Oh well.

EDIT: It worked fine when I ran it as root. *grumble*

---

### Post by Roasted on 2009-10-17
> **StuartN said:**
> No, cron runs as a root process.

I don't understand this, but I'm not sure if this pertains to me at all or if it's specific to the other guy's problem.

In cron, I have the script set to execute by jason.

An indication that rsync -a is indeed running by "root" is that the group ownership will be preserved.

If I run sudo rsync -a, the group ownership is preserved.
If I run rsync -a without sudo, the group ownership is not preserved.

As a result, when I run rsync -a in cron with jason as the executing user, group ownership is not preserved.

I know this because, that's exactly what happened on my system.

Cron executes my backup script by jason, which begins with rsync -a etc etc, and group ownership does not get preserved.

Which begs the obvious question - how is it accurate to say cron executes as root?

---

### Post by CharlesA on 2009-10-17
At least it's not just me that's having those results. Thanks for confirming it.

---

### Post by StuartN on 2009-10-18
> **Roasted said:**
> An indication that rsync -a is indeed running by "root" is that the group ownership will be preserved.

No, this only means that the owner of the files did not have permission to write to rsync's destination. It indicates that there is a problem with your setup. The archive option -a functions perfectly well when the permissions are correct. Running rsync with sudo is not a solution, merely a forceful workaround - it is far better to set up correct permissions.

You can see that cron runs as root in System Monitor, and this is necessary for it to assign ownership of cron jobs to any user on the system. Ideally you would put rsync in your own, and not root's, crontab file to prevent accidental overwrites.

You need to be sure that the owner of the files being rsynced has write access to the destination, either as owner or member of the group that owns the destination path and each directory within it.

---

### Post by CharlesA on 2009-10-18
> **StuartN said:**
> No, this only means that the owner of the files did not have permission to write to rsync's destination. It indicates that there is a problem with your setup. The archive option -a functions perfectly well when the permissions are correct. Running rsync with sudo is not a solution, merely a forceful workaround - it is far better to set up correct permissions.

You can see that cron runs as root in System Monitor, and this is necessary for it to assign ownership of cron jobs to any user on the system. Ideally you would put rsync in your own, and not root's, crontab file to prevent accidental overwrites.

You need to be sure that the owner of the files being rsynced has write access to the destination, either as owner or member of the group that owns the destination path and each directory within it.

I don't understand what's wrong with my permissions.

I created a group called "raid" that has the members of: charles, clone, karen.

ls -ld /sync returns this:

```
drwxrwx--- 13 charles raid 4096 2009-10-18 07:50 sync
```That group has write access to that folder, but the owner still changes to me. 

This is getting quite annoying tbh. :confused:

The folder structure looks like this

```
drwxrwx--- 14 charles raid 4096 2009-10-17 18:20 array
drwxrwx--- 13 charles raid 4096 2009-10-18 07:50 sync
```I am trying to sync everything in the /array folder into the /sync folder.

This is what is in the array directory:

```
drwxrwx---  22 charles charles   4096 2009-10-17 19:59 charles
**drwxrwx---  10 clone   clone     4096 2009-10-17 20:36 clone**
drwxrwxr-x 167 charles charles  12288 2009-10-11 02:34 dvds
drwxrwx---   4 charles charles   4096 2009-10-10 19:32 guildwars
drwxrwxr-x  13 charles charles   4096 2009-10-10 19:52 isos
**drwxrwx---   4 karen   karen     4096 2009-10-15 15:28 karen**
drwxrwxr-x   3 charles charles 114688 2009-10-10 20:10 music
drwxrwxr-x   2 charles charles   4096 2009-10-10 20:12 servicepacks
drwxrwxr-x   5 charles charles   4096 2009-10-13 05:20 shared
drwxrwxr-x   8 charles charles   4096 2009-10-10 20:45 testout
drwxrwx---   4 charles charles   4096 2009-10-10 20:51 win7stuff

```It works fine, except for changing the owner.

Is there something wrong with my permissions?

The only ones I am having problem with are karen and clone. The others are folders that only I access, so the owner and group are set to charles.

---

### Post by Roasted on 2009-10-18
> **StuartN said:**
> No, this only means that the owner of the files did not have permission to write to rsync's destination. It indicates that there is a problem with your setup. The archive option -a functions perfectly well when the permissions are correct. Running rsync with sudo is not a solution, merely a forceful workaround - it is far better to set up correct permissions.

You can see that cron runs as root in System Monitor, and this is necessary for it to assign ownership of cron jobs to any user on the system. Ideally you would put rsync in your own, and not root's, crontab file to prevent accidental overwrites.

You need to be sure that the owner of the files being rsynced has write access to the destination, either as owner or member of the group that owns the destination path and each directory within it.

All right. Here's a curve ball for you.

I own every single folder. I own the mount points. I own the folders inside the mount points. I own everything. Period. The samba users have access via group.

Permissions on EVERYTHING recursively is 775, so owner and group has full blown permissions.

Yet - again - I own everything.

What's wrong with my setup?

Information below:

My share is "storage". Localbackup is simply a backup drive for my home directory and storagebackup is a backup drive for my samba (storage) drive. All Samba users are a member of SambaShare group.

```
jason@Area51:/media$ ls -l
total 20
lrwxrwxrwx  1 root  root          6 2009-04-29 22:52 cdrom -> cdrom0
drwxr-xr-x  2 root  root       4096 2009-04-29 22:52 cdrom0
drwxr-xr-x  2 root  root       4096 2009-04-29 22:52 cdrom1
drwxr-xr-x 79 jason jason      4096 2009-10-18 04:52 localbackup
drwxrwxr-x 46 jason sambashare 4096 2009-09-18 23:09 storage
drwxrwxr-x 46 jason sambashare 4096 2009-09-18 23:09 storagebackup
jason@Area51:/media$ 

```

As you can see, users curt/tyler/pam all are group owned to their respective folders. This is on my storage share, which goes to my primary 250gb drive that Samba is linked to. When users hit Start - Run - \\Area51 on their computer, they're hitting "storage" that you see below.

```
jason@Area51:/media$ cd storage
jason@Area51:/media/storage$ ls -l
total 28
drwxrwxr-x  4 jason user       4096 2009-10-15 16:49 backup_data
drwxrwxr-x  9 jason curt       4096 2009-10-17 13:54 curt
drwxrwxr-x  4 jason jason      4096 2009-03-05 23:12 jason
drwxrwxr-x  2 jason sambashare 4096 2008-12-12 23:55 lost+found
drwxrwxr-x 29 jason pam        4096 2009-10-15 03:00 pam
drwxrwxr-x  4 jason sambashare 4096 2009-10-16 00:49 public
drwxrwxr-x 16 jason tyler      4096 2009-10-12 03:20 tyler
jason@Area51:/media/storage$ 

```

My rsync script:

```
#!/bin/bash
rsync -a --progress --delete --exclude=.gvfs /home/jason/ /media/localbackup/
rsync -a --progress --delete /media/storage/ /media/storagebackup/

```

Executing my backup script WITHOUT root.

```
jason@Area51:/media$ backup
sending incremental file list

sent 4595890 bytes  received 4211 bytes  3066734.00 bytes/sec
total size is 253235399132  speedup is 55049.97
sending incremental file list

sent 604744 bytes  received 1009 bytes  403835.33 bytes/sec
total size is 89327274228  speedup is 147464.85
sending incremental file list

sent 189235 bytes  received 112 bytes  378694.00 bytes/sec
total size is 16940840791  speedup is 89469.81
sending incremental file list

sent 1253721 bytes  received 2342 bytes  837375.33 bytes/sec
total size is 153140438431  speedup is 121920.99
jason@Area51:/media$ 

```

```
jason@Area51:/media$ cd storagebackup
jason@Area51:/media/storagebackup$ ls -l
total 28
drwxrwxr-x  4 jason user       4096 2009-10-15 16:49 backup_data
drwxrwxr-x  9 jason sambashare 4096 2009-10-17 13:54 curt
drwxrwxr-x  4 jason jason      4096 2009-03-05 23:12 jason
drwxrwxr-x  2 jason sambashare 4096 2008-12-12 23:55 lost+found
drwxrwxr-x 29 jason sambashare 4096 2009-10-15 03:00 pam
drwxrwxr-x  4 jason sambashare 4096 2009-10-16 00:49 public
drwxrwxr-x 16 jason sambashare 4096 2009-10-12 03:20 tyler
jason@Area51:/media/storagebackup$ 

```

And yet, group permissions did not carry over, despite me being the core owner of all of the folders in question. Not only that, but jason is a member of sambashare - a group that has permission @ 775 octal rights.

EDIT!!!! - It worked now. The key part I was missing was I need to be a member of that group in order to make it work. So Stuart was completely right, I was just misunderstanding and only looking at the owner when he was deliberately saying I need the proper rights, which it appears I didn't have.

As a test, I used my generic samba account as a test. I added "jason" and "user" to the group "user", and then I assigned "user" to be the group to the share known as "backup_data". Then I ran my rsync script without root priviledges. And I got:


```

jason@Area51:/media/storagebackup$ ls -l
total 28
**_drwxrwxr-x  4 jason user       4096 2009-10-15 16:49 backup_data_**
drwxrwxr-x  9 jason sambashare 4096 2009-10-17 13:54 curt
drwxrwxr-x  4 jason jason      4096 2009-03-05 23:12 jason
drwxrwxr-x  2 jason sambashare 4096 2008-12-12 23:55 lost+found
drwxrwxr-x 29 jason sambashare 4096 2009-10-15 03:00 pam
drwxrwxr-x  4 jason sambashare 4096 2009-10-16 00:49 public
drwxrwxr-x 16 jason sambashare 4096 2009-10-12 03:20 tyler
jason@Area51:/media/storagebackup$
```

---

### Post by CharlesA on 2009-10-19
No more insight into this? Seems both of us are having the same problem, and the permissions are set correctly.

---

### Post by Roasted on 2009-10-19
Me? My problem is fine. 

There were a couple of things I didn't realize.

When you create a user, a group with the same name as the user you just created gets put on the system. However - it has no users in it.

I wanted to use a system where I was the owner, but the user in question that was using each share (1 user per share) would get access from group permissions.

The problem was, I wasn't adding the user to the group. I didn't realize when I create a user called "fred" that Ubuntu indeed added a group called "fred", but also did not add anybody to that group. I can't help but to wonder if it was for a mix between convenience reasons and security reasons.

Then, that's fine. The user can access the share and everything is good. Right? Wrong. When I was using jason:fred (with fred being a member of the group fred) I still needed root access to copy the entire folder over with full -a permissions.

The problem? Even though I own the folder, I had to be a member of the group too. 

When I own the folder, I can do anything I want to the folder.
But when I want to change group permissions on that folder, I need to be in that group as well.

```
drwxrwxr-x  4 jason user       4096 2009-10-15 16:49 backup_data
drwxrwxr-x  9 jason curt       4096 2009-10-17 13:54 curt
drwxrwxr-x  4 jason jason      4096 2009-03-05 23:12 jason
drwxrwxr-x  2 jason sambashare 4096 2008-12-12 23:55 lost+found
drwxrwxr-x 29 jason pam        4096 2009-10-15 03:00 pam
drwxrwxr-x  4 jason sambashare 4096 2009-10-16 00:49 public
drwxrwxr-x 16 jason tyler      4096 2009-10-12 03:20 tyler

```

In short, with jason/curt/tyler/pam, that's 4 users. But there's also 4 groups - each with the same name as the user.

jason + tyler are a member of tyler
jason + curt are a member of curt
jason + pam are a member of pam
jason + user are a member of user

That enables jason, WITHOUT ROOT, to have full blown access to the entire share because:

A - I own it.
B - I'm group assigned to it.

So when I run rsync -a, I can indeed rsync EVERYTHING perfectly fine - including the group - because I'm a member of the group.

---

### Post by Roasted on 2009-10-19
Is there any way to preserve the owner without running root?

I decided to make some changes from what I posted before. Mostly because when users write data to their samba share, it comes down as fred:fred (the user) and NOT jason:fred (I'm jason). 

I'm not the one writing the data. So therefore I am not the owner.

I am however, a member of all of the user groups in question.

Pam/Curt/Tyler all have a share, and a group with their respective name. I am a member of each of their individual groups.

Their individual shares are owned by jason:themselves.

aka - jason : pam, jason : curt, jason : tyler.

Inside the shares, all of the data is owned by pam : pam, curt : curt, tyler : tyler, etc. I can access this data due to 775 permissions, because I am a member of each of the individual groups.

When I run my rsync script, WITH THE -a switch, it pulls over as me being the owner of the files.

I understand this because on my backup drive, I'm writing the data. I'm the one taking the data from storage and putting it on storagebackup (completely different hard drive). The group stays intact, but the owner changes. Instead of pam : pam owning it, since I am taking the files and moving them based on rsyncing, it comes down as jason : pam.

Is there any way to preserve the owner? It's no big deal, but I'm just curious.

EDIT - Is preserving ownership the one area where you NEED root permissions? I had just assumed -a didn't need root permissions. But I guess in my case, I kind of do if I don't own the files inside. After all, these files are created by pam/curt/tyler via samba, so they come down as the owner. As a result, jason (me) I don't own them or I could just execute the rsync command with -a and keep the owner intact since I'd be the owner. Am I on the right path? Is that right?

-I can keep the group permissions because I'm a member of each group.
-I can't keep the owner because I am not the actual owner, nor am I root.

rsync man page - 

 -g, --group                 preserve group
 -o, --owner                 preserve owner (root only)
 -p, --perms                 preserve permissions

---

### Post by CharlesA on 2009-10-20
That was what I was running into as well. I am a member of the group(s) who had rw permission on those folders as well, but it was changing the owner unless I ran it as root.

I'm guessing that you **need** to run as root for it not change ownership, since I haven't found anything that says otherwise using google and searching the forums here.

No idea what sort of setup StuartN has, but it seems to work for him, but not us. *shrug*

---

### Post by StuartN on 2009-10-20
I suggest you run rsync with the -i option and examine all the permissions at the first discrepancy, so if you were syncing from /mnt/a to /mnt/b then you would **ls -ld /mnt/b** (for the directory permissions) and **ls -ld /mnt/b** (for the files within it).

(NB. using **cp -p** manually on the first file should preserve the permissions, owner etc as rsync does with the -a option, but might give you an additional error message).

If a share is automatically mounted by Gnome (Connect to server) or Nautilus, then not all the permissions work correctly - this is noted as a bug, e.g. [https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/215499](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/215499). Mounting the share manually with the uid=your_username and gid=your_group options does work.

---

### Post by CharlesA on 2009-10-20
Copied them over using: cp -av /array/clone /sync

Here is the log:

```
`clone' -> `/sync/clone'
`clone/Osiris_Windows7RC' -> `/sync/clone/Osiris_Windows7RC'
`clone/Osiris_Windows7RC/hda-hidden-data-after-mbr' -> `/sync/clone/Osiris_Windows7RC/hda-hidden-data-after-mbr'
`clone/Osiris_Windows7RC/hda2.ntfs-ptcimg.gz.aa' -> `/sync/clone/Osiris_Windows7RC/hda2.ntfs-ptcl-img.gz.aa'
`clone/Osiris_Windows7RC/Info-packages.txt' -> `/sync/clone/Osiris_Windows7RC/Info-packages.txt'
`clone/Osiris_Windows7RC/hda-pt.parted' -> `/sync/clone/Osiris_Windows7RC/hda-pt.parted'
`clone/Osiris_Windows7RC/parts' -> `/sync/clone/Osiris_Windows7RC/parts'
`clone/Osiris_Windows7RC/disk' -> `/sync/clone/Osiris_Windows7RC/disk'
`clone/Osiris_Windows7RC/hda-pt.sf' -> `/sync/clone/Osiris_Windows7RC/hda-pt.sf'
`clone/Osiris_Windows7RC/Info-lshw.txt' -> `/sync/clone/Osiris_Windows7RC/Info-lshw.txt'
`clone/Osiris_Windows7RC/Info-dmi.txt' -> `/sync/clone/Osiris_Windows7RC/Info-dmi.txt'
`clone/Osiris_Windows7RC/hda2.ntfs-ptcl-img.gz.ac' -> `/sync/clone/Osiris_Windows7RC/hda2.ntfs-ptcl-img.gz.ac'
`clone/Osiris_Windows7RC/hda2.ntfs-ptcl-img.gz.ab' -> `/sync/clone/Osiris_Windows7RC/hda2.ntfs-ptcl-img.gz.ab'
`clone/Osiris_Windows7RC/hda-mbr' -> `/sync/clone/Osiris_Windows7RC/hda-mbr'
`clone/Osiris_Windows7RC/hda-chs.sf' -> `/sync/clone/Osiris_Windows7RC/hda-chs.sf'
`clone/Osiris_Windows7RC/hda1.ntfs-ptcl-img.gz.aa' -> `/sync/clone/Osiris_Windows7RC/hda1.ntfs-ptcl-img.gz.aa'
`clone/Osiris_XP_Clean' -> `/sync/clone/Osiris_XP_Clean'
`clone/Osiris_XP_Clean/hda-hidden-data-after-mbr' -> `/sync/clone/Osiris_XP_Clean/hda-hidden-data-after-mbr'
`clone/Osiris_XP_Clean/Info-packages.txt' -> `/sync/clone/Osiris_XP_Clean/Info-packages.txt'
`clone/Osiris_XP_Clean/hda-pt.parted' -> `/sync/clone/Osiris_XP_Clean/hda-pt.parted'
`clone/Osiris_XP_Clean/parts' -> `/sync/clone/Osiris_XP_Clean/parts'
`clone/Osiris_XP_Clean/disk' -> `/sync/clone/Osiris_XP_Clean/disk'
`clone/Osiris_XP_Clean/hda-pt.sf' -> `/sync/clone/Osiris_XP_Clean/hda-pt.sf'
`clone/Osiris_XP_Clean/Info-lshw.txt' -> `/sync/clone/Osiris_XP_Clean/Info-lshw.txt'
`clone/Osiris_XP_Clean/Info-dmi.txt' -> `/sync/clone/Osiris_XP_Clean/Info-dmi.txt'
`clone/Osiris_XP_Clean/hda1.ntfs-ptcl-img.gz.ab' -> `/sync/clone/Osiris_XP_Clean/hda1.ntfs-ptcl-img.gz.ab'
`clone/Osiris_XP_Clean/hda-mbr' -> `/sync/clone/Osiris_XP_Clean/hda-mbr'
`clone/Osiris_XP_Clean/hda-chs.sf' -> `/sync/clone/Osiris_XP_Clean/hda-chs.sf'
`clone/Osiris_XP_Clean/hda1.ntfs-ptcl-img.gz.aa' -> `/sync/clone/Osiris_XP_Clean/hda1.ntfs-ptcl-img.gz.aa'
`clone/Loki_XP_Clean_9_10_2009' -> `/sync/clone/Loki_XP_Clean_9_10_2009'
`clone/Loki_XP_Clean_9_10_2009/hda-hidden-data-after-mbr' -> `/sync/clone/Loki_XP_Clean_9_10_2009/hda-hidden-data-after-mbr'
`clone/Loki_XP_Clean_9_10_2009/Info-packages.txt' -> `/sync/clone/Loki_XP_Clean_9_10_2009/Info-packages.txt'
`clone/Loki_XP_Clean_9_10_2009/hda-pt.parted' -> `/sync/clone/Loki_XP_Clean_9_10_2009/hda-pt.parted'
`clone/Loki_XP_Clean_9_10_2009/parts' -> `/sync/clone/Loki_XP_Clean_9_10_2009/parts'
`clone/Loki_XP_Clean_9_10_2009/disk' -> `/sync/clone/Loki_XP_Clean_9_10_2009/disk'
`clone/Loki_XP_Clean_9_10_2009/hda-pt.sf' -> `/sync/clone/Loki_XP_Clean_9_10_2009/hda-pt.sf'
`clone/Loki_XP_Clean_9_10_2009/Info-lshw.txt' -> `/sync/clone/Loki_XP_Clean_9_10_2009/Info-lshw.txt'
`clone/Loki_XP_Clean_9_10_2009/Info-dmi.txt' -> `/sync/clone/Loki_XP_Clean_9_10_2009/Info-dmi.txt'
`clone/Loki_XP_Clean_9_10_2009/hda-mbr' -> `/sync/clone/Loki_XP_Clean_9_10_2009/hda-mbr'
`clone/Loki_XP_Clean_9_10_2009/hda-chs.sf' -> `/sync/clone/Loki_XP_Clean_9_10_2009/hda-chs.sf'
`clone/Loki_XP_Clean_9_10_2009/hda1.ntfs-ptcl-img.gz.aa' -> `/sync/clone/Loki_XP_Clean_9_10_2009/hda1.ntfs-ptcl-img.gz.aa'
`clone/Osiris_Ubuntu_Clean' -> `/sync/clone/Osiris_Ubuntu_Clean'
`clone/Osiris_Ubuntu_Clean/hda-hidden-data-after-mbr' -> `/sync/clone/Osiris_Ubuntu_Clean/hda-hidden-data-after-mbr'
`clone/Osiris_Ubuntu_Clean/osiris-root.ext3-ptcl-img.gz.aa' -> `/sync/clone/Osiris_Ubuntu_Clean/osiris-root.ext3-ptcl-img.gz.aa'
`clone/Osiris_Ubuntu_Clean/Info-packages.txt' -> `/sync/clone/Osiris_Ubuntu_Clean/Info-packages.txt'
`clone/Osiris_Ubuntu_Clean/hda-pt.parted' -> `/sync/clone/Osiris_Ubuntu_Clean/hda-pt.parted'
`clone/Osiris_Ubuntu_Clean/parts' -> `/sync/clone/Osiris_Ubuntu_Clean/parts'
`clone/Osiris_Ubuntu_Clean/disk' -> `/sync/clone/Osiris_Ubuntu_Clean/disk'
`clone/Osiris_Ubuntu_Clean/hda-pt.sf' -> `/sync/clone/Osiris_Ubuntu_Clean/hda-pt.sf'
`clone/Osiris_Ubuntu_Clean/Info-lshw.txt' -> `/sync/clone/Osiris_Ubuntu_Clean/Info-lshw.txt'
`clone/Osiris_Ubuntu_Clean/swappt-osiris-swap_1.info' -> `/sync/clone/Osiris_Ubuntu_Clean/swappt-osiris-swap_1.info'
`clone/Osiris_Ubuntu_Clean/lvm_logv.list' -> `/sync/clone/Osiris_Ubuntu_Clean/lvm_logv.list'
`clone/Osiris_Ubuntu_Clean/Info-dmi.txt' -> `/sync/clone/Osiris_Ubuntu_Clean/Info-dmi.txt'
`clone/Osiris_Ubuntu_Clean/hda5.ext2-ptcl-img.gz.aa' -> `/sync/clone/Osiris_Ubuntu_Clean/hda5.ext2-ptcl-img.gz.aa'
`clone/Osiris_Ubuntu_Clean/lvm_vg_dev.list' -> `/sync/clone/Osiris_Ubuntu_Clean/lvm_vg_dev.list'
`clone/Osiris_Ubuntu_Clean/hda-mbr' -> `/sync/clone/Osiris_Ubuntu_Clean/hda-mbr'
`clone/Osiris_Ubuntu_Clean/hda-chs.sf' -> `/sync/clone/Osiris_Ubuntu_Clean/hda-chs.sf'
`clone/Osiris_Ubuntu_Clean/lvm_osiris.conf' -> `/sync/clone/Osiris_Ubuntu_Clean/lvm_osiris.conf'
`clone/Osiris_Ubuntu_Gnome' -> `/sync/clone/Osiris_Ubuntu_Gnome'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749948' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749948'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749944' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749944'
`clone/Osiris_Ubuntu_Gnome/hda-hidden-data-after-mbr' -> `/sync/clone/Osiris_Ubuntu_Gnome/hda-hidden-data-after-mbr'
`clone/Osiris_Ubuntu_Gnome/osiris-root.ext3-ptcl-img.gz.aa' -> `/sync/clone/Osiris_Ubuntu_Gnome/osiris-root.ext3-ptcl-img.gz.aa'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749940' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749940'
`clone/Osiris_Ubuntu_Gnome/Info-packages.txt' -> `/sync/clone/Osiris_Ubuntu_Gnome/Info-packages.txt'
`clone/Osiris_Ubuntu_Gnome/hda-pt.parted' -> `/sync/clone/Osiris_Ubuntu_Gnome/hda-pt.parted'
`clone/Osiris_Ubuntu_Gnome/parts' -> `/sync/clone/Osiris_Ubuntu_Gnome/parts'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749945' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749945'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749943' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749943'
`clone/Osiris_Ubuntu_Gnome/disk' -> `/sync/clone/Osiris_Ubuntu_Gnome/disk'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749932' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749932'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749936' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749936'
`clone/Osiris_Ubuntu_Gnome/hda-pt.sf' -> `/sync/clone/Osiris_Ubuntu_Gnome/hda-pt.sf'
`clone/Osiris_Ubuntu_Gnome/Info-lshw.txt' -> `/sync/clone/Osiris_Ubuntu_Gnome/Info-lshw.txt'
`clone/Osiris_Ubuntu_Gnome/swappt-osiris-swap_1.info' -> `/sync/clone/Osiris_Ubuntu_Gnome/swappt-osiris-swap_1.info'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749937' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749937'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749942' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749942'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749933' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749933'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749934' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749934'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749950' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749950'
`clone/Osiris_Ubuntu_Gnome/lvm_logv.list' -> `/sync/clone/Osiris_Ubuntu_Gnome/lvm_logv.list'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749946' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749946'
`clone/Osiris_Ubuntu_Gnome/Info-dmi.txt' -> `/sync/clone/Osiris_Ubuntu_Gnome/Info-dmi.txt'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749935' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749935'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749938' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749938'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749939' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749939'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749941' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749941'
`clone/Osiris_Ubuntu_Gnome/hda5.ext2-ptcl-img.gz.aa' -> `/sync/clone/Osiris_Ubuntu_Gnome/hda5.ext2-ptcl-img.gz.aa'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749931' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749931'
`clone/Osiris_Ubuntu_Gnome/lvm_vg_dev.list' -> `/sync/clone/Osiris_Ubuntu_Gnome/lvm_vg_dev.list'
`clone/Osiris_Ubuntu_Gnome/hda-mbr' -> `/sync/clone/Osiris_Ubuntu_Gnome/hda-mbr'
`clone/Osiris_Ubuntu_Gnome/hda-chs.sf' -> `/sync/clone/Osiris_Ubuntu_Gnome/hda-chs.sf'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749949' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749949'
`clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749947' -> `/sync/clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749947'
`clone/Thor_Ubuntu_10_17_09' -> `/sync/clone/Thor_Ubuntu_10_17_09'
`clone/Thor_Ubuntu_10_17_09/Info-packages.txt' -> `/sync/clone/Thor_Ubuntu_10_17_09/Info-packages.txt'
`clone/Thor_Ubuntu_10_17_09/parts' -> `/sync/clone/Thor_Ubuntu_10_17_09/parts'
`clone/Thor_Ubuntu_10_17_09/disk' -> `/sync/clone/Thor_Ubuntu_10_17_09/disk'
`clone/Thor_Ubuntu_10_17_09/sda-mbr' -> `/sync/clone/Thor_Ubuntu_10_17_09/sda-mbr'
`clone/Thor_Ubuntu_10_17_09/sda-chs.sf' -> `/sync/clone/Thor_Ubuntu_10_17_09/sda-chs.sf'
`clone/Thor_Ubuntu_10_17_09/Info-lshw.txt' -> `/sync/clone/Thor_Ubuntu_10_17_09/Info-lshw.txt'
`clone/Thor_Ubuntu_10_17_09/swappt-sda5.info' -> `/sync/clone/Thor_Ubuntu_10_17_09/swappt-sda5.info'
`clone/Thor_Ubuntu_10_17_09/Info-dmi.txt' -> `/sync/clone/Thor_Ubuntu_10_17_09/Info-dmi.txt'
`clone/Thor_Ubuntu_10_17_09/sda-pt.parted' -> `/sync/clone/Thor_Ubuntu_10_17_09/sda-pt.parted'
`clone/Thor_Ubuntu_10_17_09/sda-hidden-data-after-mbr' -> `/sync/clone/Thor_Ubuntu_10_17_09/sda-hidden-data-after-mbr'
`clone/Thor_Ubuntu_10_17_09/sda-pt.sf' -> `/sync/clone/Thor_Ubuntu_10_17_09/sda-pt.sf'
`clone/Thor_Ubuntu_10_17_09/sda1.ext3-ptcl-img.gz.aa' -> `/sync/clone/Thor_Ubuntu_10_17_09/sda1.ext3-ptcl-img.gz.aa'
`clone/Osiris_Ubuntu_KDE' -> `/sync/clone/Osiris_Ubuntu_KDE'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372982' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372982'
`clone/Osiris_Ubuntu_KDE/hda-hidden-data-after-mbr' -> `/sync/clone/Osiris_Ubuntu_KDE/hda-hidden-data-after-mbr'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372988' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372988'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372971' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372971'
`clone/Osiris_Ubuntu_KDE/osiris-root.ext3-ptcl-img.gz.aa' -> `/sync/clone/Osiris_Ubuntu_KDE/osiris-root.ext3-ptcl-img.gz.aa'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372975' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372975'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372981' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372981'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372974' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372974'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372986' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372986'
`clone/Osiris_Ubuntu_KDE/Info-packages.txt' -> `/sync/clone/Osiris_Ubuntu_KDE/Info-packages.txt'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372973' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372973'
`clone/Osiris_Ubuntu_KDE/hda-pt.parted' -> `/sync/clone/Osiris_Ubuntu_KDE/hda-pt.parted'
`clone/Osiris_Ubuntu_KDE/parts' -> `/sync/clone/Osiris_Ubuntu_KDE/parts'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372987' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372987'
`clone/Osiris_Ubuntu_KDE/disk' -> `/sync/clone/Osiris_Ubuntu_KDE/disk'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372984' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372984'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372980' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372980'
`clone/Osiris_Ubuntu_KDE/hda-pt.sf' -> `/sync/clone/Osiris_Ubuntu_KDE/hda-pt.sf'
`clone/Osiris_Ubuntu_KDE/Info-lshw.txt' -> `/sync/clone/Osiris_Ubuntu_KDE/Info-lshw.txt'
`clone/Osiris_Ubuntu_KDE/swappt-osiris-swap_1.info' -> `/sync/clone/Osiris_Ubuntu_KDE/swappt-osiris-swap_1.info'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372989' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372989'
`clone/Osiris_Ubuntu_KDE/lvm_logv.list' -> `/sync/clone/Osiris_Ubuntu_KDE/lvm_logv.list'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372972' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372972'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372976' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372976'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372985' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372985'
`clone/Osiris_Ubuntu_KDE/Info-dmi.txt' -> `/sync/clone/Osiris_Ubuntu_KDE/Info-dmi.txt'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372979' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372979'
`clone/Osiris_Ubuntu_KDE/hda5.ext2-ptcl-img.gz.aa' -> `/sync/clone/Osiris_Ubuntu_KDE/hda5.ext2-ptcl-img.gz.aa'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372978' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372978'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372990' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372990'
`clone/Osiris_Ubuntu_KDE/lvm_vg_dev.list' -> `/sync/clone/Osiris_Ubuntu_KDE/lvm_vg_dev.list'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372977' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372977'
`clone/Osiris_Ubuntu_KDE/hda-mbr' -> `/sync/clone/Osiris_Ubuntu_KDE/hda-mbr'
`clone/Osiris_Ubuntu_KDE/hda-chs.sf' -> `/sync/clone/Osiris_Ubuntu_KDE/hda-chs.sf'
`clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372983' -> `/sync/clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372983'
`clone/Thor_Ubuntu_10_12_09' -> `/sync/clone/Thor_Ubuntu_10_12_09'
`clone/Thor_Ubuntu_10_12_09/Info-packages.txt' -> `/sync/clone/Thor_Ubuntu_10_12_09/Info-packages.txt'
`clone/Thor_Ubuntu_10_12_09/parts' -> `/sync/clone/Thor_Ubuntu_10_12_09/parts'
`clone/Thor_Ubuntu_10_12_09/disk' -> `/sync/clone/Thor_Ubuntu_10_12_09/disk'
`clone/Thor_Ubuntu_10_12_09/sda-mbr' -> `/sync/clone/Thor_Ubuntu_10_12_09/sda-mbr'
`clone/Thor_Ubuntu_10_12_09/sda-chs.sf' -> `/sync/clone/Thor_Ubuntu_10_12_09/sda-chs.sf'
`clone/Thor_Ubuntu_10_12_09/Info-lshw.txt' -> `/sync/clone/Thor_Ubuntu_10_12_09/Info-lshw.txt'
`clone/Thor_Ubuntu_10_12_09/swappt-sda5.info' -> `/sync/clone/Thor_Ubuntu_10_12_09/swappt-sda5.info'
`clone/Thor_Ubuntu_10_12_09/Info-dmi.txt' -> `/sync/clone/Thor_Ubuntu_10_12_09/Info-dmi.txt'
`clone/Thor_Ubuntu_10_12_09/sda-pt.parted' -> `/sync/clone/Thor_Ubuntu_10_12_09/sda-pt.parted'
`clone/Thor_Ubuntu_10_12_09/sda-hidden-data-after-mbr' -> `/sync/clone/Thor_Ubuntu_10_12_09/sda-hidden-data-after-mbr'
`clone/Thor_Ubuntu_10_12_09/sda-pt.sf' -> `/sync/clone/Thor_Ubuntu_10_12_09/sda-pt.sf'
`clone/Thor_Ubuntu_10_12_09/sda1.ext3-ptcl-img.gz.aa' -> `/sync/clone/Thor_Ubuntu_10_12_09/sda1.ext3-ptcl-img.gz.aa'

```

No errors.

Yet when I checks the perms on the clone directory:

```
drwxrwx---  10 charles clone     4096 2009-10-17 20:36 clone
```

and on the files and folders inside that directory:
```
charles@thor:/sync$ ls -lR clone
clone:
total 32
drwxrwx--- 2 charles clone 4096 2009-10-12 13:59 Loki_XP_Clean_9_10_2009
drwxrwx--- 2 charles clone 4096 2009-10-12 14:02 Osiris_Ubuntu_Clean
drwxrwx--- 2 charles clone 4096 2009-10-17 18:31 Osiris_Ubuntu_Gnome
drwxrwx--- 2 charles clone 4096 2009-10-16 20:04 Osiris_Ubuntu_KDE
drwxrwx--- 2 charles clone 4096 2009-10-14 20:18 Osiris_Windows7RC
drwxrwx--- 2 charles clone 4096 2009-10-12 14:02 Osiris_XP_Clean
drwxrwx--- 2 charles clone 4096 2009-10-12 14:02 Thor_Ubuntu_10_12_09
drwxrwx--- 2 charles clone 4096 2009-10-17 20:26 Thor_Ubuntu_10_17_09

clone/Loki_XP_Clean_9_10_2009:
total 1989464
-rwxrwx--- 1 charles clone          4 2009-10-10 19:36 disk
-rwxrwx--- 1 charles clone 2035121739 2009-10-10 19:35 hda1.ntfs-ptcl-img.gz.aa
-rwxrwx--- 1 charles clone         37 2009-10-10 19:24 hda-chs.sf
-rwxrwx--- 1 charles clone      31744 2009-10-10 19:24 hda-hidden-data-after-mbr
-rwxrwx--- 1 charles clone        512 2009-10-10 19:24 hda-mbr
-rwxrwx--- 1 charles clone        260 2009-10-10 19:24 hda-pt.parted
-rwxrwx--- 1 charles clone        259 2009-10-10 19:24 hda-pt.sf
-rwxrwx--- 1 charles clone      15929 2009-10-10 19:36 Info-dmi.txt
-rwxrwx--- 1 charles clone      14393 2009-10-10 19:36 Info-lshw.txt
-rwxrwx--- 1 charles clone        285 2009-10-10 19:36 Info-packages.txt
-rwxrwx--- 1 charles clone          5 2009-10-10 19:36 parts

```

```
cd+++++++++ clone/
cd+++++++++ clone/Loki_XP_Clean_9_10_2009/
>f+++++++++ clone/Loki_XP_Clean_9_10_2009/Info-dmi.txt

       15929 100%    0.00kB/s    0:00:00  
       15929 100%    0.00kB/s    0:00:00 (xfer#1, to-check=146/156)
>f+++++++++ clone/Loki_XP_Clean_9_10_2009/Info-lshw.txt

       14393 100%   13.73MB/s    0:00:00  
       14393 100%   13.73MB/s    0:00:00 (xfer#2, to-check=145/156)
>f+++++++++ clone/Loki_XP_Clean_9_10_2009/Info-packages.txt

         285 100%   46.39kB/s    0:00:00  
         285 100%   46.39kB/s    0:00:00 (xfer#3, to-check=144/156)
>f+++++++++ clone/Loki_XP_Clean_9_10_2009/disk

           4 100%    0.65kB/s    0:00:00  
           4 100%    0.65kB/s    0:00:00 (xfer#4, to-check=143/156)
>f+++++++++ clone/Loki_XP_Clean_9_10_2009/hda-chs.sf

          37 100%    5.16kB/s    0:00:00  
          37 100%    5.16kB/s    0:00:00 (xfer#5, to-check=142/156)
>f+++++++++ clone/Loki_XP_Clean_9_10_2009/hda-hidden-data-after-mbr

       31744 100%    4.32MB/s    0:00:00  
       31744 100%    4.32MB/s    0:00:00 (xfer#6, to-check=141/156)
>f+++++++++ clone/Loki_XP_Clean_9_10_2009/hda-mbr

         512 100%   33.33kB/s    0:00:00  
         512 100%   33.33kB/s    0:00:00 (xfer#7, to-check=140/156)
>f+++++++++ clone/Loki_XP_Clean_9_10_2009/hda-pt.parted

         260 100%   16.93kB/s    0:00:00  
         260 100%   16.93kB/s    0:00:00 (xfer#8, to-check=139/156)
>f+++++++++ clone/Loki_XP_Clean_9_10_2009/hda-pt.sf

         259 100%   16.86kB/s    0:00:00  
         259 100%   16.86kB/s    0:00:00 (xfer#9, to-check=138/156)
>f+++++++++ clone/Loki_XP_Clean_9_10_2009/hda1.ntfs-ptcl-img.gz.aa

       32768   0%    1.56MB/s    0:21:11  
    45219840   2%   43.12MB/s    0:00:45  
    93978624   4%   44.83MB/s    0:00:42  
   139526144   6%   44.37MB/s    0:00:41  
   185892864   9%   44.33MB/s    0:00:40  
   231505920  11%   44.41MB/s    0:00:39  
   278593536  13%   44.02MB/s    0:00:38  
   326402048  16%   44.54MB/s    0:00:37  
   373260288  18%   44.67MB/s    0:00:36  
   416317440  20%   44.06MB/s    0:00:35  
   458522624  22%   42.90MB/s    0:00:35  
   505970688  24%   42.81MB/s    0:00:34  
   550567936  27%   42.27MB/s    0:00:34  
   595623936  29%   42.75MB/s    0:00:32  
   641859584  31%   43.72MB/s    0:00:31  
   690257920  33%   43.97MB/s    0:00:29  
   739540992  36%   45.07MB/s    0:00:28  
   785448960  38%   42.94MB/s    0:00:28  
   805371904  39%   20.03MB/s    0:00:59  
   853606400  41%   20.00MB/s    0:00:57  
   902332416  44%   19.94MB/s    0:00:55  
   951091200  46%   20.87MB/s    0:00:50  
   997982208  49%   45.92MB/s    0:00:22  
  1045200896  51%   45.67MB/s    0:00:21  
  1091108864  53%   45.00MB/s    0:00:20  
  1137147904  55%   44.36MB/s    0:00:19  
  1180237824  57%   43.45MB/s    0:00:19  
  1208549376  59%   38.96MB/s    0:00:20  
  1234075648  60%   34.09MB/s    0:00:22  
  1268514816  62%   31.34MB/s    0:00:23  
  1292959744  63%   25.25MB/s    0:00:28  
  1327824896  65%   26.03MB/s    0:00:26  
  1356890112  66%   26.80MB/s    0:00:24  
  1368457216  67%   21.81MB/s    0:00:29  
  1408827392  69%   26.20MB/s    0:00:23  
  1439498240  70%   25.55MB/s    0:00:22  
  1470431232  72%   25.80MB/s    0:00:21  
  1505918976  73%   31.24MB/s    0:00:16  
  1532788736  75%   28.90MB/s    0:00:16  
  1544880128  75%   12.51MB/s    0:00:38  
  1589149696  78%   14.14MB/s    0:00:30  
  1632993280  80%   15.14MB/s    0:00:25  
  1679392768  82%   17.47MB/s    0:00:19  
  1726578688  84%   43.34MB/s    0:00:06  
  1774419968  87%   44.21MB/s    0:00:05  
  1822326784  89%   45.17MB/s    0:00:04  
  1869840384  91%   45.44MB/s    0:00:03  
  1912668160  93%   44.35MB/s    0:00:02  
  1940193280  95%   38.89MB/s    0:00:02  
  1964572672  96%   30.13MB/s    0:00:02  
  2010415104  98%   29.77MB/s    0:00:00  
  2035121739 100%   32.50MB/s    0:00:59 (xfer#10, to-check=137/156)
>f+++++++++ clone/Loki_XP_Clean_9_10_2009/parts

           5 100%    0.01kB/s    0:00:00  
           5 100%    0.01kB/s    0:00:00 (xfer#11, to-check=136/156)
cd+++++++++ clone/Osiris_Ubuntu_Clean/
>f+++++++++ clone/Osiris_Ubuntu_Clean/Info-dmi.txt

       13262 100%   14.68kB/s    0:00:00  
       13262 100%   14.68kB/s    0:00:00 (xfer#12, to-check=135/156)
>f+++++++++ clone/Osiris_Ubuntu_Clean/Info-lshw.txt

       16463 100%   18.15kB/s    0:00:00  
       16463 100%   18.15kB/s    0:00:00 (xfer#13, to-check=134/156)
>f+++++++++ clone/Osiris_Ubuntu_Clean/Info-packages.txt

         285 100%    0.31kB/s    0:00:00  
         285 100%    0.31kB/s    0:00:00 (xfer#14, to-check=133/156)
>f+++++++++ clone/Osiris_Ubuntu_Clean/disk

           4 100%    0.00kB/s    0:00:00  
           4 100%    0.00kB/s    0:00:00 (xfer#15, to-check=132/156)
>f+++++++++ clone/Osiris_Ubuntu_Clean/hda-chs.sf

          36 100%    0.04kB/s    0:00:00  
          36 100%    0.04kB/s    0:00:00 (xfer#16, to-check=131/156)
>f+++++++++ clone/Osiris_Ubuntu_Clean/hda-hidden-data-after-mbr

       31744 100%   34.56kB/s    0:00:00  
       31744 100%   34.56kB/s    0:00:00 (xfer#17, to-check=130/156)
>f+++++++++ clone/Osiris_Ubuntu_Clean/hda-mbr

         512 100%    0.55kB/s    0:00:00  
         512 100%    0.55kB/s    0:00:00 (xfer#18, to-check=129/156)
>f+++++++++ clone/Osiris_Ubuntu_Clean/hda-pt.parted

         424 100%    0.46kB/s    0:00:00  
         424 100%    0.46kB/s    0:00:00 (xfer#19, to-check=128/156)
>f+++++++++ clone/Osiris_Ubuntu_Clean/hda-pt.sf

         310 100%    0.33kB/s    0:00:00  
         310 100%    0.33kB/s    0:00:00 (xfer#20, to-check=127/156)
>f+++++++++ clone/Osiris_Ubuntu_Clean/hda5.ext2-ptcl-img.gz.aa

       32768   0%    0.00kB/s    0:00:00  
    12837042 100%   15.64MB/s    0:00:00 (xfer#21, to-check=126/156)
>f+++++++++ clone/Osiris_Ubuntu_Clean/lvm_logv.list

         257 100%    0.32kB/s    0:00:00  
         257 100%    0.32kB/s    0:00:00 (xfer#22, to-check=125/156)
>f+++++++++ clone/Osiris_Ubuntu_Clean/lvm_osiris.conf

        1421 100%    1.77kB/s    0:00:00  
        1421 100%    1.77kB/s    0:00:00 (xfer#23, to-check=124/156)
>f+++++++++ clone/Osiris_Ubuntu_Clean/lvm_vg_dev.list

          56 100%    0.07kB/s    0:00:00  
          56 100%    0.07kB/s    0:00:00 (xfer#24, to-check=123/156)
>f+++++++++ clone/Osiris_Ubuntu_Clean/osiris-root.ext3-ptcl-img.gz.aa

       32768   0%   40.40kB/s    1:56:56  
     8192000   2%    5.46MB/s    0:00:49  
    25952256   9%   10.19MB/s    0:00:24  
    38076416  13%   10.35MB/s    0:00:23  
    66617344  23%   14.09MB/s    0:00:15  
    88145920  31%   17.45MB/s    0:00:10  
   113311744  39%   17.80MB/s    0:00:09  
   128253952  45%   18.04MB/s    0:00:08  
   159186944  56%   18.38MB/s    0:00:06  
   170459136  60%   16.96MB/s    0:00:06  
   219250688  77%   23.41MB/s    0:00:02  
   267681792  94%   32.03MB/s    0:00:00  
   283538313 100%   21.17MB/s    0:00:12 (xfer#25, to-check=122/156)
>f+++++++++ clone/Osiris_Ubuntu_Clean/parts

          10 100%    0.03kB/s    0:00:00  
          10 100%    0.03kB/s    0:00:00 (xfer#26, to-check=121/156)
>f+++++++++ clone/Osiris_Ubuntu_Clean/swappt-osiris-swap_1.info

          53 100%    0.15kB/s    0:00:00  
          53 100%    0.15kB/s    0:00:00 (xfer#27, to-check=120/156)
cd+++++++++ clone/Osiris_Ubuntu_Gnome/
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749931

           0 100%    0.00kB/s    0:00:00 (xfer#28, to-check=119/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749932

           0 100%    0.00kB/s    0:00:00 (xfer#29, to-check=118/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749933

           0 100%    0.00kB/s    0:00:00 (xfer#30, to-check=117/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749934

           0 100%    0.00kB/s    0:00:00 (xfer#31, to-check=116/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749935

           0 100%    0.00kB/s    0:00:00 (xfer#32, to-check=115/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749936

           0 100%    0.00kB/s    0:00:00 (xfer#33, to-check=114/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749937

           0 100%    0.00kB/s    0:00:00 (xfer#34, to-check=113/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749938

           0 100%    0.00kB/s    0:00:00 (xfer#35, to-check=112/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749939

           0 100%    0.00kB/s    0:00:00 (xfer#36, to-check=111/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749940

           0 100%    0.00kB/s    0:00:00 (xfer#37, to-check=110/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749941

           0 100%    0.00kB/s    0:00:00 (xfer#38, to-check=109/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749942

           0 100%    0.00kB/s    0:00:00 (xfer#39, to-check=108/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749943

           0 100%    0.00kB/s    0:00:00 (xfer#40, to-check=107/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749944

           0 100%    0.00kB/s    0:00:00 (xfer#41, to-check=106/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749945

           0 100%    0.00kB/s    0:00:00 (xfer#42, to-check=105/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749946

           0 100%    0.00kB/s    0:00:00 (xfer#43, to-check=104/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749947

           0 100%    0.00kB/s    0:00:00 (xfer#44, to-check=103/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749948

           0 100%    0.00kB/s    0:00:00 (xfer#45, to-check=102/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749949

           0 100%    0.00kB/s    0:00:00 (xfer#46, to-check=101/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/.lvm_debian_4344_513749950

           0 100%    0.00kB/s    0:00:00 (xfer#47, to-check=100/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/Info-dmi.txt

       13262 100%   35.98kB/s    0:00:00  
       13262 100%   35.98kB/s    0:00:00 (xfer#48, to-check=99/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/Info-lshw.txt

       16821 100%   44.88kB/s    0:00:00  
       16821 100%   44.88kB/s    0:00:00 (xfer#49, to-check=98/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/Info-packages.txt

         285 100%    0.75kB/s    0:00:00  
         285 100%    0.75kB/s    0:00:00 (xfer#50, to-check=97/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/disk

           4 100%    0.01kB/s    0:00:00  
           4 100%    0.01kB/s    0:00:00 (xfer#51, to-check=96/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/hda-chs.sf

          37 100%    0.09kB/s    0:00:00  
          37 100%    0.09kB/s    0:00:00 (xfer#52, to-check=95/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/hda-hidden-data-after-mbr

       31744 100%   60.43kB/s    0:00:00  
       31744 100%   60.43kB/s    0:00:00 (xfer#53, to-check=94/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/hda-mbr

         512 100%    0.97kB/s    0:00:00  
         512 100%    0.97kB/s    0:00:00 (xfer#54, to-check=93/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/hda-pt.parted

         424 100%    0.81kB/s    0:00:00  
         424 100%    0.81kB/s    0:00:00 (xfer#55, to-check=92/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/hda-pt.sf

           0 100%    0.00kB/s    0:00:00 (xfer#56, to-check=91/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/hda5.ext2-ptcl-img.gz.aa

       32768   0%   61.54kB/s    0:03:31  
    13040781 100%   15.55MB/s    0:00:00 (xfer#57, to-check=90/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/lvm_logv.list

         257 100%    0.31kB/s    0:00:00  
         257 100%    0.31kB/s    0:00:00 (xfer#58, to-check=89/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/lvm_vg_dev.list

          56 100%    0.07kB/s    0:00:00  
          56 100%    0.07kB/s    0:00:00 (xfer#59, to-check=88/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/osiris-root.ext3-ptcl-img.gz.aa

       32768   0%   39.85kB/s    9:21:31  
     8781824   0%    8.38MB/s    0:02:35  
    54296576   4%   25.89MB/s    0:00:48  
    99942400   7%   31.77MB/s    0:00:38  
   147914752  11%   35.27MB/s    0:00:33  
   193167360  14%   43.96MB/s    0:00:25  
   238616576  17%   39.57MB/s    0:00:27  
   262471680  19%   34.89MB/s    0:00:30  
   289472512  21%   25.44MB/s    0:00:40  
   334430208  24%   25.39MB/s    0:00:38  
   379453440  28%   27.61MB/s    0:00:34  
   426311680  31%   32.13MB/s    0:00:27  
   472317952  35%   43.63MB/s    0:00:19  
   518881280  38%   44.01MB/s    0:00:18  
   567443456  42%   44.85MB/s    0:00:16  
   614531072  45%   44.91MB/s    0:00:15  
   654868480  48%   43.55MB/s    0:00:15  
   680558592  50%   38.57MB/s    0:00:16  
   715161600  53%   35.23MB/s    0:00:17  
   743997440  55%   30.87MB/s    0:00:18  
   777060352  57%   29.12MB/s    0:00:18  
   781516800  58%   11.96MB/s    0:00:45  
   826703872  61%   13.22MB/s    0:00:38  
   875069440  65%   15.53MB/s    0:00:29  
   922320896  68%   17.22MB/s    0:00:23  
   970457088  72%   45.07MB/s    0:00:08  
  1018232832  75%   45.69MB/s    0:00:06  
  1068793856  79%   46.22MB/s    0:00:05  
  1116635136  83%   46.36MB/s    0:00:04  
  1152417792  85%   43.40MB/s    0:00:04  
  1178402816  87%   38.20MB/s    0:00:04  
  1209958400  90%   33.66MB/s    0:00:03  
  1233453056  91%   27.86MB/s    0:00:03  
  1269039104  94%   27.82MB/s    0:00:02  
  1295810560  96%   27.87MB/s    0:00:01  
  1329397760  99%   28.22MB/s    0:00:00  
  1342646416 100%   31.32MB/s    0:00:40 (xfer#60, to-check=87/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/parts

          10 100%    0.02kB/s    0:00:00  
          10 100%    0.02kB/s    0:00:00 (xfer#61, to-check=86/156)
>f+++++++++ clone/Osiris_Ubuntu_Gnome/swappt-osiris-swap_1.info

          53 100%    0.10kB/s    0:00:00  
          53 100%    0.10kB/s    0:00:00 (xfer#62, to-check=85/156)
cd+++++++++ clone/Osiris_Ubuntu_KDE/
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372971

           0 100%    0.00kB/s    0:00:00 (xfer#63, to-check=84/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372972

           0 100%    0.00kB/s    0:00:00 (xfer#64, to-check=83/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372973

           0 100%    0.00kB/s    0:00:00 (xfer#65, to-check=82/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372974

           0 100%    0.00kB/s    0:00:00 (xfer#66, to-check=81/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372975

           0 100%    0.00kB/s    0:00:00 (xfer#67, to-check=80/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372976

           0 100%    0.00kB/s    0:00:00 (xfer#68, to-check=79/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372977

           0 100%    0.00kB/s    0:00:00 (xfer#69, to-check=78/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372978

           0 100%    0.00kB/s    0:00:00 (xfer#70, to-check=77/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372979

           0 100%    0.00kB/s    0:00:00 (xfer#71, to-check=76/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372980

           0 100%    0.00kB/s    0:00:00 (xfer#72, to-check=75/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372981

           0 100%    0.00kB/s    0:00:00 (xfer#73, to-check=74/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372982

           0 100%    0.00kB/s    0:00:00 (xfer#74, to-check=73/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372983

           0 100%    0.00kB/s    0:00:00 (xfer#75, to-check=72/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372984

           0 100%    0.00kB/s    0:00:00 (xfer#76, to-check=71/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372985

           0 100%    0.00kB/s    0:00:00 (xfer#77, to-check=70/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372986

           0 100%    0.00kB/s    0:00:00 (xfer#78, to-check=69/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372987

           0 100%    0.00kB/s    0:00:00 (xfer#79, to-check=68/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372988

           0 100%    0.00kB/s    0:00:00 (xfer#80, to-check=67/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372989

           0 100%    0.00kB/s    0:00:00 (xfer#81, to-check=66/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/.lvm_debian_4200_957372990

           0 100%    0.00kB/s    0:00:00 (xfer#82, to-check=65/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/Info-dmi.txt

       13262 100%   24.34kB/s    0:00:00  
       13262 100%   24.34kB/s    0:00:00 (xfer#83, to-check=64/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/Info-lshw.txt

       16821 100%   30.42kB/s    0:00:00  
       16821 100%   30.42kB/s    0:00:00 (xfer#84, to-check=63/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/Info-packages.txt

         285 100%    0.51kB/s    0:00:00  
         285 100%    0.51kB/s    0:00:00 (xfer#85, to-check=62/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/disk

           4 100%    0.01kB/s    0:00:00  
           4 100%    0.01kB/s    0:00:00 (xfer#86, to-check=61/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/hda-chs.sf

          37 100%    0.07kB/s    0:00:00  
          37 100%    0.07kB/s    0:00:00 (xfer#87, to-check=60/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/hda-hidden-data-after-mbr

       31744 100%   55.36kB/s    0:00:00  
       31744 100%   55.36kB/s    0:00:00 (xfer#88, to-check=59/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/hda-mbr

         512 100%    0.89kB/s    0:00:00  
         512 100%    0.89kB/s    0:00:00 (xfer#89, to-check=58/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/hda-pt.parted

         424 100%    0.74kB/s    0:00:00  
         424 100%    0.74kB/s    0:00:00 (xfer#90, to-check=57/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/hda-pt.sf

           0 100%    0.00kB/s    0:00:00 (xfer#91, to-check=56/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/hda5.ext2-ptcl-img.gz.aa

       32768   0%   55.85kB/s    0:03:49  
     9240576  71%    6.88MB/s    0:00:00  
    12842035 100%    9.05MB/s    0:00:01 (xfer#92, to-check=55/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/lvm_logv.list

         257 100%    3.39kB/s    0:00:00  
         257 100%    3.39kB/s    0:00:00 (xfer#93, to-check=54/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/lvm_vg_dev.list

          56 100%    0.73kB/s    0:00:00  
          56 100%    0.73kB/s    0:00:00 (xfer#94, to-check=53/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/osiris-root.ext3-ptcl-img.gz.aa

       32768   0%  405.06kB/s    0:44:56  
    15269888   1%    8.08MB/s    0:02:10  
    41484288   3%   12.35MB/s    0:01:23  
    68452352   6%   15.53MB/s    0:01:04  
    79757312   7%   14.28MB/s    0:01:09  
   105775104   9%   19.07MB/s    0:00:50  
   116719616  10%   17.03MB/s    0:00:55  
   143818752  13%   17.06MB/s    0:00:54  
   160202752  14%   18.77MB/s    0:00:48  
   201129984  18%   22.24MB/s    0:00:39  
   248348672  22%   31.40MB/s    0:00:26  
   299991040  27%   37.25MB/s    0:00:20  
   348684288  31%   44.97MB/s    0:00:16  
   394330112  36%   42.83MB/s    0:00:15  
   416874496  38%   34.49MB/s    0:00:19  
   445677568  40%   29.80MB/s    0:00:21  
   459046912  42%   22.57MB/s    0:00:27  
   506265600  46%   24.50MB/s    0:00:23  
   552108032  50%   32.23MB/s    0:00:16  
   599130112  54%   36.59MB/s    0:00:13  
   648052736  59%   45.06MB/s    0:00:09  
   695336960  63%   45.08MB/s    0:00:08  
   733806592  67%   43.32MB/s    0:00:08  
   763920384  69%   39.29MB/s    0:00:08  
   793706496  72%   34.73MB/s    0:00:08  
   828014592  75%   31.63MB/s    0:00:08  
   830013440  75%   17.31MB/s    0:00:14  
   855834624  78%   16.55MB/s    0:00:13  
   884015104  80%   16.00MB/s    0:00:12  
   915767296  83%   15.55MB/s    0:00:11  
   945061888  86%   26.89MB/s    0:00:05  
   977698816  89%   28.48MB/s    0:00:03  
  1004044288  91%   28.62MB/s    0:00:03  
  1039958016  95%   29.62MB/s    0:00:01  
  1069645824  97%   29.70MB/s    0:00:00  
  1092459705 100%   27.27MB/s    0:00:38 (xfer#95, to-check=52/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/parts

          10 100%    0.01kB/s    0:00:00  
          10 100%    0.01kB/s    0:00:00 (xfer#96, to-check=51/156)
>f+++++++++ clone/Osiris_Ubuntu_KDE/swappt-osiris-swap_1.info

          53 100%    0.07kB/s    0:00:00  
          53 100%    0.07kB/s    0:00:00 (xfer#97, to-check=50/156)
cd+++++++++ clone/Osiris_Windows7RC/
>f+++++++++ clone/Osiris_Windows7RC/Info-dmi.txt

       13262 100%   16.65kB/s    0:00:00  
       13262 100%   16.65kB/s    0:00:00 (xfer#98, to-check=49/156)
>f+++++++++ clone/Osiris_Windows7RC/Info-lshw.txt

       16877 100%   20.97kB/s    0:00:00  
       16877 100%   20.97kB/s    0:00:00 (xfer#99, to-check=48/156)
>f+++++++++ clone/Osiris_Windows7RC/Info-packages.txt

         285 100%    0.35kB/s    0:00:00  
         285 100%    0.35kB/s    0:00:00 (xfer#100, to-check=47/156)
>f+++++++++ clone/Osiris_Windows7RC/disk

           4 100%    0.00kB/s    0:00:00  
           4 100%    0.00kB/s    0:00:00 (xfer#101, to-check=46/156)
>f+++++++++ clone/Osiris_Windows7RC/hda-chs.sf

          37 100%    0.05kB/s    0:00:00  
          37 100%    0.05kB/s    0:00:00 (xfer#102, to-check=45/156)
>f+++++++++ clone/Osiris_Windows7RC/hda-hidden-data-after-mbr

       32768   3%   39.51kB/s    0:00:25  
     1048064 100%    1.20MB/s    0:00:00 (xfer#103, to-check=44/156)
>f+++++++++ clone/Osiris_Windows7RC/hda-mbr

         512 100%    0.60kB/s    0:00:00  
         512 100%    0.60kB/s    0:00:00 (xfer#104, to-check=43/156)
>f+++++++++ clone/Osiris_Windows7RC/hda-pt.parted

         323 100%    0.38kB/s    0:00:00  
         323 100%    0.38kB/s    0:00:00 (xfer#105, to-check=42/156)
>f+++++++++ clone/Osiris_Windows7RC/hda-pt.sf

           0 100%    0.00kB/s    0:00:00 (xfer#106, to-check=41/156)
>f+++++++++ clone/Osiris_Windows7RC/hda1.ntfs-ptcl-img.gz.aa

       32768   0%   38.32kB/s    0:03:51  
     6881280  77%    6.56MB/s    0:00:00  
     8904357 100%    8.14MB/s    0:00:01 (xfer#107, to-check=40/156)
>f+++++++++ clone/Osiris_Windows7RC/hda2.ntfs-ptcl-img.gz.aa

       32768   0%  695.65kB/s    0:50:14  
     9764864   0%    7.01MB/s    0:04:50  
    36995072   1%   15.16MB/s    0:02:12  
    47251456   2%   12.79MB/s    0:02:36  
    76349440   3%   14.90MB/s    0:02:12  
    88145920   4%   15.83MB/s    0:02:03  
   114851840   5%   15.72MB/s    0:02:03  
   125894656   6%   16.21MB/s    0:01:58  
   172097536   8%   21.43MB/s    0:01:27  
   218038272  10%   30.24MB/s    0:01:00  
   266240000  12%   35.26MB/s    0:00:50  
   314605568  15%   45.01MB/s    0:00:38  
   362577920  17%   45.41MB/s    0:00:37  
   378077184  18%   35.60MB/s    0:00:47  
   402128896  19%   30.23MB/s    0:00:54  
   410288128  19%   21.28MB/s    0:01:17  
   437059584  20%   16.57MB/s    0:01:37  
   449871872  21%   15.17MB/s    0:01:46  
   496336896  23%   19.90MB/s    0:01:18  
   543129600  25%   28.07MB/s    0:00:54  
   589332480  28%   32.17MB/s    0:00:45  
   635240448  30%   44.21MB/s    0:00:32  
   683966464  32%   44.75MB/s    0:00:30  
   732987392  34%   45.27MB/s    0:00:29  
   764706816  36%   41.80MB/s    0:00:31  
   796459008  37%   36.88MB/s    0:00:34  
   832864256  39%   34.05MB/s    0:00:36  
   860684288  41%   28.76MB/s    0:00:41  
   879296512  41%   23.76MB/s    0:00:50  
   921468928  43%   26.90MB/s    0:00:42  
   953745408  45%   26.02MB/s    0:00:42  
   982581248  46%   26.57MB/s    0:00:40  
  1011777536  48%   31.52MB/s    0:00:33  
  1041694720  49%   28.61MB/s    0:00:36  
  1065910272  50%   26.68MB/s    0:00:37  
  1092976640  52%   26.33MB/s    0:00:37  
  1127514112  53%   27.60MB/s    0:00:34  
  1156644864  55%   26.78MB/s    0:00:34  
  1186332672  56%   28.07MB/s    0:00:31  
  1214808064  57%   28.39MB/s    0:00:30  
  1249181696  59%   28.13MB/s    0:00:29  
  1272479744  60%   27.40MB/s    0:00:29  
  1301872640  62%   26.86MB/s    0:00:28  
  1332281344  63%   27.30MB/s    0:00:27  
  1364295680  65%   26.97MB/s    0:00:26  
  1390444544  66%   27.64MB/s    0:00:24  
  1419018240  67%   27.94MB/s    0:00:23  
  1437138944  68%   25.00MB/s    0:00:25  
  1474723840  70%   26.33MB/s    0:00:23  
  1503985664  71%   27.07MB/s    0:00:21  
  1536196608  73%   27.93MB/s    0:00:19  
  1566867456  74%   30.93MB/s    0:00:16  
  1596227584  76%   28.98MB/s    0:00:16  
  1627455488  77%   29.26MB/s    0:00:15  
  1659699200  79%   28.53MB/s    0:00:14  
  1690107904  80%   28.14MB/s    0:00:14  
  1723924480  82%   28.63MB/s    0:00:12  
  1756430336  83%   28.70MB/s    0:00:11  
  1787428864  85%   29.16MB/s    0:00:10  
  1810137088  86%   27.70MB/s    0:00:10  
  1839497216  87%   27.17MB/s    0:00:09  
  1869414400  89%   26.08MB/s    0:00:08  
  1904541696  90%   26.60MB/s    0:00:07  
  1937801216  92%   29.01MB/s    0:00:05  
  1967652864  93%   29.13MB/s    0:00:04  
  1996554240  95%   29.21MB/s    0:00:03  
  2026209280  96%   28.42MB/s    0:00:02  
  2056552448  98%   27.73MB/s    0:00:01  
  2089353216  99%   27.57MB/s    0:00:00  
  2097152000 100%   27.92MB/s    0:01:11 (xfer#108, to-check=39/156)
>f+++++++++ clone/Osiris_Windows7RC/hda2.ntfs-ptcl-img.gz.ab

       32768   0%  181.82kB/s    3:12:14  
    14483456   0%   10.11MB/s    0:03:21  
    35454976   1%   12.37MB/s    0:02:42  
    62160896   2%   15.88MB/s    0:02:05  
    72941568   3%   14.37MB/s    0:02:17  
    99385344   4%   18.10MB/s    0:01:47  
   111476736   5%   17.19MB/s    0:01:52  
   138215424   6%   17.19MB/s    0:01:51  
   145031168   6%   16.54MB/s    0:01:55  
   174129152   8%   16.52MB/s    0:01:53  
   187760640   8%   16.61MB/s    0:01:52  
   232816640  11%   20.59MB/s    0:01:28  
   279478272  13%   29.57MB/s    0:01:00  
   326369280  15%   34.77MB/s    0:00:49  
   375128064  17%   44.68MB/s    0:00:37  
   421298176  20%   44.95MB/s    0:00:36  
   462749696  22%   40.85MB/s    0:00:39  
   479002624  22%   28.81MB/s    0:00:54  
   527466496  25%   28.73MB/s    0:00:53  
   570458112  27%   28.14MB/s    0:00:52  
   614760448  29%   30.35MB/s    0:00:47  
   660373504  31%   43.22MB/s    0:00:32  
   704741376  33%   42.27MB/s    0:00:32  
   749273088  35%   41.93MB/s    0:00:31  
   774176768  36%   25.08MB/s    0:00:51  
   794624000  37%   21.03MB/s    0:01:00  
   820838400  39%   17.69MB/s    0:01:10  
   855965696  40%   16.30MB/s    0:01:14  
   888733696  42%   23.87MB/s    0:00:49  
   923074560  44%   26.60MB/s    0:00:43  
   944242688  45%   26.54MB/s    0:00:42  
   976027648  46%   25.50MB/s    0:00:42  
  1009778688  48%   27.76MB/s    0:00:38  
  1033535488  49%   25.67MB/s    0:00:40  
  1059127296  50%   26.34MB/s    0:00:38  
  1078525952  51%   12.95MB/s    0:01:16  
  1127251968  53%   14.84MB/s    0:01:03  
  1175224320  56%   17.90MB/s    0:00:50  
  1223196672  58%   20.88MB/s    0:00:40  
  1270415360  60%   45.75MB/s    0:00:17  
  1320517632  62%   46.09MB/s    0:00:16  
  1343553536  64%   36.63MB/s    0:00:20  
  1386184704  66%   35.49MB/s    0:00:19  
  1415413760  67%   31.57MB/s    0:00:21  
  1445101568  68%   27.13MB/s    0:00:23  
  1479344128  70%   32.39MB/s    0:00:18  
  1506082816  71%   28.59MB/s    0:00:20  
  1540161536  73%   29.57MB/s    0:00:18  
  1567358976  74%   28.98MB/s    0:00:17  
  1595867136  76%   27.63MB/s    0:00:17  
  1629552640  77%   29.29MB/s    0:00:15  
  1658880000  79%   28.31MB/s    0:00:15  
  1690107904  80%   29.22MB/s    0:00:13  
  1720778752  82%   29.28MB/s    0:00:12  
  1750106112  83%   28.25MB/s    0:00:11  
  1778188288  84%   27.75MB/s    0:00:11  
  1810956288  86%   28.16MB/s    0:00:09  
  1841594368  87%   28.58MB/s    0:00:08  
  1874657280  89%   29.47MB/s    0:00:07  
  1901592576  90%   29.44MB/s    0:00:06  
  1920237568  91%   26.06MB/s    0:00:06  
  1955627008  93%   27.19MB/s    0:00:05  
  1989738496  94%   27.43MB/s    0:00:03  
  2017787904  96%   27.19MB/s    0:00:02  
  2052128768  97%   30.78MB/s    0:00:01  
  2074411008  98%   27.68MB/s    0:00:00  
  2097152000 100%   26.67MB/s    0:01:14 (xfer#109, to-check=38/156)
>f+++++++++ clone/Osiris_Windows7RC/hda2.ntfs-ptcl-img.gz.ac

       32768   0%   47.55kB/s    5:58:50  
    11173888   1%   10.66MB/s    0:01:32  
    21266432   2%   10.15MB/s    0:01:36  
    46727168   4%   12.93MB/s    0:01:13  
    61145088   5%   12.36MB/s    0:01:16  
    86048768   8%   15.01MB/s    0:01:01  
    98631680   9%   15.25MB/s    0:00:59  
   125894656  12%   17.03MB/s    0:00:51  
   150241280  14%   20.42MB/s    0:00:41  
   194740224  19%   25.14MB/s    0:00:32  
   238125056  23%   32.91MB/s    0:00:23  
   284590080  27%   37.85MB/s    0:00:19  
   328990720  32%   42.64MB/s    0:00:15  
   370737152  36%   38.84MB/s    0:00:16  
   394592256  38%   32.50MB/s    0:00:18  
   412942336  40%   24.84MB/s    0:00:24  
   437288960  42%   20.96MB/s    0:00:27  
   446234624  43%   15.43MB/s    0:00:36  
   475594752  46%   17.56MB/s    0:00:30  
   524025856  51%   26.09MB/s    0:00:18  
   568393728  55%   30.78MB/s    0:00:14  
   613187584  59%   39.81MB/s    0:00:10  
   658145280  64%   43.55MB/s    0:00:08  
   702316544  68%   42.51MB/s    0:00:07  
   750354432  73%   43.37MB/s    0:00:06  
   782827520  76%   40.23MB/s    0:00:05  
   815333376  79%   35.85MB/s    0:00:05  
   848396288  82%   33.32MB/s    0:00:05  
   867598336  84%   26.76MB/s    0:00:05  
   899743744  87%   25.80MB/s    0:00:04  
   936443904  91%   27.64MB/s    0:00:03  
   957153280  93%   11.94MB/s    0:00:05  
  1002733568  97%   14.83MB/s    0:00:01  
  1023773945 100%   24.93MB/s    0:00:39 (xfer#110, to-check=37/156)
>f+++++++++ clone/Osiris_Windows7RC/parts

          10 100%    0.02kB/s    0:00:00  
          10 100%    0.02kB/s    0:00:00 (xfer#111, to-check=36/156)
cd+++++++++ clone/Osiris_XP_Clean/
>f+++++++++ clone/Osiris_XP_Clean/Info-dmi.txt

       13262 100%   29.10kB/s    0:00:00  
       13262 100%   29.10kB/s    0:00:00 (xfer#112, to-check=35/156)
>f+++++++++ clone/Osiris_XP_Clean/Info-lshw.txt

       16357 100%   35.42kB/s    0:00:00  
       16357 100%   35.42kB/s    0:00:00 (xfer#113, to-check=34/156)
>f+++++++++ clone/Osiris_XP_Clean/Info-packages.txt

         285 100%    0.61kB/s    0:00:00  
         285 100%    0.61kB/s    0:00:00 (xfer#114, to-check=33/156)
>f+++++++++ clone/Osiris_XP_Clean/disk

           4 100%    0.01kB/s    0:00:00  
           4 100%    0.01kB/s    0:00:00 (xfer#115, to-check=32/156)
>f+++++++++ clone/Osiris_XP_Clean/hda-chs.sf

          37 100%    0.08kB/s    0:00:00  
          37 100%    0.08kB/s    0:00:00 (xfer#116, to-check=31/156)
>f+++++++++ clone/Osiris_XP_Clean/hda-hidden-data-after-mbr

       31744 100%   64.99kB/s    0:00:00  
       31744 100%   64.99kB/s    0:00:00 (xfer#117, to-check=30/156)
>f+++++++++ clone/Osiris_XP_Clean/hda-mbr

         512 100%    1.04kB/s    0:00:00  
         512 100%    1.04kB/s    0:00:00 (xfer#118, to-check=29/156)
>f+++++++++ clone/Osiris_XP_Clean/hda-pt.parted

         250 100%    0.50kB/s    0:00:00  
         250 100%    0.50kB/s    0:00:00 (xfer#119, to-check=28/156)
>f+++++++++ clone/Osiris_XP_Clean/hda-pt.sf

         259 100%    0.52kB/s    0:00:00  
         259 100%    0.52kB/s    0:00:00 (xfer#120, to-check=27/156)
>f+++++++++ clone/Osiris_XP_Clean/hda1.ntfs-ptcl-img.gz.aa

       32768   0%   57.14kB/s   10:11:39  
     8978432   0%    6.16MB/s    0:05:31  
    24707072   1%    9.16MB/s    0:03:40  
    66781184   3%   17.84MB/s    0:01:51  
   110100480   5%   22.98MB/s    0:01:24  
   155156480   7%   33.37MB/s    0:00:56  
   203030528   9%   42.55MB/s    0:00:43  
   254574592  12%   44.81MB/s    0:00:40  
   281772032  13%   40.96MB/s    0:00:43  
   293437440  13%   32.99MB/s    0:00:53  
   316276736  15%   27.02MB/s    0:01:04  
   327221248  15%   16.73MB/s    0:01:43  
   353435648  16%   14.25MB/s    0:01:59  
   396197888  18%   20.43MB/s    0:01:21  
   444071936  21%   25.41MB/s    0:01:03  
   491880448  23%   33.76MB/s    0:00:46  
   537362432  25%   43.87MB/s    0:00:34  
   585236480  27%   45.10MB/s    0:00:32  
   633569280  30%   45.21MB/s    0:00:31  
   679116800  32%   44.67MB/s    0:00:30  
   719650816  34%   43.02MB/s    0:00:31  
   753565696  35%   39.74MB/s    0:00:33  
   782827520  37%   35.22MB/s    0:00:36  
   803241984  38%   29.29MB/s    0:00:43  
   833945600  39%   26.83MB/s    0:00:45  
   866779136  41%   26.57MB/s    0:00:45  
   894009344  42%   26.10MB/s    0:00:45  
   918323200  43%   27.01MB/s    0:00:42  
   953450496  45%   28.51MB/s    0:00:39  
   985464832  46%   27.49MB/s    0:00:39  
  1011417088  48%   24.34MB/s    0:00:43  
  1054146560  50%   28.15MB/s    0:00:36  
  1081933824  51%   26.61MB/s    0:00:37  
  1114439680  53%   27.29MB/s    0:00:35  
  1144586240  54%   31.57MB/s    0:00:29  
  1174732800  56%   28.58MB/s    0:00:31  
  1184169984  56%   11.93MB/s    0:01:14  
  1230438400  58%   13.58MB/s    0:01:02  
  1276411904  60%   15.43MB/s    0:00:51  
  1323925504  63%   17.46MB/s    0:00:43  
  1371340800  65%   44.64MB/s    0:00:15  
  1420492800  67%   45.32MB/s    0:00:14  
  1468563456  70%   45.85MB/s    0:00:13  
  1517551616  72%   46.20MB/s    0:00:12  
  1553793024  74%   43.53MB/s    0:00:12  
  1583710208  75%   38.94MB/s    0:00:12  
  1603829760  76%   32.27MB/s    0:00:14  
  1636630528  78%   28.01MB/s    0:00:16  
  1671692288  79%   27.73MB/s    0:00:14  
  1700855808  81%   27.11MB/s    0:00:14  
  1732837376  82%   29.32MB/s    0:00:12  
  1763213312  84%   29.17MB/s    0:00:11  
  1793064960  85%   27.97MB/s    0:00:10  
  1821442048  86%   28.23MB/s    0:00:09  
  1843462144  87%   25.97MB/s    0:00:09  
  1877278720  89%   26.77MB/s    0:00:08  
  1902444544  90%   25.60MB/s    0:00:07  
  1937047552  92%   26.82MB/s    0:00:05  
  1963524096  93%   26.81MB/s    0:00:04  
  1995309056  95%   26.36MB/s    0:00:03  
  2025390080  96%   26.98MB/s    0:00:02  
  2054946816  97%   26.09MB/s    0:00:01  
  2084438016  99%   28.23MB/s    0:00:00  
  2097152000 100%   28.93MB/s    0:01:09 (xfer#121, to-check=26/156)
>f+++++++++ clone/Osiris_XP_Clean/hda1.ntfs-ptcl-img.gz.ab

       32768   0%  109.22kB/s    1:10:57  
    26804224   5%   23.03MB/s    0:00:18  
    57147392  12%   25.84MB/s    0:00:15  
    73957376  15%   22.68MB/s    0:00:16  
    98369536  21%   21.04MB/s    0:00:17  
   126353408  27%   21.84MB/s    0:00:15  
   133234688  28%   16.67MB/s    0:00:19  
   156532736  33%   18.09MB/s    0:00:16  
   173080576  37%   16.40MB/s    0:00:17  
   198475776  42%   15.83MB/s    0:00:16  
   208470016  44%   16.17MB/s    0:00:15  
   234651648  50%   16.80MB/s    0:00:13  
   248053760  53%   16.55MB/s    0:00:12  
   274268160  58%   16.62MB/s    0:00:11  
   285016064  61%   16.57MB/s    0:00:10  
   309886976  66%   16.28MB/s    0:00:09  
   325910528  70%   17.03MB/s    0:00:07  
   361725952  77%   19.26MB/s    0:00:05  
   406126592  87%   27.41MB/s    0:00:02  
   452427776  97%   32.27MB/s    0:00:00  
   464991588 100%   21.35MB/s    0:00:20 (xfer#122, to-check=25/156)
>f+++++++++ clone/Osiris_XP_Clean/parts

           5 100%    0.02kB/s    0:00:00  
           5 100%    0.02kB/s    0:00:00 (xfer#123, to-check=24/156)
cd+++++++++ clone/Thor_Ubuntu_10_12_09/
>f+++++++++ clone/Thor_Ubuntu_10_12_09/Info-dmi.txt

       11212 100%   39.24kB/s    0:00:00  
       11212 100%   39.24kB/s    0:00:00 (xfer#124, to-check=23/156)
>f+++++++++ clone/Thor_Ubuntu_10_12_09/Info-lshw.txt

       21544 100%    0.00kB/s    0:00:00  
       21544 100%    0.00kB/s    0:00:00 (xfer#125, to-check=22/156)
>f+++++++++ clone/Thor_Ubuntu_10_12_09/Info-packages.txt

         285 100%  139.16kB/s    0:00:00  
         285 100%  139.16kB/s    0:00:00 (xfer#126, to-check=21/156)
>f+++++++++ clone/Thor_Ubuntu_10_12_09/disk

           4 100%    1.30kB/s    0:00:00  
           4 100%    1.30kB/s    0:00:00 (xfer#127, to-check=20/156)
>f+++++++++ clone/Thor_Ubuntu_10_12_09/parts

           5 100%    1.63kB/s    0:00:00  
           5 100%    1.63kB/s    0:00:00 (xfer#128, to-check=19/156)
>f+++++++++ clone/Thor_Ubuntu_10_12_09/sda-chs.sf

          37 100%    6.02kB/s    0:00:00  
          37 100%    6.02kB/s    0:00:00 (xfer#129, to-check=18/156)
>f+++++++++ clone/Thor_Ubuntu_10_12_09/sda-hidden-data-after-mbr

       31744 100%    1.89MB/s    0:00:00  
       31744 100%    1.89MB/s    0:00:00 (xfer#130, to-check=17/156)
>f+++++++++ clone/Thor_Ubuntu_10_12_09/sda-mbr

         512 100%   20.00kB/s    0:00:00  
         512 100%   20.00kB/s    0:00:00 (xfer#131, to-check=16/156)
>f+++++++++ clone/Thor_Ubuntu_10_12_09/sda-pt.parted

         420 100%   16.41kB/s    0:00:00  
         420 100%   16.41kB/s    0:00:00 (xfer#132, to-check=15/156)
>f+++++++++ clone/Thor_Ubuntu_10_12_09/sda-pt.sf

         310 100%    8.90kB/s    0:00:00  
         310 100%    8.90kB/s    0:00:00 (xfer#133, to-check=14/156)
>f+++++++++ clone/Thor_Ubuntu_10_12_09/sda1.ext3-ptcl-img.gz.aa

       32768   0%  367.82kB/s    0:49:03  
    41779200   3%   39.84MB/s    0:00:25  
    91127808   8%   43.47MB/s    0:00:22  
   139165696  12%   44.27MB/s    0:00:20  
   187465728  17%   44.71MB/s    0:00:19  
   206897152  19%   39.16MB/s    0:00:21  
   231800832  21%   30.44MB/s    0:00:27  
   272138240  25%   28.77MB/s    0:00:27  
   319324160  29%   28.53MB/s    0:00:26  
   363954176  33%   34.16MB/s    0:00:20  
   412909568  38%   43.18MB/s    0:00:15  
   461406208  42%   45.11MB/s    0:00:13  
   506953728  46%   44.73MB/s    0:00:12  
   554237952  51%   45.37MB/s    0:00:11  
   601161728  55%   44.74MB/s    0:00:10  
   623706112  57%   20.18MB/s    0:00:22  
   666271744  61%   19.81MB/s    0:00:20  
   714145792  65%   19.88MB/s    0:00:18  
   760774656  70%   19.88MB/s    0:00:15  
   807960576  74%   43.93MB/s    0:00:06  
   855670784  79%   45.16MB/s    0:00:04  
   900399104  83%   44.41MB/s    0:00:04  
   949977088  87%   45.13MB/s    0:00:02  
   980254720  90%   41.10MB/s    0:00:02  
  1008762880  93%   36.52MB/s    0:00:01  
  1041170432  96%   33.58MB/s    0:00:01  
  1072496640  99%   29.15MB/s    0:00:00  
  1082629790 100%   33.98MB/s    0:00:30 (xfer#134, to-check=13/156)
>f+++++++++ clone/Thor_Ubuntu_10_12_09/swappt-sda5.info

          53 100%    0.17kB/s    0:00:00  
          53 100%    0.17kB/s    0:00:00 (xfer#135, to-check=12/156)
cd+++++++++ clone/Thor_Ubuntu_10_17_09/
>f+++++++++ clone/Thor_Ubuntu_10_17_09/Info-dmi.txt

       11209 100%   35.42kB/s    0:00:00  
       11209 100%   35.42kB/s    0:00:00 (xfer#136, to-check=11/156)
>f+++++++++ clone/Thor_Ubuntu_10_17_09/Info-lshw.txt

       21173 100%   66.92kB/s    0:00:00  
       21173 100%   66.92kB/s    0:00:00 (xfer#137, to-check=10/156)
>f+++++++++ clone/Thor_Ubuntu_10_17_09/Info-packages.txt

         285 100%    0.88kB/s    0:00:00  
         285 100%    0.88kB/s    0:00:00 (xfer#138, to-check=9/156)
>f+++++++++ clone/Thor_Ubuntu_10_17_09/disk

           4 100%    0.01kB/s    0:00:00  
           4 100%    0.01kB/s    0:00:00 (xfer#139, to-check=8/156)
>f+++++++++ clone/Thor_Ubuntu_10_17_09/parts

           5 100%    0.02kB/s    0:00:00  
           5 100%    0.02kB/s    0:00:00 (xfer#140, to-check=7/156)
>f+++++++++ clone/Thor_Ubuntu_10_17_09/sda-chs.sf

          37 100%    0.11kB/s    0:00:00  
          37 100%    0.11kB/s    0:00:00 (xfer#141, to-check=6/156)
>f+++++++++ clone/Thor_Ubuntu_10_17_09/sda-hidden-data-after-mbr

       31744 100%   97.48kB/s    0:00:00  
       31744 100%   97.48kB/s    0:00:00 (xfer#142, to-check=5/156)
>f+++++++++ clone/Thor_Ubuntu_10_17_09/sda-mbr

         512 100%    1.57kB/s    0:00:00  
         512 100%    1.57kB/s    0:00:00 (xfer#143, to-check=4/156)
>f+++++++++ clone/Thor_Ubuntu_10_17_09/sda-pt.parted

         420 100%    1.29kB/s    0:00:00  
         420 100%    1.29kB/s    0:00:00 (xfer#144, to-check=3/156)
>f+++++++++ clone/Thor_Ubuntu_10_17_09/sda-pt.sf

         310 100%    0.95kB/s    0:00:00  
         310 100%    0.95kB/s    0:00:00 (xfer#145, to-check=2/156)
>f+++++++++ clone/Thor_Ubuntu_10_17_09/sda1.ext3-ptcl-img.gz.aa

       32768   0%   97.56kB/s    3:05:07  
     9502720   0%    5.69MB/s    0:03:04  
    28114944   2%    8.90MB/s    0:01:55  
    50102272   4%   11.91MB/s    0:01:24  
    63242240   5%   11.68MB/s    0:01:25  
    92110848   8%   17.24MB/s    0:00:56  
   107806720   9%   17.36MB/s    0:00:54  
   132710400  12%   16.78MB/s    0:00:55  
   158924800  14%   18.35MB/s    0:00:49  
   174915584  16%   14.60MB/s    0:01:00  
   202440704  18%   17.42MB/s    0:00:49  
   211877888  19%   15.19MB/s    0:00:56  
   261685248  24%   21.60MB/s    0:00:37  
   310083584  28%   31.43MB/s    0:00:24  
   356548608  32%   35.82MB/s    0:00:19  
   405831680  37%   46.25MB/s    0:00:14  
   454852608  41%   46.05MB/s    0:00:13  
   499417088  46%   45.14MB/s    0:00:12  
   532742144  49%   42.01MB/s    0:00:12  
   577273856  53%   40.88MB/s    0:00:12  
   623935488  57%   40.30MB/s    0:00:11  
   671940608  62%   41.13MB/s    0:00:09  
   702676992  64%   40.52MB/s    0:00:09  
   729022464  67%   36.19MB/s    0:00:09  
   761561088  70%   32.83MB/s    0:00:09  
   786759680  72%   27.38MB/s    0:00:10  
   816119808  75%   26.99MB/s    0:00:09  
   829980672  76%   11.56MB/s    0:00:21  
   845447168  78%    9.61MB/s    0:00:24  
   877887488  81%   10.44MB/s    0:00:19  
   906035200  83%   10.30MB/s    0:00:16  
   935886848  86%   25.19MB/s    0:00:05  
   963444736  88%   28.07MB/s    0:00:04  
   995295232  91%   27.93MB/s    0:00:03  
  1025572864  94%   28.34MB/s    0:00:02  
  1053917184  97%   27.98MB/s    0:00:01  
  1083733938 100%   24.07MB/s    0:00:42 (xfer#146, to-check=1/156)
>f+++++++++ clone/Thor_Ubuntu_10_17_09/swappt-sda5.info

          53 100%    0.06kB/s    0:00:00  
          53 100%    0.06kB/s    0:00:00 (xfer#147, to-check=0/156)

```

```
charles@thor:/$ ls -ld /sync/clone
drwxrwx--- 10 charles clone 4096 2009-10-17 20:36 /sync/clone
charles@thor:/$ ls -l /sync/clone
total 32
drwxrwx--- 2 charles clone 4096 2009-10-12 13:59 Loki_XP_Clean_9_10_2009
drwxrwx--- 2 charles clone 4096 2009-10-12 14:02 Osiris_Ubuntu_Clean
drwxrwx--- 2 charles clone 4096 2009-10-17 18:31 Osiris_Ubuntu_Gnome
drwxrwx--- 2 charles clone 4096 2009-10-16 20:04 Osiris_Ubuntu_KDE
drwxrwx--- 2 charles clone 4096 2009-10-14 20:18 Osiris_Windows7RC
drwxrwx--- 2 charles clone 4096 2009-10-12 14:02 Osiris_XP_Clean
drwxrwx--- 2 charles clone 4096 2009-10-12 14:02 Thor_Ubuntu_10_12_09
drwxrwx--- 2 charles clone 4096 2009-10-17 20:26 Thor_Ubuntu_10_17_09

```

I'll just continue to run rsync as root until I am able to get this resolved, even if it is a "dirty" fix.

The tl;dr version: cp -av /array/clone /sync did exactly the same thing rsync did with no errors (that I could see anyway).

EDIT: I even changed the permissions on /sync to 777.

---

### Post by StuartN on 2009-10-21
My apologies, I am completely mistaken. From **man rsync**:

*-o, --owner: This option causes rsync to set the  owner  of  the  destination file  to be the same as the source file, but only if the receiving rsync is being run as the super-user (see also  the  --super and  --fake-super  options).   Without this option, the owner of new and/or transferred files are set to the invoking user on the receiving side.*

That means that in order to change the owner of the file, you must run rsync as root, otherwise the file will be owned by the user running rsync.

This means if you ever restore a backup, the files will be inaccessible to the original user.

In addition, the user running rsync must be a member of every group that is copied, other wise the group is converted to that user's primary group. (So, roughly, all file attributes apart from owner are preserved if the group meberships are correct).

**Solutions:**

1) Run the rsync daemon and set up rsyncd modules to match the user pairs running backups. (This is how mine works).

2) Save the command in a script with the setuid bit so that any user can run the pre-saved command as root, but not modify it. (Edit: But this seems to have been disabled from Ubuntu 8.10 onwards)

3) Run rsync as root. The biggest issue with this is that the state of mind a system failure invokes will cause most people to do something like rsync source/ destination/ and overwrite the (good) backup with the (bad) failed system.

---

### Post by CharlesA on 2009-10-21
Oh I see. Thanks for the info. 

How would I go about setting up those jobs in rsyncd? I'm not quite sure what you mean, but I am curious.

I can understand why that would be a major risk (to run it as root), you'd just have totally screwed yer data up in the event of a mishap, if you screw the script up.

I'll probably end up just running it as root. I've renamed my rsync script to "backup" and created one called "restore" with the destination and source swapped. It's not foolproof, but it should help somewhat. :)

---

### Post by StuartN on 2009-10-21
> **CharlesA said:**
> How would I go about setting up those jobs in rsyncd?

You can run an rsync command with an rsync daemon as either source or destination, and specify the effective user of the rsync daemon:

```
rsync -a --delete ~/ rsync://user@192.168.1.111:/user/ 
```

Rsync daemon must be set up with modules for each rsync user, according to the syntax in **man rsyncd.conf**.

Because rsync daemon is a root process it can read files from one user and write as another.

---

### Post by CharlesA on 2009-10-21
Thanks! I'll check it out.

Also, thanks for the help. :-)

---

### Post by Roasted on 2009-10-21
> **StuartN said:**
> My apologies, I am completely mistaken. From **man rsync**:

*-o, --owner: This option causes rsync to set the  owner  of  the  destination file  to be the same as the source file, but only if the receiving rsync is being run as the super-user (see also  the  --super and  --fake-super  options).   Without this option, the owner of new and/or transferred files are set to the invoking user on the receiving side.*

That means that in order to change the owner of the file, you must run rsync as root, otherwise the file will be owned by the user running rsync.

This means if you ever restore a backup, the files will be inaccessible to the original user.

In addition, the user running rsync must be a member of every group that is copied, other wise the group is converted to that user's primary group. (So, roughly, all file attributes apart from owner are preserved if the group meberships are correct).

**Solutions:**

1) Run the rsync daemon and set up rsyncd modules to match the user pairs running backups. (This is how mine works).

2) Save the command in a script with the setuid bit so that any user can run the pre-saved command as root, but not modify it. (Edit: But this seems to have been disabled from Ubuntu 8.10 onwards)

3) Run rsync as root. The biggest issue with this is that the state of mind a system failure invokes will cause most people to do something like rsync source/ destination/ and overwrite the (good) backup with the (bad) failed system.

Or do the solution I'm running with. I just added myself + the user in question to their respective group. AKA - I'm jason, and say I have a user fred. Well, when fred creates a document, it's owned as fred:fred. But when I rsync the data without root, it gets copied as jason:fred. If fred + jason is a member of the group fred, and the permissions are 770, 775, etc, then fred (the user) can still access the files just fine through group permissions, despite not retaining immediate ownership. Sure, he won't be able to change any permissions, but a user having "7" RWX permissions on all of their data probably wouldn't know the difference in the first place.

So I'm just keeping a mental note for my setup. My samba drive is owned by user:user, with me + the user in question being a member of their group. (aka jason + fred is a member of fred, and all files are owned by fred:fred). Then when I rsync, I take ownership, but even if I pull that backup, fred can still hit his files just fine.

A few quick commands later and the data could be back to fred:fred in no time.

---

### Post by CharlesA on 2009-10-21
> **Roasted said:**
> 
So I'm just keeping a mental note for my setup. My samba drive is owned by user:user, with me + the user in question being a member of their group. (aka jason + fred is a member of fred, and all files are owned by fred:fred). Then when I rsync, I take ownership, but even if I pull that backup, fred can still hit his files just fine.

A few quick commands later and the data could be back to fred:fred in no time.

Yeah that's a good point as well. Could just Rsync it as a non-root and then run chown -R user:group destination to fix the ownership.

Different ways to accomplish the same thing.

I'm trying to decide what I want to do. I might just run rsync as myself and make the restore script run chown on the two directories that aren't mine, if I need to restore the data back to the original source.

---

### Post by Roasted on 2009-10-21
> **CharlesA said:**
> Yeah that's a good point as well. Could just Rsync it as a non-root and then run chown -R user:group destination to fix the ownership.

Different ways to accomplish the same thing.

I'm trying to decide what I want to do. I might just run rsync as myself and make the restore script run chown on the two directories that aren't mine, if I need to restore the data back to the original source.

I'm letting the data on my backup drive stay named as jason:fred, where the source is still fred:fred. Granted, I COULD write a script to run after the non-root rsync command to chown the folders/files to fred:fred, but it's not a big deal to me.

What's more important to me is making sure things work the way I want. And currently things are running pretty solid and I'm happy with my setup. 

But, as I said, because I'm a member of each user's group, even if I have to pull a backup, I can access the data just fine - which is all I need. If I have to reset ownership, no biggie - takes me less than 20 seconds. :) And even if I didn't reset ownership, the user wouldn't know the difference. Because 775 permissions with fred:fred vs jason:fred doesn't yield much difference to the end user. The only thing Fred can't do is change permissions. But since Fred is working from a Windows box via Samba, Fred can't change them anyway. :P

---

### Post by StuartN on 2009-10-21
I think I got stuck in the groove of the way things used to be done (when an actual admin would come and write a script for me). My Linux NAS has rsync in it and worked perfectly from day one with multiple users, so I never noticed any difficulty. One much, much easier alternative is:

User_a writes a script containing their backup command, for instance **rsync -a --delete /home/user_a/ /media/backup/user_a/** and is assigned permissions to read and write their own directory within backup.

User_a assigns group read and execute permissions on the script, then sets the setuid bit, with **chmod 6750 backup** - note that members of the group should not be able to write (modify) the script or they could alter it to run any command.

User_b (anyone who belongs to group) can then start the script, which switches user id to user_a and runs rsync with all of user_a's permissions. The backup is run as if user_a ran it.

(as a little test, create a user sample and save **whoami ; rsync -a /home/sample/ temp/** in a script backup_sample, then **sudo chmown sample:sample backup_sample** and **sudo chmod 6750 backup_sample** - now ./backup_sample wil backup all of samples home into a directory temp, no matter who runs it).

---

### Post by Roasted on 2009-10-21
Not sure if I follow, but are you suggesting to write a different script for each user? Then just set in crontab the executing user for their corresponding script?

Example:

 - users: fred, bob, dave

crontab - execute as fred - script "fred-backup"
rsync -a --progress --delete /media/storage/fred /media/storagebackup/fred


crontab - execute as bob - script "bob-backup"
rsync -a --progress --delete /media/storage/bob /media/storagebackup/bob


crontab - execute as dave - script "dave-backup"
rsync -a --progress --delete /media/storage/dave /media/storagebackup/dave

---

### Post by CharlesA on 2009-10-21
> **StuartN said:**
> User_a assigns group read and execute permissions on the script, then sets the setuid bit, with **chmod 6750 backup** - note that members of the group should not be able to write (modify) the script or they could alter it to run any command.

User_b (anyone who belongs to group) can then start the script, which switches user id to user_a and runs rsync with all of user_a's permissions. The backup is run as if user_a ran it.

(as a little test, create a user sample and save **whoami ; rsync -a /home/sample/ temp/** in a script backup_sample, then **sudo chmown sample:sample backup_sample** and **sudo chmod 6750 backup_sample** - now ./backup_sample wil backup all of samples home into a directory temp, no matter who runs it).

I tried using chmod 6750 after using "su" to switch to the clone user.

Unfortunately when I switched back to my main acct and ran the script, It changed the owner. Did you mean chmod 4750? I couldn't find a chmod 6xxx in the man pages or by googling.

---

### Post by StuartN on 2009-10-22
> **CharlesA said:**
> Unfortunately when I switched back to my main acct and ran the script, It changed the owner. Did you mean chmod 4750? I couldn't find a chmod 6xxx in the man pages or by googling.

4xxx assigns suid and 2 assigns guid, so 6 assigns both user and group of the file owner.

```
ls -l
-rwsr-x--- 1 user_a user_a 37 2009-10-21 11:38 backup_usera
```

**Roasted**: yes, you could use runas on a script that you own, but this is running the other user's script as if you were that user. It would be easy enough to use the same script for everyone and substitute their userid into the backup / restore path - but there would be one copy owned by each user.

---

### Post by Lars Noodén on 2009-10-22
> **CharlesA said:**
> I tried using chmod 6750 after using "su" to switch to the clone user.

Unfortunately when I switched back to my main acct and ran the script, It changed the owner. Did you mean chmod 4750? I couldn't find a chmod 6xxx in the man pages or by googling.

I also notice that info is harder to find.  
It used to be on most university IT departments' help pages, now many have an IT dept in name only...  
 
That first column is for the [suid,sgid](http://www.homepage.montana.edu/~unixuser/051602/SUID.html) and sticky bits.  

4 = user
2 = group
1 = sticky

```

$ mkdir ZZ; ls -lh | grep ZZ
**drwxr-xr-x** ...

$ chmod 1755 ZZ; ls -lh | grep ZZ
drwxr-xr-**t** ...

$ chmod 2755 ZZ; ls -lh | grep ZZ
drwxr-**s**r-x ...

$ chmod 3755 ZZ; ls -lh | grep ZZ
drwxr-**s**r-**t** ...

# Oops.  There is a bug in Ubuntu's chmod :
$ chmod 0755 ZZ; ls -lh | grep ZZ
drwxr-[COLOR="DarkRed"]**_s_**[/COLOR]r-x ...

# at least this works:
$ chmod g-s,o-t ZZ; ls -lh | grep ZZ
drwxr-xr-x ...
```

AFAIK only the sgid and sticky bits are useful, and then only for directories:  

sgid on a directory causes files and directories to inherit the group of the directory. 

Using the stickybit on a directory means that only the owner of a file can delete it in that directory, regardless of write permission.  

suid and sgid are dangerous for files, because scripts run via those files have the privileges granted the user (for suid) and group (sgid) for the user and group of the file not those of the account running the file.  Please do not use suid or sgid on files.  Sudo can be used to accomplish the same job much, much more safely.

---

### Post by StuartN on 2009-10-22
> **Lars Noodén said:**
> suid and sgid are dangerous for files, because scripts run via those files have the privileges granted the user (for suid) and group (sgid) for the user and group of the file not those of the account running the file.  Please do not use suid or sgid on files.  Sudo can be used to accomplish the same job much, much more safely.

I agree with you, and suggest that people should **sudo -u username** or place the job in username's crontab instead of using root. I also think that many privileged tasks should be scripted in preparation for a disaster - the forums are full of "I just did **sudo blah** and ... help!"

In the days when "removeable media" meant a reel of tape, it was hard to remove username's backup script from the building, rewrite it on your home system, and then bring it back in. And no regular user had direct access to root privilege. So I am learning a lot here.

---

### Post by Penguin Guy on 2009-10-22
Take a look at instructions for backing up Linux, compared to instructions for backing up Mac. Now it is clear why Linux is not the most popular OS.

Linux: Follow [this]("http://www.linux.com/news/enterprise/storage/8200-back-up-like-an-expert-with-rsync") page of instructions.
Mac: Put a [time capsule]("store.apple.com/uk/product/MC343/Time-Capsule-1TB") next to your computer.

If only Ubuntu had something like this...

---

### Post by StuartN on 2009-10-22
> **Penguin Guy said:**
> If only Ubuntu had something like this...

I have seen plenty of positive comments about Back in Time, which does much the same thing for Linux.

However, rsync is highly scaleable and Time Capsule is not - I have seen what happens when you restore Time Capsule to a different machine, change username or add a second user.

---

### Post by CharlesA on 2009-10-22
Wow a wireless hard drive. O_o

I'm going to just run rsync as root, since it's only backing up stuff. I've got a script set so that I can restore without using root permissions, in the event I need to do so.

Thanks for all the help everyone.

---

### Post by Roasted on 2009-10-22
> **StuartN said:**
> I have seen plenty of positive comments about Back in Time, which does much the same thing for Linux.

However, rsync is highly scaleable and Time Capsule is not - I have seen what happens when you restore Time Capsule to a different machine, change username or add a second user.

That's what I heard too. Everywhere I ask, people say rsync is still top dog.

---

### Post by coffee on 2009-11-13
I have a rsync script in Python that is working well for me.  It has 3 files the main backup.py and restformat.py used to formate my title and subtitles in the log file and backupexcluded.txt with the directories I do not what to backup.

**_backup.py_**
```
#!/usr/bin/python

import os
from time import asctime
import restformat

#Variables
backupruntime = asctime()
sourcedir = "/home/coffeeboy/"
backupdir = "/media/FreeAgent/backup/"
incrementsdir = '/media/FreeAgent/backup-increments/' + backupruntime

#Logging
backuplog = open('/media/FreeAgent/rsync-backup.log', 'a')
print >> backuplog, (restformat.title(backupruntime))
print >> backuplog, ('Making increments directory: "' + incrementsdir + '"\n')

#Make incrementsdir
os.mkdir(incrementsdir)

#Logging
print >> backuplog, (restformat.subtitle('BEGIN BACKUP'))
backuplog.close()

#Run rsync backup command with Linux logging
os.system('rsync -arEtb --delete --stats --log-file-format="%i %o %f %n" --exclude-from=/home/coffeeboy/bin/backupexcluded.txt --backup-dir=' + '"' + incrementsdir + '" ' + sourcedir + ' ' + backupdir + ' >> ' + '/media/FreeAgent/rsync-backup.log')


#Logging
backuplog = open('/media/FreeAgent/rsync-backup.log', 'a')
print >> backuplog, (restformat.subtitle('END BACKUP'))
print >> backuplog, ('\n\n')
backuplog.close()
```

enter your username for all *coffeeboys* and change */media/FreeAgent* to you desired backup location.  You will need to mkdir both an backup-increments folder and a backup folder and creat a rsync-backup.log in the backup location.


**_restformat.py_**
```
#!/usr/bin/python

def title(mytitle='reStructueredText Title'):
    'Retuns mytitle formatted as a restructeredText tilte.'
    return '======================================='+'\n'+ mytitle + '\n' + '======================================='

def subtitle(mysubtitle='reStructeredText Subtitle'):
    'Returns mysubtitle formatted as a reStructeredText substring.'
    return mysubtitle + '\n' + '---------------------------------'
```

This formates the title and subtitle lines used in the log file.

The *backupexcluded.txt* file is a list of all visible and hidden files and folders (one per line) that I do not want to backup. [i.e. I do not backup up my .VirtualBox directory because of the size.

[B]
An example log file output:[/B]
=======================================
Fri Nov 13 12:23:01 2009
=======================================
Making increments directory: "/media/FreeAgent/backup-increments/Fri Nov 13 12:23:01 2009"

BEGIN BACKUP
---------------------------------

Number of files: 14088
Number of files transferred: 4
Total file size: 9327826172 bytes
Total transferred file size: 767443 bytes
Literal data: 767443 bytes
Matched data: 0 bytes
File list size: 328252
File list generation time: 0.003 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 1111946
Total bytes received: 16066

sent 1111946 bytes  received 16066 bytes  150401.60 bytes/sec
total size is 9327826172  speedup is 8269.26
END BACKUP
---------------------------------

If anyone can help I would like to get rsync to print out a list of only the files that have been updated since the last backup as well as those that have been deleted (thus are being moved to increments).  I can only seem to get the above output or a list of all files in the backup path, which is a little over kill for my log file.

Also if I could get some suggestions on how to use a config file for source and backup dirs and the like that would be cool. I am rather new to Python and just really getting my feet wet.

Thank you

---

### Post by StuartN on 2009-11-18
> **coffee said:**
> If anyone can help I would like to get rsync to print out a list of only the files that have been updated

Does rsync -i (or --itemize) do what you want? This is a list of every action taken, which you can save and grep for new copies, updates or deletions.

---

### Post by coffee on 2009-11-18
> **StuartN said:**
> Does rsync -i (or --itemize) do what you want? This is a list of every action taken, which you can save and grep for new copies, updates or deletions.

I have tried the -i option but am not sure how to emplement the grep solution.  An example would be cool if you don't minde.

---

### Post by coffee on 2009-11-18
I have moved my code conversations to [[COLOR="Blue"]this new thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1328330").
The code has updated and gotten a little stronger.  I seem to be stuck with posting it in line as I already have.  The upload keeps failing.  I have the code bundled in a tar file but even still no luck.

---

