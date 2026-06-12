---
title: "No copying done using Grsync or rsync"
date: 2011-05-18
forum: General Help
---

### Post by myosotis on 2011-05-18
I'm using Ubuntu 10.10 64-bit and I'm a fairly new linux user. I've been trying to set up Grsync to to make incremental backups to my external harddrive but have some problems. In the file lists it looks like files are actually being copied but when I look at the harddrive none of the new files are actually there. As far as I can understand I'm not making a dry-run.

I also found this thread:

[http://ubuntuforums.org/showthread.php?t=1760718](http://ubuntuforums.org/showthread.php?t=1760718)

And I tried using the commands suggested in that post, with the same results.

Help much appreciated!

EDIT: The external disk is NTFS-formatted. I'm not sure if this matters or not.

---

### Post by jerrrys on 2011-05-19
i do not use ntfs so don't know about that.  i suspect that your options are not right in grsync.

take a look at 'luckybackup, its in the software center.  LB is just another gui for rsync, but i find it better laid out with clearer on board instructions.  and if its any help, the instructions for LB can for the most part be applied to grsync (easier to understand).

---

### Post by seawolf167 on 2011-05-19
I have a couple of "media" drives formatted in NTFS (so my networked Windows computers can read them), and I back up to NTFS drives as well. I haven't had any issues at all.

A couple things to check (I'm not sure why it isn't working for you), do you have rwx permission in that /source directory tree? Can you copy a test folder/files with no extra options (aside from the -v switch)? If not, does it work with *sudo*?

---

### Post by myosotis on 2011-05-19
I'll have a look at Lucky Backup, but I'd also like to understand what I'm doing wrong, if possible.

When I do an ls -l in the media directory (where both the disks are) I get the following:
```

drwxrwxrwx 1 root  root  24576 2011-05-17 09:00 data
drwx------ 1 sanna sanna 16384 2011-04-29 16:21 kameleont
```

(Yes, sanna is me ;) )
As far as i understand that's right?

Now when I try to do an rsync -v I get the response

```
skipping directory .
```

I've tried placing the test directories in different places (including placing both on the desktop, as well as on the disks I'm trying to backup) and I get the same result.

---

### Post by seawolf167 on 2011-05-19
What is the full *rsync *command you are using?

What is the output of:

```
rsync -runv /media/kameleont /media/data
```

---

### Post by myosotis on 2011-05-19
The output is:

```
sending incremental file list
```Followed by a long list of the files missing on the destination disk, ending with:

```
sent 1287533 bytes  received 8789 bytes  66478.05 bytes/sec
total size is 235314441330  speedup is 181524.68 (DRY RUN)

```

EDIT: The result in my previous post was using only rsync -v. I've also tried rsync -ruv --delete, which just resulted in a similar file list, with no actual copying.

---

### Post by seawolf167 on 2011-05-19
Provided you want to copy the directory tree from /media/kameleont to /media/data, it sure looks like the previous command will work without the -n switch. If you want an exact copy, add in the --delete switch

Copy /media/kameleont to /media/data, no deleting

```
rsync -ruv /media/kameleont /media/data
```Exact mirror of /source on /destination

```
rsync -ruv --delete /media/kameleont /media/data
```

---

### Post by myosotis on 2011-05-19
Weird. I type:

```
rsync -ruv --delete /media/data /media/kameleont/backup
```

And get the same

```
sending incremental file list
```

Followed by the file list. I also copied a few files into one folder to have completely new files to be included, and they show up in the file list, but when I look in the destination folder they're not there.

And at the end I get:

```
sent 482167780 bytes  received 5250 bytes  15808951.80 bytes/sec
total size is 235351397749  speedup is 488.11
```

---

### Post by myosotis on 2011-05-20
I think I got it to work. When I wrote /media/data/ instead of /media/data it worked. Before it had created another subfolder with everything in, which I hadn't noticed before.

---

### Post by seawolf167 on 2011-05-21
Cool, glad it is working :)

---

