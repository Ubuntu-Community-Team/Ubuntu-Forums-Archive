---
title: "Need backup sync software recommendation."
date: 2010-09-12
forum: General Help
---

### Post by Keypel on 2010-09-12
Need backup sync software recommendation. 

Hopefully something with a GUI. (if not, some dd if= cmd might do)

I need something that will:

+copy from a source dir to a destination dir (1st -> 2nd dir)
+del files and folder not found in the source.
+Exclude copying files that are already in the destination (if files are same size, then skip)(if files size is different, then overwrite).
+Remote folder sync such as ftp, would be nice.

In other words something that will synchronize destination dir with the source.

I tried a program called lucky backup. Was not impressed. 

Thanks in Advance!!

---

### Post by Dex73 on 2010-09-12
Well I was going to recommend LuckyBackup, actually curious what you didn't like about it. I hear good things about rsync, though it is a command line application and I'm pretty sure it's what drives LuckyBackup anyway. I've looked everywhere for the best program for this. Definitely post what you find, if anything!

---

### Post by baddnady23 on 2010-09-12
A little search of the forums on this topic will turn up an infinite amount of into related to this specific topic.  To meet your specific demands, check out **rsync**.  It is very versatile and will do exactly what you are asking for.  It also as a GUI called **Grsync** which is located in the repos.  I have never needed the GUI however as the command line version is very easy to pick up on.  I have it set up with cron to run every night and back up my /home drive to my backup server sitting in a closet.  When coupled with SSH, it is a very good backup client.

Of course this isn't the only solution, but is one that I have found to work very well.  You'll probably get 50 different answers to this question.  :p

[http://ubuntuforums.org/showthread.php?t=238672]("http://ubuntuforums.org/showthread.php?t=238672")

---

### Post by Keypel on 2010-09-13
> **baddnady23 said:**
> A little search of the forums on this topic will turn up an infinite amount of into related to this specific topic.  To meet your specific demands, check out **rsync**.  It is very versatile and will do exactly what you are asking for.  It also as a GUI called **Grsync** which is located in the repos.  I have never needed the GUI however as the command line version is very easy to pick up on.  I have it set up with cron to run every night and back up my /home drive to my backup server sitting in a closet.  When coupled with SSH, it is a very good backup client.

Of course this isn't the only solution, but is one that I have found to work very well.  You'll probably get 50 different answers to this question.  :p

[http://ubuntuforums.org/showthread.php?t=238672]("http://ubuntuforums.org/showthread.php?t=238672")

Thanks, I like Grsync much better than Lucky backup. I'm just not good at cmd lines, too hard for me to remember all the diff cmd's.

---

### Post by BigBaka on 2010-09-13
Thanks for this thread, I just installed Grsync but am wondering how to get the program to backup onto a Windows network via samba where the MS workgroup is OFFICE the comp name is BK and the backup destination folder is in a folder called Backup on the root of the d drive. 

I had a guess and put the destination directory as smb://bk/d/Backup/ but I got the following readout

ssh: Could not resolve hostname smb: Name or service not known

rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(601) [sender=3.0.7]

Also tried smb://OFFICE/BK/D/Backup/ as the destination directory (this time including the MS workgroup), but had the same result.

---

### Post by baddnady23 on 2010-09-13
CHeck out this guide, it may be of some help.

[http://www.mikerubel.org/computers/rsync_snapshots/]("http://www.mikerubel.org/computers/rsync_snapshots/")

---

### Post by Keypel on 2010-11-11
Edit 

lol

I replied to the wrong thread.

Ugg, how do I delete this post? Ok, just ignore.

---

