---
title: "Question about how HDD Mountings work"
date: 2011-07-03
forum: General Help
---

### Post by thejoester on 2011-07-03
OK so if this is total noob question please forgive me. 

I have a 320GB sata HDD that I have partitioned out into one 20GB partition and the rest on another.

the 20 GB partition holds my ubuntu OS
the rest holds saved data (documents, movies, pics etc)

Now I notice that the "data" partition mounts in /media/data. However I recently had a problem where the 20GB partition was like 98% full and suddenly I was unable to save any large files to the data partition, it said the disk was full even though it is using 80GB of the total of 290GB. 

I think this has to do with how it mounts in /media/data is this correct?

---

### Post by dino99 on 2011-07-03
nothing related with "mount"

be sure your installation looks like:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by thejoester on 2011-07-03
The title of your post is "New Install Duel Boot system Ub 10.10", this is not a dual boot setup. 

I have a 2GB Swap partition, and a 20GB system for "/" which was recommended in another install guide I read (it could be wrong though). 

The problem is, the Ubuntu partition works fine except it got full (due to some log files growing too big), when this happens I am also unable to save any files onto the other partition which I access through /media/data. For example if I go to [www.ubuntu.com](www.ubuntu.com) and download the latest .ISO and choose to save it on this separate partition then it will fail saying there is not enough space, even though it has plenty of space available.

---

### Post by twipley on 2011-07-03
You have got the necessary permissions to access the drive, right?

using the command "ls -l /media/<label>," you can see.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

If not, then you may have to "chown" your way in.

---

### Post by SeijiSensei on 2011-07-03
If you have /home in that 20 GB partition, perhaps that's what's taking up the space.  Try running this:

```

cd /
sudo du -sx *

```

That will show the amount of space used by each of the major directories on the root.  (The "x" option will keep it from looking at the mounted filesystem on /media.)  How big is /home?  /var?  Once you've identified the big directories, you can cd to each of them and run du again.

---

### Post by thejoester on 2011-07-03
> **twipley said:**
> You have got the necessary permissions to access the drive, right?

using the command "ls -l /media/<label>," you can see.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

If not, then you may have to "chown" your way in.

I do have rights to it. I was able to save to it previously and as soon as I deleted the 13GB of log files that was in /var/log then I was able to save again.

---

### Post by SeijiSensei on 2011-07-03
if you've really generated 13 GB of logs on a workstation, I hope you did some investigation before deleting the logs.  Out of curiosity, which logs were the large ones?

You should install the **logrotate** package if it's not already installed.  You can specify a rotation frequency and the number of old logs to maintain.  By default, things like /var/log/syslog will rotate weekly, usually with four weeks of stale logs kept for reference.

---

### Post by psusi on 2011-07-03
Your web browser is trying to download the file to its cache directory first, and then move it to the final destination.  The cache is presumably on the full drive.

You can use wget to download the file on the command line to get around that silly problem.

---

### Post by thejoester on 2011-07-03
yeah I posted about that here too ([http://ubuntuforums.org/showthread.php?t=1795634]("http://ubuntuforums.org/showthread.php?t=1795634"))

Mainly it was my UFW logging everything and I did not have logrotate on but I do now

---

### Post by dFlyer on 2011-07-03
> **thejoester said:**
> OK so if this is total noob question please forgive me. 

I have a 320GB sata HDD that I have partitioned out into one 20GB partition and the rest on another.

the 20 GB partition holds my ubuntu OS
the rest holds saved data (documents, movies, pics etc)

Now I notice that the "data" partition mounts in /media/data. However I recently had a problem where the 20GB partition was like 98% full and suddenly I was unable to save any large files to the data partition, it said the disk was full even though it is using 80GB of the total of 290GB. 

I think this has to do with how it mounts in /media/data is this correct?

Under linux a 10 - 20 gig partition is great for / (root), but shouldn't include you /home folder which should be holding all your files. My advice is to repartition your HD with a 10 - 20 gig / (root) and the rest of your hard drive should be mounted /home minus what ever you use as a swap file.

---

