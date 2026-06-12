---
title: "Are compressed backups more logical? Or not really?"
date: 2009-09-05
forum: General Help
---

### Post by Roasted on 2009-09-05
I have two 500gb hard drives in my system. One copies the other via an rsync script that runs twice a day, controlled by crontab. It's fully automated. I do nothing.

The one advantage to this is it's not a true raid mirror system, so if I delete something I shouldn't have I can just go to the backup drive and grab it.

But I was just curious, is there a backup solution that compresses your data? And if so, is it more logical than the method I use, or is it typically only ideal if backup space is limited?

---

### Post by P4man on 2009-09-05
compressing makes a ton of sense for a backup. Why not compress it?
What also makes sense, is not just rsyncing, I mean thats pretty good already, but better is doing a "real" backup where you do incremental backups like every day, and do a full backup like every week/month.

In your case, if you delete or overwite or corrupt a file accidentally, you have 12 hours to discover it, or it will still be gone forever. If you do a backup scheme like I described, you're pretty safe. And it doesn't cost that much diskspace in most cases.

"Simple backup" lets you define such incremental schemes, and it compresses your data. Have a look here:

[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

---

### Post by The Cog on 2009-09-05
I am not convinced of the wisdom of compressing backups. Unless you are going to individually compress each file as you back it up, you will have to make one big file like a tar.gz which can be more difficult to deal with than a straight mirror. Also, for many people, the majority of their files they want to back up are music and video files, which are already compressed, so trying to compress them again won't make any significant difference to their size.

---

### Post by Roasted on 2009-09-05
How much would you be able to compress, say, 300gb of data? I don't have the disk space to do incremental backups daily like that, and I do DVD backups of my pictures monthly which is the BIG concern. Music, videos, etc... although I want them, they ARE realistically replaceable - whereas pictures are not.

If I could compress 300gb of data to something obscenely small, then it would make sense for me to throw on incremental (daily?) backups on a 500gb disk. But if 300gb compressed goes to 200gb, well, that's not really helping me out too much there, is it? 

The idea behind me rsyncing wasn't for avoiding corrupt data, files, folders, etc. It was for redundancy since I'm aware enough to realize that hard drives can die at any given time. That was the big reason behind me beginning rsyncing to a 2nd disk - not so much worrying about data corruption.

---

### Post by The Cog on 2009-09-06
Pictures like jpegs are unlikely to compress more than a few percent - try it. Same with videos and music. They are all already compressed.

Although rsync is a good strategy for making sure you have some redundancy, P4man is right that rsync is quite happy to back up corrupted files or to delete files from the backup because the source got accidentally deleted. Some kind of delayed second backup is a good idea. Maybe use DVDs to store all your personal wedding photos etc.

---

### Post by Roasted on 2009-09-06
> **The Cog said:**
> 
Although rsync is a good strategy for making sure you have some redundancy, P4man is right that rsync is quite happy to back up corrupted files or to delete files from the backup because the source got accidentally deleted. Some kind of delayed second backup is a good idea. Maybe use DVDs to store all your personal wedding photos etc.

That's why I have it back up every 12 hours and not every 12 seconds. :) 

But again, what other choice do I have? If I can take 300gb of data, and zip it to 80gb, then compressed backups for me would be ideal cause I have a 500gb hard drive to have daily backups done for the last 3-4 days. But if 300gb of data would only get compressed to 270gb, well, 500gb isn't going to give me more than a day's worth of backup anyway, and I'm in the same boat as rsyncing anyway.

I like rsyncing in the fact that if I do delete something, I can simply bounce to the backup drive and re-copy it to my main drive. Pretty much the same idea as the compressed backups with restoring it, just different I suppose.

I just think the disk space I have available kind of puts a damper on this idea for me to actually use it. However I was just curious about whether or not there was a specific applications like this for linux.

One thing I'm curious about is I've been playing with Ubuntu Server 9.04 in a VM just to see what it's all about. Is there any way to get something like sbackup running on Ubuntu Server? It has no gui, so I'm not sure if sbackup is even an option. Anything like it out there?

---

