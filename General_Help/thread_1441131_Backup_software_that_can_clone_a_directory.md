---
title: "Backup software that can clone a directory"
date: 2010-03-28
forum: General Help
---

### Post by Wee_Guy on 2010-03-28
Hi,

I'm looking for software that can backup all the files in my /home directory including hidden files.

I liked [Lucky Backup]("http://luckybackup.sourceforge.net/"), but it puts everything in a tar file, meaning that the backup fails if the file gets too large (4 GB I think). I would prefer to avoid using tar/archives anyway, as often I only need to recover 1 file from a backup (an archive holding my 50 Gb of data would take ages to open).

Does anyone know of a program or a way to get rsync or the like to copy all the files in a directory, including hidden files, into another directory ( so I end up with effectively a carbon copy of the original). Disk space is not an issue so I don't need to compress anything. I'm not bothered whether its a fancy GUI-based program or a rsync command, just so long as it can save my previous files from.... myself.


Thanks in advance for your advice :)

---

### Post by mrmeee17 on 2010-03-28
Yes I would like to know this as well. I need something like WIndows' 'create a system image'. What would you guys recommend?

Thank you.

---

### Post by DasEi on 2010-03-28
take a look to unison, it does incremtal backups, too

also rsync is a very handy tool, see man rsync, it can also use ssh via network for this

for sector based cloning of a whole partition can use dd

---

### Post by jrider on 2010-03-28
> **Wee_Guy said:**
> Hi,

I'm looking for software that can backup all the files in my /home directory including hidden files.

I liked [Lucky Backup]("http://luckybackup.sourceforge.net/"), but it puts everything in a tar file, meaning that the backup fails if the file gets too large (4 GB I think). I would prefer to avoid using tar/archives anyway, as often I only need to recover 1 file from a backup (an archive holding my 50 Gb of data would take ages to open).

Does anyone know of a program or a way to get rsync or the like to copy all the files in a directory, including hidden files, into another directory ( so I end up with effectively a carbon copy of the original). Disk space is not an issue so I don't need to compress anything. I'm not bothered whether its a fancy GUI-based program or a rsync command, just so long as it can save my previous files from.... myself.


Thanks in advance for your advice :)

Grsync is a what I use. Its a GUI for rsync.

---

### Post by Wee_Guy on 2010-04-01
Thanks for the advice folks. I've not tried unison yet as Grsync looks quite promising. The only issue at the moment is getting it to run without permissions issues. I've only tried running it as root once and I managed to direct it to a random folder that had appeared in /media instead of the drive I was aiming for, resulting in the source HD copying data to itself for about an hour before I eventually noticed and facepalmed.

Going to try Grsync as root again later with the correct destination...

---

### Post by merlin_ie on 2010-04-01
well, i dont know if this will really help, but i think its along the right track. i use [COLOR="Red"]remastersys[/COLOR] to backup my distro at least 3 time a week (so if i ruin the distro, i can just burn the iso and reinstall) and its worked perfectly everytime. kept EVERYTHING, even contents in trash lol. hope this helps

---

### Post by Wee_Guy on 2010-04-01
Thanks merlin_ie, remastersys is pretty cool. I might use it to image the whole system before updates or config file tomfoolery, but my user data changes much more regularly, so I intend to backup said data on its own more often. That way, I'm covered for pretty much anything. That's my plan anyway, so either remastersys or clonezilla will be used for the system files, but I need something that can clone my /home directory to another drive (Grsync looks like it might be a winner).

...With my plan now laid out, I seem to want something to go bad just to justify the time spent on this backup scheme... plus I can laugh at people who don't have backups without being hypocritical :)

---

### Post by Irony on 2010-04-01
In terminal do;

```
cd /home

cp -ax * /dir/folder
```

This will copy everything in your home folder to the folder of your choice (where /dir/folder is the actual path you choose)... yes it really is that simple. Note you can do this from your normal GUI, no need to go to shell. You will get an error about gvfs permissions but you can ignore it.

