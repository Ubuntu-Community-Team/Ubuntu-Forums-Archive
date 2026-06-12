---
title: "Kernel panic issue after hard reboot"
date: 2011-07-21
forum: General Help
---

### Post by Weidbrewer on 2011-07-21
I woke up this morning and my screen would not turn on, as if it had gone into hibernate mode or some such thing.  This has happened once or twice before, but not recently.  I did a hard reboot and got a message (scrambling my brain trying to remember what it was) about my hard drive.  I fully powered down and came back a half-hour later and tried to boot again, and this time I got the "Kernel Panic - not syncing: VFS: Unable to mount root fs" message.

Looking around, it seems that this issue is normally caused by an update, but I haven't installed any recently.  Any idea what this might be, or is it likely that my HDD has gone bad?  (I have also seen stuff about using a liveCD and running "sudo e2fsck /dev/sdx#," but again, I have a sneaking suspicion my HDD might be toast with my luck...)

OS: Ubuntu 64 10.04

Thanks!

---

### Post by regala on 2011-07-21
> **Weidbrewer said:**
>  (I have also seen stuff about using a liveCD and running "sudo e2fsck /dev/sdx#," but again, I have a sneaking suspicion my HDD might be toast with my luck...)

OS: Ubuntu 64 10.04

Thanks!

indeed, your system hard disk is likely on its way to push daisies...
try and mount it *read-only* with a livecd and try and save any data you deem important. seems like you don't have much time to waste, if any.

---

### Post by Weidbrewer on 2011-07-21
Yeah, that is what I suspected.  Thanks for the confirmation (if "thanks" is really the appropriate term here... ;) )

When I get home, I'll pull out the ol' LiveCD and see if I can DD it to a new drive.  Thankfully, there's nothing of dire importance on the OS drive - just my MythTV and TeamSpeak setups, which just take time to rebuild.  Everything else is on a separate RAID, so it's not the end of the world.

---

### Post by DawieS on 2011-07-21
Before you remove the disk, you may want to run a Filesystems Check on all partitions, then re-install Grub, then boot from the disk and see how it goes.

I had a similar situation, with some freezing, and also File Splicing errors while reading from the disk. After replacing the disk, a week later the new disk had exactly the same symptoms.

I have a strong suspicion that a possible bug in the Power Manager caused this behaviour. I then repaired the old disk and put it back in service, and disabled Power Manager in the Startup Preferences. Everything is running perfect since (1 week now).

For some reason ALL partitions on the source disk gets marked as being dirty in the MBR while copying or reading from the disk, and the disk is off-lined.:confused:

---

### Post by Weidbrewer on 2011-07-21
Power manager *does* seem to be very buggy - these problems started the same day that I put a newish monitor on that machine that has wonky power-saving behavior itself.

I'm going to still clone the drive if I can - after all, I might only get one go at it, and I can always fix it later if the problem isn't hardware related.

Checking the disk, I'm on board with - but could you please refresh my memory on how to reinstall GRUB?  Also, where are the power manager's startup preferences?  Are they in the admin link from the desktop like the others, or is this something that I need to modify elsewhere?

---

### Post by DawieS on 2011-07-21
> **Weidbrewer said:**
> Checking the disk, I'm on board with - but could you please refresh my memory on how to reinstall GRUB?  Also, where are the power manager's startup preferences?  Are they in the admin link from the desktop like the others, or is this something that I need to modify elsewhere?
To restore Grub, boot from another working Ubuntu installation, or Live CD, then open a terminal and type:
```
sudo fdisk -l
```to find out what the current device name of your boot disk you want to repair is.

If it is "/dev/sdb" then type:
```
sudo grub-install /dev/sdb
```After booting from that disk, type:
```
sudo update-grub
```to get the correct menu entries (after maybe switching off external drives that you don't want included)

Power Manager:
Click on System > Preferences > Power Management and select Never at Actions. Then click on System > Preference > Startup Applications, and un-check Power Manager. With the next reboot, the Power Manager daemon should not start up.

---

### Post by Weidbrewer on 2011-07-21
Awesome - thanks!  I'm still probably going to attempt to clone the disk and fix that one, 'cause I've grown leery of that HDD recently anyway.

Thanks for taking the time to explain - way, way too often questions like that in the Linux community are met with "STFU n00b!' and "Read the effin' manual!" rather than actual help

---

### Post by Weidbrewer on 2011-07-22
And the answer was:  HDD was totally borked.  Rebuilt everything, and now I have a cron-job created to image that sucker every week.  :)

