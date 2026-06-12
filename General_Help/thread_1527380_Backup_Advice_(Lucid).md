---
title: "Backup Advice (Lucid)"
date: 2010-07-09
forum: General Help
---

### Post by rsvr85 on 2010-07-09
Hello everyone,
Coming from Windows and being used to the built in backup/restore/recovery tools, I've found myself a little stumped trying to backup my Lucid install.
I've been reading through the forums on which backup software does a good job and have decided to installed luckyBackup & Back In Time.

As mentioned, I'm quite new to Linux and will inevitably hose the OS at some point so what I want to achieve is this;  A full document backup once per week and an OS/settings backup every night.  The document backup can be incremental but i wish the OS & settings to save as individual archives. 

Which locations do i need to specify for the OS & settings?, i tried backing up "/" but of course the destination disk (external hdd) is in that location and luckybackup threw an error.

TIA for any advice, it's greatly appreciated! :D

---

### Post by AlphaLexman on 2010-07-09
Even physically external hard drives are "inside" of '/', they may be mounted in /mnt or /media (depending on your setup) so doing a backup of '/' will backup ALL mounted drives whether they are in /mnt or /media or wherever.

rsync, a command line tool, does a good job of backing up (or syncing, hence the name) your files/data. It has an option '--exclude' to not backup/sync whatever you tell it not to.

There is also a gui alternative 'Grsync' in the repo's.

---

### Post by rsvr85 on 2010-07-09
Thanks AlphaLexman i'll look into rsync.  
So, which locations will i need to specify to backup all of my settings and the OS?  Also, after i have backed up the settings how will i import them back in?  Is it a  case of overwriting the current files/folders or will i need a special backup software?  
Regards :D

---

### Post by AlphaLexman on 2010-07-09
ALL of your settings are in your /home/yourusername/ folder. Settings are typically stored in hidden files or folders (beginning with a dot . ) You can see these by typing:
```
ls -a
```
in a terminal window.

I personally backup (and not as often as I should) for my OS the following:

[LIST]
[*]/bin
[*]/boot
[*]/etc
[*]/lib
[*]/root
[*]/sbin
[*]/sys
[*]/usr
[*]/var
[/LIST]

---

### Post by philinux on 2010-07-09
I have /home on it's own partition and never backup the os.

I just backup important stuff from /home.

If you want a backup of just the OS this is good.

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by rsvr85 on 2010-07-09
Ok so just to be 100% sure (sorry!) ... backing up **/home/me** should see me ok to restore documents and settings?

Scenario:
Tonight i make a complete back up of **/home/me**.  Tomorrow morning i'm messing about and break the system.  
Can i just copy the backed up /home/me to the obvious place and all will be well?

---

### Post by AlphaLexman on 2010-07-09
A backup of /home/you will only save/restore your settings. You can mess things up with sudo if you are not careful. Read the man pages before doing ANYTHING you feel uncomfortable about. When I first started with ubuntu I read man pages before running ANY command I got of the internet. I learned quickly.

---

### Post by philinux on 2010-07-09
> **rsvr85 said:**
> Ok so just to be 100% sure (sorry!) ... backing up **/home/me** should see me ok to restore documents and settings?

Scenario:
Tonight i make a complete back up of **/home/me**.  Tomorrow morning i'm messing about and break the system.  
**Can i just copy the backed up /home/me to the obvious place and all will be well**?

No. Think of home like my documents and settings. Not the OS.

---

### Post by rsvr85 on 2010-07-09
> **philinux said:**
> No. Think of home like my documents and settings. Not the OS.

So how do i go about backing up the OS & its settings? (think migwiz.exe).

Thanks

---

### Post by philinux on 2010-07-09
> **rsvr85 said:**
> So how do i go about backing up the OS & its settings? (think migwiz.exe).

Thanks

No idea what migwiz is.

See post #5 for remastersys.

---

### Post by rsvr85 on 2010-07-09
Thanks for your input guys.  I'll look into all methods mentioned.

[migwiz.exe]("http://en.wikipedia.org/wiki/Windows_Easy_Transfer")

---

### Post by rsvr85 on 2010-07-09
remastersys is the best solution for me.  My follow up question is; can i set things up to run remastersys every night, (which saves the .iso in my home folder), once remastersys has completed, copy the iso to an external drive and replace/delete any existing image?
(When i set the external as the working directory in the options it complained of the directory no being found????)

Thanks

---

### Post by AlphaLexman on 2010-07-09
There is really no reason to backup your entire OS nightly. Besides saving the .iso to your /home folder, makes your backups of your documents and settings larger with that .iso in it. Redundant.

---

### Post by philinux on 2010-07-09
> **AlphaLexman said:**
> There is really no reason to backup your entire OS nightly. Besides saving the .iso to your /home folder, makes your backups of your documents and settings larger with that .iso in it. Redundant.

Remastersys uses /home/remastersys and not /home/username

However nightly seems overkill. And there is a 4gig limit to created iso.

That's an iso spec limit and not remastersys.

---

### Post by rsvr85 on 2010-07-12
I like remastersys thanks for the tip philinux!

I've done as advised and separated "/home" and "/" into two partitions.

I made an full-backup ISO (i omitted "/home") with remastersys and installed in a VM, after installation everything was as expected.  
If i reinstalled my main system with my ISO will the system automatically take on the existing "/home" partition and all settings/programs etc. be restored?

---