See; [http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

---

### Post by KayakJim on 2010-04-01
Duplicity works very well, especially if you have an Amazon S3 or other off-site storage account.

You could also look into Cloud storage like Dropbox and set it for your entire /home directory.

---

### Post by Wee_Guy on 2010-04-02
I don't want to use cloud storage, as although it does have its advantages, my connection speed would mean it would take around 2 and a half weeks to upload all 50 Gb to a server. I've got loads of unused disk space at the moment so I'm quite happy to just fill that with uncompressed archives.

I don't think Duplicity would work very well for local backups as it uses tar which fails when the tar file gets to 4 Gb in size.

Irony, thanks, that seems to work quite well, bar the small issue of it ignoring symlinks. Can CP replace symlinks with copies of the target file (with the symlinks name) ?

---

### Post by Irony on 2010-04-02
Note sure what you mean - you could just back up the entire root install by not doing *cd /home* and instead just doing;

```
sudo cp -ax * /. /dir/folder
```

There'd only be a couple of gigs more and you would back up everything so that if you messed up your install you would simply copy it back.

---

### Post by Wee_Guy on 2010-04-02
I googled about and have created a text file which can create a folder labeled by date and then use the command Irony mentioned to backup my files. I can now backup the entire system whenever I want in 3 clicks :)

I'm backing up to a drive called Backup, so:
```

mkdir /media/Backup/`date '+%d%m%y'`
cd /
sudo cp -ax * /media/Backup/`date '+%d%m%y'`
```creates folder labelled by date in /media/Backup, then copies system into that folder, you could probably use cron for this too if you wanted.


Edit: Ran Disk Usage Analyser, I suppose another 6 Gb won't really make a big difference to the time it takes. Good point about that being much more useful, don't know why I didn't just do that at first.

---

### Post by Wee_Guy on 2010-04-03
Hows this for Irony?
I was running the backup script above and listening to Spotify (through Wine). HDD's happily churning away. Then Spotify starts jumping like crazy for about 30 seconds. I tried to pause the backup with ```
sudo kill -STOP (pid)
``` but before the terminal had opened the system froze completely. I was forced to do a hard reboot, after which I discovered that none of the programs on my system would open anymore, about half of the menu icons were gone and some system fonts had changed (presumably because it couldn't find the default ones). I restarted it, hoping for the best. GRUB error 17.

Boot off Live CD, Nautilus can't see the Ubuntu partition, but everything else is fine. Gparted can't recognise the format of the Ubuntu partition, which now appears to be rather corrput.

I've not lost any data, my /home partition is fine (for now). Unfortunately that was the only thing I had backed up. Until now I thought that I had some clonezilla images of the Ubuntu partiton, but it turns out I was wrong:cry:

So does anyone have any idea how I could possibly recover this partition? I really don't have the time to reinstall Ubuntu and all my apps and fixes for all the stuff that doesn't work out of the box.

(By the way I'm not trying to say that this is anyones fault, I am rather frustrated though)

---

### Post by Wee_Guy on 2010-04-03
I think I may already know what caused the problem above. A while ago my BIOS mysteriously flashed itself with the wrong firmware, after that my PC froze more and more regularly until it wouldn't boot. I installed some updates this morning, and after I restarted I foolishly ignored the fact that the BIOS had reset its date and time (and eveything else on it). I then booted Ubuntu and it crashed in the middle of the backup, and when I pulled the plug it corrupted the partition. This is the second time my BIOS has 'flashed itself'. As I have never deliberately done so, I can only assume that either 1) Someone else has done so, most probably via the internet or 2) Ubuntu has decided to try and update my BIOS, but flashed it with the firmware for a different mobo.
If I can't figure out what exactly caused this I'm going to just assume it was an update and either never update my system again or resort to running Windows...

I still think its quite ironic that I managed to destroy the thing I didn't have any backups of whilst backing it up :P

---

### Post by Irony on 2010-04-03
Ubuntu doesn't update your BIOS.

I make it a point to never be doing anything on my computer whilst a backup is in progress... afterall it is trying to copy a 'live' system so if you are doing stuff it might make the copy incomplete. However I don't see how the copying could have anything to do with corrupting your system as it not altering anything.

I don't see how your BIOS can be updating itself, it just sounds corrupted.

---

### Post by Wee_Guy on 2010-04-04
Yeah its pretty strange. I don't know how but thats twice now that it has managed to end up with the wrong BIOS on it...

Anyway I'm running Vista on it until I can figure out what caused it. I don't know for certain whether or not it was Ubuntu but I'd rather not chance it.

---

### Post by jcontreras on 2011-10-14
hi,,

good day to you i just want to advice try to visit this link                                      
[http://www.sdrive.co/?click=34](http://www.sdrive.co/?click=34)

for some information of your problem this can may be help you, and i already test this..

---

