---
title: "Folder disappeared... twice"
date: 2011-03-02
forum: General Help
---

### Post by NortySpock on 2011-03-02
TL;DR A folder I use regularly (Music) disappeared last week. I couldn't find any trace of it or any reason for its disappearance. I restored it from backup, only to have it disappear again yesterday. Running Lucid amd64, Ext4. How to I fix this?

My music folder went missing last week. I'm running Lucid (10.04) amd64. I checked the trash, "ls -al", and didn't spot any obvious commands like "rm -rf Music" that would cause this folder to poof out of existence. No joy, it was just GONE. I found some option to force Ubuntu to run its disk check on the next reboot, but it seemed to come up clean. So I restored the folder from backup and kept going.

Yesterday I found the Music folder was missing again. So I did some more digging.

cat /var/log/syslog.1 turned up

```
Mar  1 03:41:05 Spocks-Fist ntfs-3g[1838]: Inode 336289 has corrupt attribute flags (0x8000 <> 0x20): Input/output error
Mar  1 04:17:02 Spocks-Fist CRON[3276]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar  1 04:42:05 Spocks-Fist ntfs-3g[1838]: Inode 336289 has corrupt attribute flags (0x8000 <> 0x20): Input/output error
Mar  1 05:17:01 Spocks-Fist CRON[3465]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar  1 05:43:06 Spocks-Fist ntfs-3g[1838]: Inode 336289 has corrupt attribute flags (0x8000 <> 0x20): Input/output error
Mar  1 06:17:01 Spocks-Fist CRON[3675]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar   1 06:25:01 Spocks-Fist CRON[3705]: (root) CMD (test -x  /usr/sbin/anacron || ( cd / && run-parts --report  /etc/cron.daily ))
Mar  1 06:44:05 Spocks-Fist ntfs-3g[1838]: Inode 336289 has corrupt attribute flags (0x8000 <> 0x20): Input/output error


  					 						

```

Which doesn't seem relevant because the partition in question is formated as ext4. Now, this is a dual-boot system (the other half is Windows 7) and I have a 1.5 TB external formated as NTFS that I use for backups. 

Also, I ran an fsck off of a liveCD on the partition to see if it could find and fix anything.

```
root@ubuntu:/home/ubuntu# e2fsck -pfv /dev/sda5

  678730 inodes used (2.65%)
    2354 non-contiguous files (0.3%)
     679 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 637804/382
74738110 blocks used (72.99%)
       0 bad blocks
      19 large files

  546000 regular files
   83525 directories
      60 character device files
      26 block device files
       0 fifos
     613 links
   49081 symbolic links (40419 fast symbolic links)
      29 sockets
--------
  679334 files

```

What is going on here?

I don't need the data back, I can pull from backups again, but I want to fix the problem and not have to worry about losing other stuff.

---

### Post by fabricator4 on 2011-03-02
Check the smart data to see if the drive is healthy.  If there were any serious problems however fsck should have shown up something

Check whatever script, program, or procedure you are using to do the backups and make sure it's not causing any unexpected behaviour.

Try a file search to see if the files have been moved somewhere.

Directories should _not_ just go missing.

Chris

---

### Post by NortySpock on 2011-03-02
> **fabricator4 said:**
> Check the smart data to see if the drive is healthy.  If there were any serious problems however fsck should have shown up something

SMART comes up healthy.

> **fabricator4 said:**
> 
Check whatever script, program, or procedure you are using to do the backups and make sure it's not causing any unexpected behaviour.


My backup procedure is
```
rsync -avzh <source> <target>
```I sort of doubt that's causing an issue.

> **fabricator4 said:**
> 
Try a file search to see if the files have been moved somewhere.
 

```
locate Music
``` with some grep pipes to clean out cruft ( locate Music | grep norty | grep -v stuff) plus a Mk 1 eyeball grepping shows nothing of interest.

I also tried a Nautilus-based search / eyeball grep, with nothing interesting found.

> **fabricator4 said:**
> 
Directories should _not_ just go missing.

Chris
That's what I thought too... Thanks for the help so far. Please keep it coming.

---

### Post by fabricator4 on 2011-03-02
> **NortySpock said:**
> SMART comes up healthy.[quote]

Did you force it to do a test?  It should have shown if there was a problem but I'm never happy until I've let it run at least the quick test.

Even so, a problem bad enough to lose a directory should have fsck waving error flags all over...

[quote]That's what I thought too... Thanks for the help so far. Please keep it coming.

My suggestions get sillier...

Do you use Nautilus much?  Check to see if you got Nautilus to confirm on deletes. A few times I've been tempted to turn confirmation off, then got smart and left it alone :-)

Silly question #99...   ~/Music doesn't equate to a mount point or a link at any point does it?

Chris

---

### Post by NortySpock on 2011-03-03
> **fabricator4 said:**
> 
Did you force it to do a test?  It should have shown if there was a problem but I'm never happy until I've let it run at least the quick test.

Even so, a problem bad enough to lose a directory should have fsck waving error flags all over...

I forced it to do the extended test, but when it took over 30 minutes I canceled it and went with the quick test. The quick test came up clean.

> **fabricator4 said:**
> 
My suggestions get sillier...

Do you use Nautilus much?  Check to see if you got Nautilus to confirm on deletes. A few times I've been tempted to turn confirmation off, then got smart and left it alone :-)

I use nautilus about as much as I use the command line, so it's 50/50. I don't see an option in Nautilus Preferences to confirm delete. I do have an option to confirm emptying the trash (checked) and an option to have a separate delete command that bypasses the trash (unchecked).

In either case, I don't think I accidentally hit the delete button too often -- I've been using the system for about a year without issue.

> **fabricator4 said:**
> 
Silly question #99...   ~/Music doesn't equate to a mount point or a link at any point does it?

Chris
No, I don't recall setting anything up like that.

FYI, I've restored the folder from backups again, so we'll see if it has taken a liking to running off to the Great Hard Drive in the Sky...

---

### Post by fabricator4 on 2011-03-04
> **NortySpock said:**
> 

FYI, I've restored the folder from backups again, so we'll see if it has taken a liking to running off to the Great Hard Drive in the Sky...

Well, good luck.  I hope it stays where it's supposed to. I can't help feeling that the answer is right there in front of us somewhere.

---

### Post by heitzmann on 2012-04-14
Are you using Linux DC++?
I've had this problem as well, but I found all files inside a folder in ~/.dc++/FileLists

Take a look at [https://bugs.launchpad.net/linuxdcpp/+bug/879475](https://bugs.launchpad.net/linuxdcpp/+bug/879475) and [https://bugs.launchpad.net/dcplusplus/+bug/551184](https://bugs.launchpad.net/dcplusplus/+bug/551184)

---

