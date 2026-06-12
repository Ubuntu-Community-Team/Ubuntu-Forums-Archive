---
title: "Backing up Large Folders with rsync"
date: 2009-08-27
forum: General Help
---

### Post by terminator14 on 2009-08-27
About 2 years ago now, I bought the QNAP TS-409 PRO NAS (Network Attached Storage) and have been filling it with stuff ever since. Now, the QNAP company has made a firmware update that I want to switch to, but it recommends that before switching, all data the NAS has be backed up. Unfortunately, I have 4x1TB drives in it, using RAID 5 and backing up all the data is no easy task. Especially since the RAID 5 was meant to protect the data since a lot of it is valuable.

My problem is that I need to transfer about 1TB of data from the NAS to several other hard drives I have around the house, do the update, and transfer the data back. The smart tool to use seems to be rsync but I haven't used it enough to know exactly how it works. The functions I need it to do are:

-Show a progress bar (the backup might take a while and I don't want to give up staring at no progress and cancel it)
-Use checksums to verify that everything copied ok
-Copy recursively all subfolders in the folder I specify
-don't delete originals (I'll do that myself if I have to)
-don't use compression preferably to speed it up
-don't use encryption preferably since it's all on my lan

From googling and reading the man pages, this is what I've come up with as parameters for rsync I should use:

```
-q quiet (I don't need to see millions of files scrolling by on the screen)
-c use checksums to verify everything
-r recursive
-l copy symlinks as symlinks (I don't know if I'll hit any symlinks)
-H preserve hard links (don't know if I'll hit these either)
-p preserve permissions (I don't know if I need this)
-o preserve owner
-g preserve group
-h human-readable format (what becomes human readable? does it show file sizes while copying?)
--progress show progress bar
```

so if "Photos" is the folder I'm backing up, my command will look like this:

```
rsync -q -c -r -l -H -p -o -g -h --progress Photos Destination_Folder
```

Is this right? Do I need the -l, -H (am I likely to hit those, and can having these parameters hurt?), -p, -o, -g (I assume these would be important on a NAS that keeps track of different users). Also, does rsync use checksums to verify that what it copied is ok, or does it only use them to check if a file should be overwritten or skipped if the destination already has the same file? I need it to check files it copies to make sure they copied ok.

---

### Post by terminator14 on 2009-08-27
Looks like -q suppresses the progress bar so I don't need that. Also it looks like the progress bar is not an overall one like I would prefer but one for each file. I could live with that though, as long as it shows it working. In order to simplify it a bit, I narrowed down the command to something like this:

```
rsync -crh --progress source/ destination/
```

Does that seem like the best way to go?

---

### Post by terminator14 on 2009-08-28
rsync manpages:

> -c, --checksum
...
...
Note that rsync always verifies that each transferred  file  was
              correctly  reconstructed  on  the  receiving  side by checking a
              whole-file checksum that is generated  as  the  file  is  trans&#8208;
              ferred,  but  that automatic after-the-transfer verification has
              nothing to do with this option’s before-the-transfer “Does  this
              file need to be updated?” check.


So it looks like rsync always verifies the data the is copied and the -c flag is not required in my case, since the destination folders are always empty.

I am having a problem with the speed of rsync however for some reason. I'm running it with the command:

```
rsync -e ssh -rh --progress admin@NAS:/source/folder /destination/folder/
```

The NAS has a gigabit ethernet port which is connected with CAT6 cable to a gigabit ethernet switch which is connected to my computer (also supports gigabit). I'm copying the source folder from the NAS to my computer and the speed is ~600kB/s... This is way below the speed I would normally get if I just mount the network drive and copy files using nautilus. Is this due to ssh's encryption? Can I speed up rsync somehow? At 600kB/s it will take forever to copy such large amounts of data.

---

### Post by terminator14 on 2009-08-28
Trying a few more things, I managed to speed it up a bit but not by much. I had a 250GB WD portable drive that was empty so I plugged it directly into the QNAP's USB port, connected to the QNAP through ssh, found where it mounted the drive, and told it to do a local backup from the folder where it kept all my data to the WD. I used this command:

```
rsync -rtuv --progress /share/MD0_DATA/source/ /share/WD/destination/
```

It's still only copying at ~2MB/s. This is a local backup. Shouldn't it be going much faster? I tried basically the same options on my computer and it copies files at ~30MB/s. Am I missing something? The hardware specs page for my NAS at the main QNAP site says that all the NAS's USB ports are 2.0 so it's not the USB speed.

---

