---
title: "Back up/Sync Utility w/ Schedule and Network Access?"
date: 2011-04-04
forum: General Help
---

### Post by Rubicon421 on 2011-04-04
What's a good back up utility with a scheduling feature that can back up  to a network hard drive? I'm backing up to an NTFS formatted external  that is connected to my router and I would like the files to be backed  up individually so they can be browsed by other PCs (Windows &  Linux) on my network, as opposed to a disc image or archive like some  back up programs.

---

### Post by mendhak on 2011-04-04
I think you may have to use two applications for this.  The first could be a backup utility such as [rsync]("https://help.ubuntu.com/community/rsync").  So create a script that uses rsync to write to your external drive.  Then use [crontab]("https://help.ubuntu.com/community/CronHowto") to schedule that script to run every X hours.

---

### Post by Rubicon421 on 2011-04-04
I tried grsync which is a GUI front end for rsync but I can't navigate to my network HD to choose it as a destination. I get a open/save dialog browser window that has the Places side bar but it only shows local devices and bookmarked folders. I have a bookmark already created for the network drive too but it doesn't show up.

---

### Post by mendhak on 2011-04-04
Ah, have you mounted the network hard drive yet? That drive won't show up for you in places unless you've mounted it.  It sounds like you have a NAS if it's connected to the router. 

There are two ways you can do this - you can either have that NAS mounted all the time, or you can only mount it when you run your script.  It's your preference, really.

Assuming you go for the always-mounted option, that means you'll need to add an entry to your /etc/fstab file.  You'll find a lot of threads talking about how to do this but here's [one]("http://68.12.217.177:8080/wordpress/?page_id=92").

---

### Post by Rubicon421 on 2011-04-04
It's not technically a NAS device because it only has USB but my router has a USB port (Netgear Readyshare) and it is currently mounted. I can access it in Nautilus and have read/write access. I don't have it set to automount yet but I rarely restart my machine and I'd rather get the backup working first before I mess with fstab.

---

### Post by mendhak on 2011-04-04
If you browse to it in Nautilus and press Ctrl+L, do you get the path in the address bar?  You could copy that path and paste it into the grsync app you mentioned earlier.

---

### Post by Rubicon421 on 2011-04-04
Didn't know about the cntrl+L trick. Thanks! That will come in helpful again in the future I'm sure. I got a little further but still having a problem. I input the destination folder location using the path from Nautilus when I pressed cntrl+L and got this error when I ran a simulation:

*** Launching RSYNC command (simulation mode):
rsync -r -n -t -v --progress -s /home/droid/Desktop smb://readyshare/wd2tb/Droid_BackUp

ssh: Could not resolve hostname smb: Name or service not known 
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(601) [sender=3.0.7]
Rsync process exit status: 255

BTW, if anyone knows of a different program for syncing/back up, I'd like to try others as well. I started setting up Crash Plan and thought it was going to be perfect for what I needed but it turns out that it's back ups are stored in some proprietary format that can't be browsed.

---

### Post by Rubicon421 on 2011-04-04
I use Syncback in Windows and I really like the interface so I'd like to find something like it. I just found sbackup so I'm going to give it a try.

---

### Post by Rubicon421 on 2011-04-04
Sbackup also uses compression and archiving so the back up is not browsable. I'm thinking it might be easier to just copy the folders manually and choose overwrite all for the changes then manually delete any files that I had removed from the source. 

I'm trying to keep a back up of music and pictures. If I move folders around, rename files or delete them in the source, I would like this to be reflected in the destination. There has to be a simple program for this that has network access. I could live without a scheduling feature and run it manually if needed.

---

### Post by mendhak on 2011-04-05
OK, for the simulation you did, try using the IP address instead of the hostname.  So it should be an IP address instead of 'readyshare'.  Reason is, the error message indicates something of this nature

> 
Could not resolve hostname smb: Name or service not known 

Do you happen to know an IP address for that share?

Edit:  The IP address will most likely be the IP address of the router itself (for example, 192.168.0.1)

---

### Post by mendhak on 2011-04-05
I'm using a program called [Unison](http://www.cis.upenn.edu/~bcpierce/unison/).  Unison takes two folder paths, so it means you'll need the ReadyShare folder mounted.  It then goes through both folders and does a comparison.  The first time you run it, it takes a long time.  Subsequent runs are generally faster.  You could give that a shot if the IP address fails you above.

---

### Post by Rubicon421 on 2011-04-05
The router firmware has a 'share over HTTP' feature but I have not enabled it yet. I figured since I am able to browse the drive in Nautilus and have read/write access that I should try to get it to work as is without enabling any more "security holes" than I have to.

---

### Post by AxelBlade on 2011-04-05
have u tried FreeFileSync?

---

### Post by Rubicon421 on 2011-04-05
> **AxelBlade said:**
> have u tried FreeFileSync?

Yes, I tried it a few days ago and it seems to have similar problems accessing the network drive. I may just end up enabling the HTTP or FTP access but it seems like that shouldn't be necessary since Nautilus can already access it.

---

