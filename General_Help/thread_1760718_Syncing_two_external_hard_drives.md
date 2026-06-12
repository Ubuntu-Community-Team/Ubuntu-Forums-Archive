---
title: "Syncing two external hard drives"
date: 2011-05-17
forum: General Help
---

### Post by ron177 on 2011-05-17
Dear all,

 I have an external hard drive that contains some 600 GB of files and  folders. I use this external drive frequently and so the files and  folders in it change on a daily basis. I want to back up this drive on  another external drive. What is the best way to sync these two external  hard drives on a daily basis?

 I have been trying to sync them through the Grsync software. But I  think either I am not choosing the right options or else Grsync is not  the best/right software for my purpose because the second hard drive  does not ever become completely identical to the first one. What am I  doing wrong? Should I go with another software? If so, are there  suggestions for a good one? Or am I doing something not right?

 When I run Grsync, I choose the first external hd as my source and  the second one as my destination. Then below that I check "Preserve  time," "Preserve permissions," "Preserve owner," and "Preserve group."  Below that, I also check "Verbose" and "Show transfer progress." Other  options are all unchecked. Should I reconfigure these options?

 FYI, I frequently rename, edit, modify, or else completely delete  files and folders in the primary hard drive. Hence, my need to back it  up everyday so that the change would be replicated in the second hard  drive.
 
Appreciatively,
 
R

---

### Post by dargaud on 2011-05-17
Use rsync on the command line (makes it easy to script).
Always start with -n (fake run) before doing a real run.
For instance I back up my data like you with:
```
rsync -xavHl --delete /InternalDisk /media/ExternalDisk/
```
Warning, the trailing / has some importance.

---

### Post by seawolf167 on 2011-05-17
Aye, rsync is the way to go

Setup your command and test it ensure it works the way you want it too (maybe something like)

```
rsync -ruv --delete /source /destination
```then add a crontab entry to run your command (or bash script) everyday (or whenever you want to run it). See my crontab link in my signature for more info, or just post back if you have questions.

---

### Post by ron177 on 2011-05-17
You know the problem is that I don't know even basic things about rsync and I am generally not all that great when it comes to working off the Terminal. Where can I learn some basic command lines for rsync? How can I download rsync by the way?

Thanks so much!

---

### Post by seawolf167 on 2011-05-17
You already have rsync and all the commands on your system. Click the link "linuxcommands" in my sig for a nice walkthrough of some of them. 

You can also start reading up [here]("http://ubuntuforums.org/showthread.php?t=801404")

Finally (and most importantly), *man* will/should be your best friend

```
man commandname
```

gives you the manual for commandname, so the rsync manual (man page) is accessed by typing

```
man rsync
```

---

### Post by ron177 on 2011-05-17
> **dargaud said:**
> Use rsync on the command line (makes it easy to script).
Always start with -n (fake run) before doing a real run.
For instance I back up my data like you with:
```
rsync -xavHl --delete /InternalDisk /media/ExternalDisk/
```Warning, the trailing / has some importance.


Thanks much for the tip. What does

-xavHl
mean in your command line?

Also does this mean this command line mean that the files and folders in the destination will be deleted (since you have "delete" in the command line) and all the material from the source will be copied to the destination drive once again? If so, this is not what I want. 

I want an incremental backup meaning that I want to backup all the files that have *changed* since the last backup. I don't want to delete the entire destination drive and recopy everything from the source. That would take just too much time everyday.

---

### Post by ron177 on 2011-05-17
> **seawolf167 said:**
> Aye, rsync is the way to go

Setup your command and test it ensure it works the way you want it too (maybe something like)

```
rsync -ruv --delete /source /destination
```then add a crontab entry to run your command (or bash script) everyday (or whenever you want to run it). See my crontab link in my signature for more info, or just post back if you have questions.

Many thanks for the links and the advice. I am beginning to read the material you suggested. I wonder why your command line differs from the person who suggested I should type in: 

rsync -xavHl --delete /InternalDisk /media/ExternalDisk/
What does -ruv mean in your command line?

---

### Post by seawolf167 on 2011-05-18
Its all in the man pages :P

But:

-r = recursive (copy all directories, contents and their subdirectories)
-u = update (if a file/folder exists, do not overwrite unless newer)
-v = be verbose (so when testing in a terminal you can see what is being moved/etc)
--delete = delete files/folders from /destination that are not on /source (so /destination is an exact mirror of /source)

As said previously, you can add the -n switch to preform a "dry-run", and if you have the -v switch on, you can redirect the output to a file so you can see exactly what would be copied/deleted/etc.

```
rsync -ruvn --delete /source /destination > rsync-dry-run-file-list
gedit rsync-dry-run-file-list
```

---

### Post by collisionystm on 2011-05-18
Open a terminal

rsync --help

---

### Post by dargaud on 2011-05-19
When you use rsync, there are so many options that you need to consider the corner cases:
- what should it do if files have changed both on the source and the destination (does not apply in the case of a backup)
- what should it do if source files are deleted or moved
- what should it do if the source files belong to various users
- what should it do if there are hard/soft links
- what should it do if the source spread over several mounted filesystems
- what should it do if some permissions block access to source files
- what should it do if there are special files (devices, pipes...)
- should it transfer 'useless files' (backups, CVS, SVN...)
- what should it do with strange characters in filenames

Other than that, it's pretty simple to use...   :P

---

### Post by ron177 on 2011-06-01
This has successfully resolved my problem. Thanks everyone for tips and advice.

---

### Post by seawolf167 on 2011-06-01
Glad you got it all working!

---

### Post by rmcellig on 2012-11-05
I can't understand why my test rsync doesn't work. Any ideas?

rsync -ruvn --delete /media/randy/radio_music/test2/ /Home/Desktop/test1

Nothing happens. I have the code in Scheduled tasks which I use all the time. Even when I frce the code to sync, nothing happens. I have some items in the test2 folder that I would assume show up in the test1 folder.

---

### Post by wildmanne39 on 2012-11-05
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