---

### Post by pqwoerituytrueiwoq on 2011-07-22
> **Weidbrewer said:**
> And the answer was:  HDD was totally borked.  Rebuilt everything, and now I have a cron-job created to image that sucker every week.  :)
care to post the script/command?

---

### Post by Weidbrewer on 2011-07-24
Sorry for the delay - people don't usually ask *me* for code, so I wanted make sure my code was 100% working.

First off, the image itself can be simply done manually with this code:

```
dd if=/dev/sda conv=sync,noerror bs=64K | gzip -c  > /media/raid/backup/system.img.gz

```

if= would be the drive I'm imaging, and the second value is the destination file and location, saved as a zip file.  Change file location as needed.

My script to do things automatically with a script, I used:

```
#!/bin/bash
# edit above line to the path to bash
#command to find is: "which bash"
#
##############set your variables below###########
# prefix is the prefix of the filename,
# example filename: server1-07-20-2011.bak, the prefix would be: server1
# numtokeep is the number of backups you would like to preserve
# backupFolder is the location of your backup files, exclude trailing slash, make sure it exists!
#
prefix=dolly
numtokeep=3
backupFolder=/media/raid/backup
sourceDrive=sda
#
#################################################
#
#  go to backup folder just to be safe
cd $backupFolder
#
# count how many files are in backup folder, and set to a variable
filecount=`ls -l $backupFolder/$prefix* | wc -l`
#
# checking to see if number of backups is greater than number to keep
if [ $filecount -gt $numtokeep ]
        then
                extras=$(($filecount - $numtokeep))
                echo "leaving $numtokeep, deleting $extras"
                for counter in $(ls -ltr $backupFolder/$prefix* |  head -n $extras | awk '{ print $8 }')
                do
                        if [ "$1" == "--test" ]
                        then
                                echo "Will delete: $counter"
                        else
                                echo "deleting: $counter"
                                rm -R $counter
                                if [ $? != 0 ] ; then
                                echo "Error deleting: $counter"
                                else
                                echo "Successfully deleted: $counter"
                                fi
                        fi
                done
        else
                echo "not enough backups to delete"
fi

#
#
#
# start imaging with dd, if not test run
now=$(date +"%y-%m-%d")
backupFile=$prefix-$now.img.gz

if [ "$1" == "--test" ]
then
        echo "If this were an actual emergency, this would start image from $sourceDrive to $backupFolder/$backupFile"
else
        echo "Starting Image to $backupFolder/$backupFile... go get a coffee - dd is slow as f^@#$."
        dd if=/dev/$sourceDrive conv=sync,noerror bs=64K | gzip -c  > $backupFolder/$backupFile
        if [ $? != 0 ] ; then
                echo "did not complete image"
        else
                echo "imaging completed."
        fi
fi


```

Note the comment at the top to check your bash location (Use "which bash")  I saved mine as "auto-image.sh". If you cut and paste, I mode this post on a Windows machine (sorry) so there may be some stray ^M errors copied over.  Open is with Nano and save - it'll auto convert it.  Also, "numtokeep=3" is how many backups to keep.  Mine is set to three, so after 3 are made, it will start deleting the oldest.

Change the permissions:
```
chmod  +x <filename>
```

Then:
```
sudo crontab -e
```

I used the values:

```
30 0 * * 0 /path/to/filename
```

The first to values are time, so 30 0 = 12:30 AM.  * is a wild card, and kind of not important here, and the trailing "0" is the day of the week - in this case Sunday.  (Monday is "1", etc.)  This makes the cron job run Sundays at 12:30 am every week.  

Final two things are that you can test it with:

```
./<filename> --test
```
(run this from the location you have the file saved.)

If you ever need to restore one of these backups:
```
gunzip -c path/to/file | dd of=/dev/[system-drive] conv=sync,noerror bs=64K 
```

Hopefully, that is all of use to someone.

---

### Post by ajmc on 2011-07-24
I have experience a kernel panic in one of our servers before, it was caused by an overheating of the processor.  The fan stopped working.

---

### Post by Weidbrewer on 2011-07-24
> **ajmc said:**
> I have experience a kernel panic in one of our servers before, it was caused by an overheating of the processor.  The fan stopped working.

Yeah, certainly been there (well, in my case, it was the fan on my GPU going), which is why I let it sit all day.  I was hoping that it was heat issue, but alas, it was not in the end.

---

