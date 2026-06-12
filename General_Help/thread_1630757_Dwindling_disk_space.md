---
title: "Dwindling disk space"
date: 2010-11-25
forum: General Help
---

### Post by rmcellig on 2010-11-25
Something is taking up a lot of space on my HD. I have about 2GB left and want to know what the best tool is to use so that I can find out what exactly is taking up all the space so I can delete it or move it to another drive.

---

### Post by drs305 on 2010-11-25
You can go through this guide - there are GUI and command line suggestions for finding out what's taking up your disk space:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

Most common: undeleted trash (your's and root's), large log files, and backups (by sbackup, etc) mistakenly made on / instead of another mounted partition .

---

### Post by Enigmapond on 2010-11-25
System/Administration/Disk Utility.....

---

### Post by rmcellig on 2010-11-25
When I do properties on my Home folder it is only 5.4MB. My Linux partition is 77GB. What could be taking up the rest of the space. Should I do properties on some of the folders in my File System?

---

### Post by Gunman1982 on 2010-11-25
You could clean up your cache of downloaded packages. Open a terminal and execute 'sudo apt-get clean;sudo apt-get autoclean' and check again how much free space you have.

---

### Post by rmcellig on 2010-11-25
I just ran xdiskusage and this is what I came up with. Could it be these backups that are causing the problem? If so how can I delete them?

---

### Post by rmcellig on 2010-11-25
I finally found the files I want to delete but I am not sure how to delete them for good.

---

### Post by matt_symes on 2010-11-26
Hi

If you are sure you want to delete them all...

Press the shift key and select them all and press, with the shift key still pressed, delete.

EDIT: Note to self.. Stop speed reading posts  

Kind regards

---

### Post by drs305 on 2010-11-26
You can open a file browser as root:
```
gksu nautilus /root/.local/share/Trash/files
```

Highlight the files, then use SHIFT-DEL to delete them. If you just press DEL, they will reappear.

For a command line method to delete them, see the link I referenced in Post #2 . It's all there.

---

### Post by rmcellig on 2010-11-26
Thank you so much!!! Now I have almost 60DB of free space!!! What could have caused that to happen?

---

### Post by drs305 on 2010-11-26
> **rmcellig said:**
> Thank you so much!!! Now I have almost 60DB of free space!!! What could have caused that to happen?

I noticed the files were stored on /media. In most cases, the backups are set up to be written to a removable drive mounted on /media at the time of the backup. If the removable drive is not mounted, the backup occurs anyway. Instead of being written to the removable drive, the files are written to the /media folder on the / partition.

When checking disk space on the / partition, it is best to unmount all non-system partitions first so that you only see what is physically written on the / partition itself. It helps find problems such as this, since there would normally be no files in /media unless something was mounted.

---

### Post by rmcellig on 2010-11-26
> **drs305 said:**
> I noticed the files were stored on /media. In most cases, the backups are set up to be written to a removable drive mounted on /media at the time of the backup. If the removable drive is not mounted, the backup occurs anyway. Instead of being written to the removable drive, the files are written to the /media folder on the / partition.

When checking disk space on the / partition, it is best to unmount all non-system partitions first so that you only see what is physically written on the / partition itself. It helps find problems such as this, since there would normally be no files in /media unless something was mounted.

Thanks for the explanation! What should I do in the future so that if the drive is not available, the backup would not take place. In other words, the backup would only take place if the target drive was available, otherwise nothing will happen. This is what I would like as the backup behaviour. I am using Simple Backup just to see how backups are done in Ubuntu.

---

### Post by QLee on 2010-11-26
[QUOTE=rmcellig]...What could have caused that to happen?[/QUOTE]

This is the situation I cautioned you about yesterday in the thread where you asked about Using rsync to sync folders.
[http://ubuntuforums.org/showthread.php?p=10161950#post10161950](http://ubuntuforums.org/showthread.php?p=10161950#post10161950)

Remember to consider it when you use that scheduled task rsync command that aeiah gave you. Although, I imagine you'd find it faster next time.

---

### Post by rmcellig on 2010-11-26
Yes. Now I understand what you were saying and thanks so much for the heads up. I learned something here and I feel good that I did, so now if I try rsync to sync two folders, what should the code look like so that rsync will only work if the target volume is available.

I plan on putting the code in Scheduled Tasks so that I can set up a schedule for the syncs.

---

### Post by drs305 on 2010-11-26
If your backup program doesn't offer a way to check to see if the partition is mounted, you can use a script such as the following. If you Google "bash check drive mounted" you will get lots of different ways of doing this.

Essentially you would want to create a script which checks to see if the backup partition is mounted before running the backup app. If the partition is not mounted, either stop or try to mount the partition and then check again.

In its simple form it would look something like this:

> #!/bin/bash

grep "/media/mybackups" /etc/mtab > /dev/null
if [ $? -eq 0 ] ; then 
*insert the command to run the backup here*
else 
*exit or try to mount the partition here*
fi

---

### Post by QLee on 2010-11-27
[QUOTE=rmcellig]Yes. Now I understand what you were saying and thanks so much for the heads up. I learned something here and I feel good that I did...[/QUOTE]

Great, that's why we're doing this, to help each other learn, it's so much more satisfying than answering the same 10 questions over and over, eh. ;-)

Replied to other thread too but you've already got an excellent answer and a method to search for others.

When you have your draft script ready, you can post a thread and ask for suggestions, there are some very good coders who scan the forums and make suggestions, sometime even the disagreements among them can be instructive. I'm only a mediocre coder anyway.

---

