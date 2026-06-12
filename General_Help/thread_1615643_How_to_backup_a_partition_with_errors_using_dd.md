---
title: "How to backup a partition with errors using dd?"
date: 2010-11-07
forum: General Help
---

### Post by linuxd00 on 2010-11-07
Hi,

i use the dd command to regularly backup my windows partition.

basically i do:

[PHP]sudo dd if=/dev/sda1 of=./Backupfile.bin bs=100MB[/PHP]

form a USB HDD..

this works charms for backup and restore even over a remote shell.. i have even been able to remotely repair my system from vacation..
now comes the problem:

the partition has developed some I/O errors. Windows has notices and just marked some sectors as being broken/bad.

But dd being Filesystem independent doesnt know and aborts when trying to read and getting an HArdware IO error.

my question:

how can i fix this so i can still backup AND restore the partition? 

i cant afford a new HD at the time.

---

### Post by srs5694 on 2010-11-07
First, make finding the funds for a new hard disk a priority. Bad sectors in hard disks often multiply, so you could be looking at the early stages of a catastrophic failure. If so, the disk could become completely unusable very quickly. If necessary, scrounge a retired but working disk from a friend or relative. Maybe you'll even luck out and be offered something from somebody here.

As to your question, though, there are two Linux tools you might look into:


[list]
[*]**ntfsclone** -- This is an NTFS-specific filesystem cloning tool. It includes a --rescue option that ignores read errors, thus enabling backup of failing disks. Personally, I'd use ntfsclone rather than dd anyhow, since ntfsclone backs up only those sectors that are in use, which results in a smaller backup than dd.
[*]**ddrescue** -- This is a dd variant that does extra passes on bad sectors in an effort to rescue them. This could be useful if the bad sectors contain vital data that you must recover.
[/list]


You could also look into the "noerror" option to dd, which causes it to continue rather than abort when it encounters an error. Type "man dd" and search for "noerror" for details.

Another option would be a Windows-specific backup tool. One I've been using recently is [DriveImage XML.](http://www.runtime.org/driveimage-xml.htm) I don't use Windows that much, so I can't say I have all *that* much experience with DriveImage XML, but I've used it to successfully back up and move a Windows 7 partition from one location on a disk to another, which is always a tricky operation. (Windows gets fussier and fussier about its boot partition with every new release.)

---

