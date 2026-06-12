---
title: "Incremental backup applications?"
date: 2009-07-26
forum: General Help
---

### Post by mrramsey on 2009-07-26
I have a windows program I love, called "second copy" and it simply backs up folders
to a second hard drive -- but only when they are modified.

I saw the program "Timevault" but went nowhere with it -- one of those apps that you have to decipher and I'm Mr user friendly.

Any suggestions on any apps or how to do incremental backups with ubuntu?

By the way, using ubuntu for the first time as of yesterday and it's really very impressive.

Thanks kindly.

---

### Post by DeMus on 2009-07-26
> **mrramsey said:**
> I have a windows program I love, called "second copy" and it simply backs up folders
to a second hard drive -- but only when they are modified.

I saw the program "Timevault" but went nowhere with it -- one of those apps that you have to decipher and I'm Mr user friendly.

Any suggestions on any apps or how to do incremental backups with ubuntu?

By the way, using ubuntu for the first time as of yesterday and it's really very impressive.

Thanks kindly.

Through Synaptic you can install grsync which is the graphical UI for rsync which will be installed as well.
You can find grsync in Applications > Tools > grsync.
It has many options for making backups, including the one you love so much" backup only modified files and folders.
I use it since a few weeks and like it very much.

---

### Post by mrramsey on 2009-07-26
Wow -- this is an active forum !

Thanks for that tip, I'm looking at it now -- looks nice -- I'll have to get familiar
with all those options.

Do you know by chance if it will do an automatic backup when you shutdown the PC?

That's the way my 2nd copy works -- very convenient.

---

### Post by mrramsey on 2009-07-26
Just to make it easy on myself do you know which options should be checked if I want to make an EXACT copy of a folder when grsync is run?

Like, even if I delete a file, it will also delete the file on the backup drive.

THANKS !

---

### Post by mrramsey on 2009-07-26
Basic options I have checked --

preserve time
delete on destination
ignore existing ?? (not sure about this)
show transfer progress

Advanced options I have checked --

always checksum
make backups


Not sure what ignore exisiting is about.

Like I say want an EXACT copy of the source folder when I backup.

---

### Post by DeMus on 2009-07-28
> **mrramsey said:**
> Basic options I have checked --

preserve time
delete on destination
ignore existing ?? (not sure about this)
show transfer progress

Advanced options I have checked --

always checksum
make backups


Not sure what ignore exisiting is about.

Like I say want an EXACT copy of the source folder when I backup.

Sorry for the very late answer.
"Ignore existing" means: when a file in the backup has the same date and time and size as in the original folder, it will not be copied again since it is there already. This saves time.

I set the following items:
Basic: Preserve time; Preserve owner; Preserve Permissions; Preserve group; Verbose; Ignore existing; Skip newer; Show transfer progress
Advanced: nothing
Extra options: nothing

"Like, even if I delete a file, it will also delete the file on the backup drive." Set the option: delete on destination in Basic.

For the rest just try it and compare the two folders to see if what you get is what you want.
Success.

---

### Post by SPARTAN-118 on 2009-08-10
Hi I am looking for a backup program for when I migrate from WUBI to a full install.

Question: Will grsync backup to a CD/DVD? I need to backup to some form of removable media, as I only have one hard drive and one computer, and I'm not up to buying a whole new External Hard Drive.

I have over 10GB of data on my home folder alone. Is this program capable of doing a full system backup onto a few DVDs, or even a USB thumb drive? I'd be willing to pay a few for a 16GB thumb drive, but not  $120 for a 1TB HDD (which would last me a while, but I can't afford that right now).

Please? Anyone? If there is another application that does all these things (while supporting incremental backups), please tell me.
I have hardly any space left on my Hard Drive, and I want to create seperate partitions for my Windows Vista, swap, '/' directory, and home, so home gets all the space it can.

Also, on a related note, do you know what the Disk Drive "D" is for in Vista? It says "$Recycle.Bin" as a folder in it, but the same folder in the main partition (C:\) has much more stuff in it. I also have other partitions, which would be safe to format?:

[LIST]
[*]HDDRecovery
[*]Toshiba System Volume
[/LIST]
Not sure which has the recovery images for Windows (that came pre-installed), but I don't really care, as, once Ubuntu is seperate of Windows, I don't care about what happens to it anymore (other than all my files being wiped clean, of course). I need all the space I can get, and I will gladly format any partition that I don't really need.

SPARTAN-118

---

### Post by rocknrollmouse on 2009-08-10
Re- your 'D:' drive:
Many manufactures pre-installed machines come with hard drive user space pre-partitioned (ignoring any recovery partitions), giving a system (or Windows) partition, and an empty volume.  It is not unusual for the empty volume to be much larger in size than the Windows one.  Very often for Windows users it can become a data store for large files (music; photos; video, etc).  However I'm sure many users never even realise it's there or use it.

---

### Post by rocknrollmouse on 2009-08-10
Back to rsync (command line not gui)

Running the command:
> 
sudo rsync -a --ignore-existing -v /srv/samba/testdir /backup/testdir

first run: it backs up directory testdir, including files sub-folders and their files.
second run: it will back up changed files in sub-folders, but not changed files in the root of testdir - how do I need to modify the command to include these files in an incremental backup as well?

Second question: the -z, compress, option allows backup to be compressed, how easy is it to browse/restore from such a backup?

---

### Post by SPARTAN-118 on 2009-08-10
> **rocknrollmouse said:**
> Re- your 'D:' drive:
Many manufactures pre-installed machines come with hard drive user space pre-partitioned (ignoring any recovery partitions), giving a system (or Windows) partition, and an empty volume.  It is not unusual for the empty volume to be much larger in size than the Windows one.  Very often for Windows users it can become a data store for large files (music; photos; video, etc).  However I'm sure many users never even realise it's there or use it.

Yes, however, the space is only 6.9GB (max.), and I'm fairly certain it's for temporary files. I guess I'll experiment in Windows, you know, delete a file, see which folder/directory changes.

Now, about grsync:
To backup or "sync" your files to the CD/DVD, do you have to select "Destination Directory" as /media/cd or /cd0 or /cd1, etc.? Or does it even support writing to CDs/DVDs, period?

---

### Post by rocknrollmouse on 2009-08-10
From Control Panel, open System, goto the Advanced tab, and choose the Performance [Settings] button.  Again goto the Advanced tab, and choose the [Change] button.  This will show you the drive (or drives) holding the Windows Swap file.  {Unusual for a manufacturer to include a dedicated Swap partition, this is an old-stlye tweak to prevent the Swap file becoming fragmented etc.}

---

