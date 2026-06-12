---
title: "Need alternative to Simple backup"
date: 2009-07-03
forum: General Help
---

### Post by mookie60 on 2009-07-03
I currently use Spideroak for online backups, that works fine for that purpose.  However I'd also like to do a recurring (daily) backup to an attached usb drive.

I've tried ubuntu's Simple backup, but I don't like backups that roll everything into one big file.  I'd like to be able to have normal access (via nautilus) to the backed up files without restoring them.   . . . being a NOOB, I need something with a GUI.

I've seen some webpages that have lists of backup pgms, but they don't ever seem to address that issue of rolling the files into a single archived file.   I also tried something called Bacula - wayyy big and complicated for my needs.

Thanks for any suggestions.

John

---

### Post by earthpigg on 2009-07-04
have you considered using dd?

[http://www.backuphowto.info/linux-backup-hard-disk-clone-dd](http://www.backuphowto.info/linux-backup-hard-disk-clone-dd)

edit: yes, you may have to run 'man dd' and read the manual to get exactly what you want.... the price you pay for absolute control is lack-of-ease-of-use :D

---

### Post by mookie60 on 2009-07-04
From the link, it looks like this is for cloning the hard drive.   

I really only want to back up my Home folder to the usb drive.   In particular, I'd like to backup my Evolution email file.  This is a single, very large file which I don't want to routinely update (to the cloud) using Spikeroak. 

Thanks for the suggestion.

---

### Post by DeMus on 2009-07-04
> **mookie60 said:**
> From the link, it looks like this is for cloning the hard drive.   

I really only want to back up my Home folder to the usb drive.   In particular, I'd like to backup my Evolution email file.  This is a single, very large file which I don't want to routinely update (to the cloud) using Spikeroak. 

Thanks for the suggestion.

When you want to back-up your Home folder and still be able to have all the files as individual files in the back-up why not simply make a script?
```
Open a terminal
```
type ```
gedit back-up and hit enter
```
In the openend text file you type:
```
cp -R -u /home/username/* /destination/
```
You have to rename username with your name and destination with the path where you want to have your back-up.
```
Save the file
```
Then type:
```
chmode +x back-up
```
to make it executable
Now you only have to make a launcher on your desktop.
On the desktop, right-click on an empty space, choose make launcher from the menu and type what I wrote in the attached picture. Again replace "username" with your name

Explanation:
-R takes care that all folders are copied as well
-u only copies those files which are newer than the ones in the back-up and the ones which are not there already

---

### Post by mookie60 on 2009-07-04
I generally have a command-line phobia . . . but I'm going to give it a shot


Thank you DeMus

---

### Post by niteshifter on 2009-07-04
Hi,

rsync does what you want. Here's a simple three-liner script I use to backup my home folder:
```

#!/bin/bash
sudo rsync -av --progress --delete --log-file=/home/[COLOR="Red"]niteshifter[/COLOR]/Desktop/$(date +%Y%m%d)_rsync.log /home/[COLOR="Red"]niteshifter[/COLOR] [COLOR="Lime"]/media/ExtWD250/rsync_home_ns[/COLOR]
sudo chown [COLOR="Red"]niteshifter[/COLOR]:[COLOR="Red"]niteshifter[/COLOR] /home/[COLOR="Red"]niteshifter[/COLOR]/Desktop/*_rsync.log
```

It duplicates the file and folder structure of my home on an external drive, no big-a** tarballs to deal with ;) It's much quicker than tarballing, also avoids subtle problems that cp alone can have.
```
man rsync
```
for all about rsync.

Notes:
Preserves file and folder permissions (the -a option).
It shows what it's doing (the v and --progress options).
Deletes files from the destination that are no longer in the source (the --delete option).
It creates a date prefix log file on the desktop (the --log-file= )
I have sudo there because from time to time files or folders owned by others may be present. Drop the sudo before rsync if all files and folders are owned by you, drop the chown line also.
Change text marked in red to your username, change the green to the path for your external drive.
Restoring is easy: just swap source and destination terms

---

### Post by alphacrucis2 on 2009-07-04
There is a graphical front end for rsync available in the repos. Take a look at grsync.

---

### Post by mlissner on 2009-07-04
If you can get past your command line phobia, rsnapshot is a wrapper program around rsync that can give it a LOT more power. It works great for automated backups of whatever you can imagine.

Personally, I have it run every day, week and month, and I can go back and browse any of those snapshots in time whenever I want. Pretty slick.

---

### Post by mike555 on 2009-07-04
you might want to try "Back in time" from ;   [http://backintime.le-web.org/](http://backintime.le-web.org/)      , it works very well for me ......

---

### Post by blueridgedog on 2009-07-04
+1 for rsync.  It is a fantastically simply and effective tool and with media prices what they are today, there is no reason to try and use an old fashioned backup process when a live copy can be had for pennies on the gig.

---

### Post by DeMus on 2009-07-04
> **alphacrucis2 said:**
> There is a graphical front end for rsync available in the repos. Take a look at grsync.

Just installed grsync, saw that rsync was installed already, and it runs fantastic. Many options to set or unset and then....go.
Thanks for the tip.

---

### Post by mookie60 on 2009-07-04
Grsync looks like a good solution for me.  I have DeMus's script working, and now can try Nightshifter's.

Thanks one and all.

---

