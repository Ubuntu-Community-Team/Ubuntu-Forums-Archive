---
title: "Span DVD - backup software?"
date: 2012-05-18
forum: General Help
---

### Post by fisheater on 2012-05-18
Hi,

I have 100GB of photos I would like to back up on to DVD for remote (safety deposit box) backup.

I looked into brasero, but the documentation is lean. I searched online and the forums with not much luck.

Anyone have success with this? Suggested software +/- link to guide.

TY

FE

P.S. looking for an alternative to using any HD

---

### Post by PhantomTurtle on 2012-05-18
This is a bit old now, but it should work - [http://ocaoimh.ie/2009/12/16/fill-span-dvd-archives-discspan/]("http://ocaoimh.ie/2009/12/16/fill-span-dvd-archives-discspan/"). (I haven't tried it though). Brasero is supposed to have this, but I hear that it doesn't work. I can't test this because the only things I burn to CD's and DVD's are for live CD's of Linux Distributions (I have lots).

---

### Post by ubaddn on 2013-02-26
this is very important question because of
the looming threat of EMP attack
(electromagnetic pulse from mile-high nuclear explosion
or galactic core ejection);
all magnetic storage devices are vulnerable;
so, important backups should also be on optical media .

[year 2007 suggests AMANDA or dar:]("http://ubuntu-tutorials.com/2007/01/10/backing-up-media-to-multiple-dvds-ubuntu/")
. says all the "big shops" use AMANDA .

[AMANDA (Advanced Maryland Automatic Network Disk Archiver):]("http://www.amanda.org/docs/README.txt")
* Linux Journal Readers' Choice Award *
. back up multiple hosts over network
to tape drives/changers or disks
or optical media.
Amanda uses native utilities and formats
(e.g. dump and/or GNU tar)
and can back up a large number of servers and workstations
running multiple versions of Linux or Unix.
Span tapes, i.e. if a single backup is too large for one tape,
Amanda will split it and put the pieces on
multiple tapes automatically.
. forums .
[forums.zmanda.com]("http://forums.zmanda.com")

dar is a shell command:
[dar.linux.free.fr/]("http://dar.linux.free.fr/")
that backs up directory trees and files, taking care of
hard links, Extended Attributes, sparse files, MacOS's file forks,
any inode type (including Solaris Door inodes), etc.
It has been tested under Linux, Windows, Solaris, FreeBSD, NetBSD, MacOS X
and several other systems,
. you need is dar [1]. It’s a command line archiving tool
that you can use to archive your entire system, your homedir, or any folder.
It can compress the archive,
and it can split it into slices of whatever size you want.
So if you were burning to CDs
you met set the slice size to 600MB.
Dar would split the archive into however many 600MB files as necessary.
What’s more, dar can pause after producing each slice,
so that you can burn the slice to a CD
then delete it (or do anything you else you like)
before telling dar to continue.
This means you only have to have 600MB of free space on your disk,
even if your total archive is much bigger.

[kdar is a gui for dar]("http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html") .

[lxsplit is used after a compress or tar]("http://babeyudi.wordpress.com/2010/09/07/how-split-and-join-file-with-lxsplit-in-ubuntu/") .

. if anyone is coming from Windows 7zip,
[it is working within Wine]("http://ubuntuforums.org/showthread.php?t=782897&page=3") .

---

### Post by scdbackup on 2013-02-27
Especially intended for the given task is scdbackup:
[http://scdbackup.webframe.org/main_eng.html](http://scdbackup.webframe.org/main_eng.html)

Configuration demands some thought. But usage is easily 
repeatable or scriptable:
[http://scdbackup.webframe.org/examples.html](http://scdbackup.webframe.org/examples.html)

scdbackup is a collection of C programs and shell scripts
for GNU/Linux and other Unix-like systems. It produces 
several independently usable CD, DVD, or BD volumes in 
ISO 9660 format which can be read by about any current 
operating system. Each volume contains a MD5 checksum
by which the scdbackup_verify script can test the write
success and storage integrity.

Support for scdbackup and burn backend xorriso:
[email]scdbackup@gmx.net[/email]

---

### Post by fanum2 on 2014-02-13
Huge fan of this solution! I have been looking for a couple years for something like this. Is there a reason there is no .deb for Ubuntu, or even a PPA? Is there any reason we couldn't make one (of either)? 

I would like to make it easier for non-tech savvy people to install. 

Thanks again, this is a life saver. 

> **scdbackup said:**
> Especially intended for the given task is scdbackup:
[http://scdbackup.webframe.org/main_eng.html](http://scdbackup.webframe.org/main_eng.html)

Configuration demands some thought. But usage is easily 
repeatable or scriptable:
[http://scdbackup.webframe.org/examples.html](http://scdbackup.webframe.org/examples.html)

scdbackup is a collection of C programs and shell scripts
for GNU/Linux and other Unix-like systems. It produces 
several independently usable CD, DVD, or BD volumes in 
ISO 9660 format which can be read by about any current 
operating system. Each volume contains a MD5 checksum
by which the scdbackup_verify script can test the write
success and storage integrity.

Support for scdbackup and burn backend xorriso:
[EMAIL="scdbackup@gmx.net"]scdbackup@gmx.net[/EMAIL]

---

