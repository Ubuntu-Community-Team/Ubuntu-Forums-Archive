---
title: "Backup Solutions"
date: 2011-04-17
forum: General Help
---

### Post by MaximB on 2011-04-17
Hello !

I am looking for a total backup solution for my company.
We have a mixed environment with Windows and Linux servers.
And about 2TB to backup each week (or less).

I want to be able to restore the OS from bare metal, and I want to make regular backups of the data (and the mail which is exchange 2003).
Also I would like to preserve Linux and Windows permissions.

What can you recommend ?

---

### Post by Dutch70 on 2011-04-17
Will Clonezilla not do what you need? 
[[COLOR="RoyalBlue"]http://clonezilla.org/[/COLOR]]("http://clonezilla.org/")

---

### Post by earthpigg on 2011-04-17
assuming the MBR and similar haven't changed, can you use rsync or similar to overcome:

> 
Limitation:
# Differential/incremental backup is not implemented yet. 

without sacrificing reliability?


(not that it is relevant to me, but because that would be my next question in the OP's shoes :P )

---

### Post by MaximB on 2011-04-17
> **Dutch70 said:**
> Will Clonezilla not do what you need? 
[[COLOR="RoyalBlue"]http://clonezilla.org/[/COLOR]]("http://clonezilla.org/")

Sorry but Clonezilla suffers from many limitations, the system/partition must be down - and we can't have that in a production environment (unless it's a one time only just to close the OS).
Also it clones the disks ,and if we have several servers (Windows and Linux) with different places to backup - cloning could be a problem).

I was thinking about Rsync BUT :
1. It doesn't backup OS's and cannot restore from bare metal.
2. It doesn't keep Windows permissions.

---

### Post by MaximB on 2011-04-20
No more replys ? wow, the UF really died out since the times I was active...
Really sad :(

---

### Post by Lars Noodén on 2011-04-20
Bacula is popular.

Myself, I'd go with rsync over SSH.

---

### Post by collisionystm on 2011-04-20
I use Rsync.
 
I have Windows and linux servers as well.
 
Just create a backup server with ubuntu. Mount the Windows Partitions with samba ( add to fstab to make permanent ) 
 
Use SSH rsa keys for your linux boxes.
 
crontab the rsync commands and voila, your stuff is backing up. Check the rsync --help in terminal to see what each command switch does as far as permissiosn go.
 
Oh and if you are looking for a BETTER way to backup, use rsnapshot. It does 1 full system backup and then does daily backups, Inside of these daily backups is only the files that changed that day. That way you can always restore your files with good ones.

---

### Post by earthpigg on 2011-04-21
> **MaximB said:**
> No more replys ? wow, the UF really died out since the times I was active...
Really sad :(

well, you may or may not like it but the most 'perfect' solution is also the 'stupidest' one. stupid being a good thing, in this case.

[https://wiki.archlinux.org/index.php/Disk_Cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)
[http://en.wikipedia.org/wiki/Dd_%28unix%29](http://en.wikipedia.org/wiki/Dd_%28unix%29)

it doesn't attempt to be intelligent in any way, it just copies ones and zeroes sequentially from an input (if=) to an output (of=). all permission and everything else will be completely unmodified - even corrupted files or filesystems will have those corruptions cloned intact. 

bonus points: i'm pretty sure if the input hard drive and output hard drive are the same exact make/model/etc, you could probably just take the old hard drive out, slap the 'backup' hard drive into the computer, and boot from that. never done that, but i believe my theory to be sound.

---

### Post by MaximB on 2011-04-21
Thanks for your replys.

I love rsync, but it won't save Windows files/folder permissions (and it's important as our file server is Windows, don't ask me - it was there when I arrived ;) ).

Why is Rsnapshot better then rsync ? (I know the differences between them, but rsync has it all synchronized and backup up, why do you need rsnapshot ?).

DD is out of the question - it'a a MAJOR space waste, any imaging program would be more efficient.

---

### Post by collisionystm on 2011-04-21
Well rsnapshot comes in handy for this reason.....
 
If a user deletes a file on accident, or breaks a file and does not tell you... then your system runs a new backup....you now only have a backup of the broken file.

---

### Post by re1d on 2011-04-28
System76 laptop, 10.04, 320GB HDD, VMware with Win7 in one VM; want to use Clonezilla as am using it to back up another older smaller dual-boot Ubuntu/XP machine. This is a work machine that I control, the VM only does a couple of things but they're necessary for work.

My question is what FS to use on the backup drive; for instance, for the dual-boot Win/Linux work machine I'm currently backing up, I'm using a 30GB external HDD formatted in FAT32. That's OK because it's beneath the limit for FAT32. But for the newer laptop I'll need a bigger backup partition. I chose FAT32 for the other one because I know everything on the computer being backed up, Windows & Linux both, are compatible with it. 

What FS should I use to back up the new laptop, considering that I'll be backing up the Win7 VM as well as the Linux part of the machine? I plan to use a backup partition of about 160GB. Could I format it NTFS and have it work with Ubuntu 10.04? Or, conversely, if I format it EXT, will it back up the Win7 VM OK?

Hope it's not a dumb question - didn't see a reference to it anywhere else. Thanks!

---

