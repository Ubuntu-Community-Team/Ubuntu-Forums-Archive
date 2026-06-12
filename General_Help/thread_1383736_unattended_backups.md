---
title: "unattended backups"
date: 2010-01-17
forum: General Help
---

### Post by jsprenkl on 2010-01-17
Good afternoon.

I'm trying to find a way to backup my files to cdr/dvdr. I'd like to put a blank disk in when I finish using the machine, have it backup anything new, up to the size of the media and stop. I can put in new media the next day and I'd like it to continue from where it left off. It would be best if the backups are readable by any machine and I could extract specific files if a problem should arise. Any suggestions? Tar won't let me specify a final archive size and wants to do all the volumes in the backup at the same time.

Thanks!

---

### Post by warfacegod on 2010-01-17
This isn't quite what you are talking about but to me seems like less your if you do it only once or twice a month.

[http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

---

### Post by tom4everitt on 2010-01-17
I'm not sure I understand completely, 

your whole system will never fit one cd/dvd, right? so you will never have one full backup... how are you going to restore from such a backup?

and then you want save any changes to new cds every day, but not any changes exceeding, say, 700 mb? do you want to save those changes the next day or never? how is the system going to keep track on what has been saved on what has not?

I might miss something, but this sounds extremely complicated. Easier (and perhaps not so much more expensive in the long run) would be to buy an external hard drive, on which you keep a few backups. This is an excellent guide for that:
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

or you can just use some program such as lucky backup.

---

### Post by jsprenkl on 2010-01-17
> **tom4everitt said:**
> I'm not sure I understand completely, 

your whole system will never fit one cd/dvd, right? so you will never have one full backup... how are you going to restore from such a backup?

and then you want save any changes to new cds every day, but not any changes exceeding, say, 700 mb? do you want to save those changes the next day or never? how is the system going to keep track on what has been saved on what has not?


I don't want to restore the system files, only my own new content. If my machine dies and I buy a new one the hardware will be different so restoring settings/programs for the wrong hardware would be a disaster.

Restoring a damaged file/files should be as simple as sticking in the cd and using tar or unzip to expand the files onto my new hardware.

It should be relatively simple to create a database of what was backed up and what was not (since linux doesn't include an archive bit in the file system).

I didn't want to write my own if I didn't have to. This seems like it should already exist somewhere. Didn't people deal with tape drives on unix for decades?

---

### Post by DestructionsRightHand on 2010-01-17
Giving the cost per daily cd's to a external disk that can do incremental backups does it have to be cd's?

---

### Post by falconindy on 2010-01-17
> **jsprenkl said:**
> I don't want to restore the system files, only my own new content. If my machine dies and I buy a new one the hardware will be different so restoring settings/programs for the wrong hardware would be a disaster.
No, it wouldn't, as hardware is detected and accommodated for at every bootup. As long as your kernel is robust enough to handle the hardware changes and you alter the appropriate system files, there's no issues changing out the entire system from underneath linux.

> **jsprenkl said:**
> Restoring a damaged file/files should be as simple as sticking in the cd and using tar or unzip to expand the files onto my new hardware.
Sure, that's the goal of any backup system. An incremental backup system on more accessible hardware would make this far easier to implement, rather than having multiple CDs. How would you know what file is on which CD?

> **jsprenkl said:**
> It should be relatively simple to create a database of what was backed up and what was not (since linux doesn't include an archive bit in the file system).
Sense. This makes none. If Linux provides no archive bit, how is it easy to know when a file was last transferred? You can only know when it was last modified or accessed (if your FS supports it and is mounted appropriately). Tar and rsync have the ability to do an update (copy if source is newer than dest), but on a read only file system this isn't possible (well, not 100% true, but assume it is for simplicity's sake).

> **jsprenkl said:**
> I didn't want to write my own if I didn't have to. This seems like it should already exist somewhere. Didn't people deal with tape drives on unix for decades?
Sure. You know about tar -- short for tape-archiver. There's plenty of options in there that wreak of being associated with tapes. Among the less interesting ones are...
```
       -L, --tape-length N
              change tapes after writing N*1024 bytes
       -M, --multi-volume
              create/list/extract multi-volume archive
```

---

### Post by falconindy on 2010-01-17
edit: oops, dbl post

---

### Post by jsprenkl on 2010-01-17
> **falconindy said:**
> No, it wouldn't, as hardware is detected and accommodated for at every bootup. As long as your kernel is robust enough to handle the hardware changes and you alter the appropriate system files, there's no issues changing out the entire system from underneath linux.

Not if the correct device drivers are not installed. I've found it difficult to get Linux to work properly with my hardware even when it's properly installed.

---

### Post by jsprenkl on 2010-01-17
> **DestructionsRightHand said:**
> Giving the cost per daily cd's to a external disk that can do incremental backups does it have to be cd's?

An excellent point I think...

---

### Post by jsprenkl on 2010-01-17
> **falconindy said:**
> Sense. This makes none. If Linux provides no archive bit, how is it easy to know when a file was last transferred? You can only know when it was last modified or accessed (if your FS supports it and is mounted appropriately). Tar and rsync have the ability to do an update (copy if source is newer than dest), but on a read only file system this isn't possible (well, not 100% true, but assume it is for simplicity's sake).


To make up for the missing archive bit do the following:

Create a database.
create a row with a timestamp when you archive a file and to which disk you saved it. Give them an arbitrary number or some identifier.
When backing up check the modified date on each file against the database. If it's newer then back it up again. If the fs has the modification date tracking feature turned off save a hash and size of the file. You can detect changes by rehashing the files and comparing against the database.

---

### Post by falconindy on 2010-01-17
> **jsprenkl said:**
> Not if the correct device drivers are not installed. I've found it difficult to get Linux to work properly with my hardware even when it's properly installed.
I think you should educate yourself about Linux drivers work (and how they're vastly different from Windows drivers). If driver support wasn't as it is, liveCDs would be a horrible failure. They're clearly not. There's also a reason Windows doesn't make LiveCDs.

> **jsprenkl said:**
> To make up for the missing archive bit do the following:

Create a database.
create a row with a timestamp when you archive a file and to which disk you saved it. Give them an arbitrary number or some identifier.
When backing up check the modified date on each file against the database. If it's newer then back it up again. If the fs has the modification date tracking feature turned off save a hash and size of the file. You can detect changes by rehashing the files and comparing against the database.
So every time I want to do a backup, I need to lookup, possibly hash, and compare 72000 files with a list of equal or larger (due to garbage accumulation) size? Yikes. I suspect my backup is small compared to yours as well (~3GiB uncompressed), given that you suggest the need for multiple DVDs.

Curious -- what is your aversion to using an external hdd? Your goal is unattended backups, but you want to be responsible for manually switching removable media if need be?

---

