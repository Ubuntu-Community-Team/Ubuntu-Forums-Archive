---
title: "Evolution 2.28: Archiving &amp; backup"
date: 2011-01-31
forum: General Help
---

### Post by nicnok on 2011-01-31
I want to create retrievable archives of a my old emails say monthly to avoid the old emails running me out of memory.
If I use the 'Backup Settings' procedure as explained in Evolution Help what happens when I wish to consult the /home/dbus/evolution-backup.tar.gz archive file?
1/ Will it simply over-write my current Evolution data? [in which case its not what I need]
2/ If not, how do I return the archive file to dead storeage and resuscitate my current data? 
3/ If it will overwrite using the 'Restore Evolution' procedure given in Evolution Help is there a workaround ... perhaps by ... 
3a/ renaming the archive file, 
3b/ or 'restoring' it in another version of Evolution,
3c/ or archiving CURRENT data as a 2nd backup with a different name [eg: /home/dbus/evolution-backupJan11.tar.gz?] then restoring that?

4/ Will I be able to retrieve successive archives if I rename them, say '/home/dbus/evolution-backup.tarDec10.gz' etc once Evolution's saved them?

Alternatively the following came from a dead thread [from  [commonlyUNIQU3]("http://ubuntuforums.org/member.php?u=411692") ] ... is it still valid? does it avoid the problem of potentially running out of memory?

[COLOR=Sienna][I]A. Make a subfolder to the "Inbox" under the "On This Computer" tree ( I call mine "Archive")
B. Drag and drop the emails you want to archive into this folder.*  
NOTES: This will move the selected emails  off of your Exchange server/account and into this folder (and into  local storage) - unless you do a copy & paste instead of drag &  drop.  
[/I][I]*You may need to have the setting for downloading emails for offline access enabled for this to work as desired.
If I recall, the new integrated backup feature creates a compressed  (.zip) archive from which you can later restore the email (haven't tried  that just yet).[/I][/COLOR]

---

### Post by Tyler27 on 2011-02-10
What is the command to view archived files within the directory?

---

### Post by nicnok on 2011-02-11
> **Tyler27 said:**
> What is the command to view archived files within the directory?

[FONT=DejaVu Sans, sans-serif][SIZE=2][FONT=Nimbus Sans L, sans-serif]Evolution Help 2.28 says:[/FONT][/SIZE][/FONT]
[FONT=DejaVu Sans, sans-serif][SIZE=2][FONT=Nimbus Sans L, sans-serif]1.3.1 Restoring Evolution from backup[/FONT][/SIZE][/FONT]
[FONT=DejaVu Sans, sans-serif][SIZE=2][FONT=Nimbus Sans L, sans-serif]Select File > [/FONT]Restore Settings to open the available evolution-backup.tar.gz files [takes you to /home/dbus/evolution-backup.tar.gz[/SIZE][/FONT]
[FONT=DejaVu Sans, sans-serif][SIZE=2]select the evolution-backup.tar.gz file [ '/home/dbus/evolution-backup.tar.gzp'] & click 'save'[/SIZE][/FONT]
[FONT=DejaVu Sans, sans-serif][SIZE=2]Before the process starts a popup window appears & asks you to close Evolution.[/SIZE][/FONT]
[FONT=DejaVu Sans, sans-serif][SIZE=2]Close all the windows and then click Restore in the popup window.[/SIZE][/FONT]


[FONT=DejaVu Sans, sans-serif][SIZE=2]I'm also adding a further post in a moment.
[/SIZE][/FONT]

---

### Post by nicnok on 2011-02-11
Found this on [http://live.gnome.org/Evolution/Archiving](http://live.gnome.org/Evolution/Archiving)

**Archiving For evolution 2.14**

 This feature is planned for evolution 2.14 release. 

Its under construction now.
 
**Backup And archiving :**

 Archiving applies to data that is likely to be needed again and logically placing information where it can    be easily found and retrieved. Backup creates a mirrored copy of data, a reserve resource should something   happen to the original data. Retrieval is a slower, more cumbersome process, with the additional cost of   storage involved.
Archiving, requires fast file-level access to data and should involve search and retrieval software and indexed repositories. Whereas backup volumes are usually kept for days before being replaced by new   volumes, archived files can be kept for decades.
  At the very broad view archiving is long term storage and backup is short term.  We archive the things which we will be needing very frequently and it should be easily accessible.  More info on : 1)[http://computerworld.co.nz/news.nsf/news/DDA38125EE52836FCC25723E00071A25](http://computerworld.co.nz/news.nsf/news/DDA38125EE52836FCC25723E00071A25)                 2) [http://www.expresscomputeronline.com/20050919/technology02.shtml](http://www.expresscomputeronline.com/20050919/technology02.shtml)

.......... the article continues .........

Perhaps I just wait & see? When is 2.14 scheduled for release?

---

### Post by howefield on 2011-02-15
> **nicnok said:**
> When is 2.14 scheduled for release?

If you are using Karmic, you are already using a version of Evolution newer than 2.14

---

### Post by nicnok on 2011-02-19
> **howefield said:**
> If you are using Karmic, you are already using a version of Evolution newer than 2.14

Excellent point of course ... have tried to plant a question with the Gnome forum [no response so far]

---

