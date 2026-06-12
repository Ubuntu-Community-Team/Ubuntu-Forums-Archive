---
title: "Suddenly have no partition space!"
date: 2011-09-14
forum: General Help
---

### Post by Tk007LwZFJW5ej on 2011-09-14
An hour ago, I had over 200 Gbs of free space on my Linux partition. All of a sudden, a system message popped up warning me of low disk space. I emptied the trash, then took a look at conky on my desktop, and watched the available space gradually decreasing from half a gig to a few Kb. I have no idea what happened. I wasn't downloading anything. I've been trying to scan with clamav, but it's complaining that I have no more write space left. I checked the properties on all visible folders  in the file system, and none of them are large enough to account for 200+ Gb of missing space.  EDIT: Don't know if it's related, but I just found six or seven empty text files in my user folder. They were all named with random alphanumeric strings, and I definitely did not create them.

---

### Post by kimda on 2011-09-14
Do you have baobap installed? You can start it in Unity by typing disk usage analyser in the dash (windowskey + disk usage analyser). It will scan your homefolder and show which directories are taking up space. You can also scan the complete filesystem.

---

### Post by kimda on 2011-09-14
Another way to find big files is by using the commandline.

This will find files under the current directory bigger than 10 MB. 
```
find . -type f -size +10M -ls
```

---

### Post by Tk007LwZFJW5ej on 2011-09-14
I used the command you posted. Nothing particularly large is showing up, and there are only a handful of modestly sized (0.5 - 1 Gb) files. I don't have boabap and I'm not able to download or remove any programs now. My system monitor says that I've reached the 100% full point.

---

### Post by drs305 on 2011-09-14
The three most common reasons for running out of space on an otherwise sufficiently-sized partition seem to be large log files, un-emptied Trash bins (users and root's), and backups made on the system partition instead of the backup partition.

Here is a guide I wrote a while back that helps troubleshoot space issues:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by WorMzy on 2011-09-14
Can you post the output of this command please:

```
sudo du -hx --max-depth=1 / | sort -h
```

(Give it a little while to complete)

---

### Post by Tk007LwZFJW5ej on 2011-09-14
I found the culprit: a 240 GB .xsession-errors.old file in my user folder. Strangely, when I checked the folder properties in nautilus, it contained 300 GB, but   sudo du -h --max-depth=1 / | grep '[0-9]G\>'  showed 515 GB.   Do I need to do something with this file before deleting it?

---

### Post by WorMzy on 2011-09-14
Personally, I'd read the log and find out why it's so big. If you don't find out what's caused the log to get this big, and address it, then the same thing will probably just happen again.

But other than that, no. You can just delete it.

---

