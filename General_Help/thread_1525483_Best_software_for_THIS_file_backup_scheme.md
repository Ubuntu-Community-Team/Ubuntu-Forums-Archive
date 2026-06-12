---
title: "Best software for THIS file backup scheme ?"
date: 2010-07-06
forum: General Help
---

### Post by nemetsk on 2010-07-06
There's so much software for backups I don't know where to start. I figured it'd be easier to ask other ubuntusers.

So... what would be best based on these particulars ?

1. An entire "tree" hierarchy of dirs and files to be backed up every so often on external HDDs (manually as I see fit).

2. As one HDD fills up, I can grab a new one to use as my backup medium, **and the software will simply re-build the file system (tree) as necessary, only copying new/updated files and creating the directories to store them**.

3. Backup software tracks which&where already-backed-up files were copied in some sort of spread/db/log, i.e. so that I may search and easily see which ex hdd I need to grab.

---

### Post by arsenic23 on 2010-07-06
If you absolutely have to use multiple external drives for backup wouldn't it be better to break the tree into parts and back each part up to it's respective drive using rsync and a script?

You could make a ~/backup folder or similar and place directories for each drive in it.  You could then set a backup script that would detect which one of these drives was plugged in and back up the appropriate content.  

I built something similar for my Boss.  She just puts the dive into the eSATA holder (it looks like a toaster) and clicks on the launcher for the script.

---

### Post by Samulus on 2010-07-06
I would say either a shell script or python script running in the background as a cronjob that backs up according to your specified parameters. I'm not aware of any pre-exsisting software that does what you're asking for though. But I don't know too much about backup tools for Ubuntu to begin with so this is just one suggestion.

---

### Post by nemetsk on 2010-07-06
> **arsenic23 said:**
> If you absolutely have to use multiple external drives for backup wouldn't it be better to break the tree into parts and back each part up to it's respective drive using rsync and a script?

Well there are a few pitfalls:
1. I have directories that are larger than any given disk, and have to be split/shared over disks already.
2. I need to prepare for any part of the tree to expand past the physical limits of a drive.
3. I do what you are saying now, just manually (no script)... I need the ability to both back up something once and move on, and provide myself an out for more data anywhere in the tree.

---

### Post by arsenic23 on 2010-07-07
Well...  I'm not aware of anything that will work like that out of the box, but that's not stopping you from hobbling something together.

Here's a decent list of already available backup untilities:
[http://www.linux.org/apps/all/Administration/Backup.html](http://www.linux.org/apps/all/Administration/Backup.html)

Personally, if I was in your shoes I'd make a low cost, low power, backup server; place it off site; and rsync to it every night with a cron job.

---

