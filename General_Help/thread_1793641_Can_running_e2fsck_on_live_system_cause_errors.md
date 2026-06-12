---
title: "Can running e2fsck on live system cause errors?"
date: 2011-06-29
forum: General Help
---

### Post by 8086 on 2011-06-29
We have an old server running, and I decided to run fsck.ext3 -n on the disk to check it (while it was running). Turns out it reports lots of errors - not a good thing. 

The weird thing is that when booting up a rescue cd and running fsck.ext3 on it, it says there are no problems with it. The filesystem is marked clean. Forcing a check with -f turns up nothing.

Now, when booting it from disk, fsck complains about an unclean file system that has not been checked for like 50000 days (obviously an error). Running e2fsck -n /dev/sda2 turns up errors again - not necessarily the same ones as the last time.

This makes me wonder: 
[LIST=1]
[*]Can running e2fsck on a mounted file system cause errors? I ran with -n which is not supposed to do anything, just doing a read-only check. On the other hand, I heard checking a live file system might throw erros since the files being checked might change while bign checked, thus causing false positives.
[*]Can the old version of e2fstools (1.38, approx 2005) mean non-existing errors are shown? Both the rescue cd and the system use this version.
[*]In any case - why would the file system report errors on boot-up when the rescue cd just said it was ok? It should have been marked clean by now.
[/LIST]

For laughs, I shut down the system and booted Knoppix which has a quite recent version (1.41.12, May 2010) of e2fstools. It showed no errors on the file system.

What do you think - are there errors or not on the file system? This is driving me nuts!

(P.S. The system is actually running Suse, but this is not about Suse specific things - just general Linux tools. And I use Ubuntu personally :p )

---

### Post by psusi on 2011-06-29
Running it with -n can not CAUSE errors, but on a mounted filesystem, it can report errors that are not actually there.

It sounds like your system has a broken real time clock, so it doesn't know what time it is when first booting up, then gets the correct time from the network.  That would explain why it complains about not being checked in 50000 days.

---

### Post by tgalati4 on 2011-06-30
If the server is running OK, then don't worry about it.  If you want to test integrity of the drive, boot from a LiveCD and run badblocks.  If you find some, then run fsck with the -c parameter and it will mark the bad blocks so they won't get used.  Also install smartmontools, then check your drive health:

sudo smartctl -a /dev/sda

Run a short test:

sudo smartctl -t short /dev/sda

Run a long test: (both tests are nondestructive)

sudo smartctl -t long /dev/sda

View the results:

sudo smartctl -a /dev/sda

You should only run fsck on unmounted filesystems.  Since root is mounted on a running server, it's dangerous to run fsck on the boot partition.  So, yes the errors may be due to file changes (such as everything in /proc).

---

### Post by dcstar on 2011-06-30
> **psusi said:**
> Running it with -n can not CAUSE errors, but on a mounted filesystem, it can report errors that are not actually there.
...........

That probably explains the warning message saying exactly that.

---

### Post by 8086 on 2011-06-30
From the man page on e2fsck
*[INDENT]Note that in general it is not safe to run e2fsck on mounted filesystems.The only exception is if the -n option is specified, and -c, -l, or -L options are not specified. However, even if it is safe to do so, the results printed by e2fsck are not valid if the filesystem is mounted.[/INDENT]*

You were right about it not being a good idea to run e2fsck on the root partition of a live system, even if just doing a non-destructive read-only test. 

Old tools might also be part to blame (it is running virtualized - so the internal clock is quite correct) - I suspect the last file system check were set to start of the epoch (Jan 1 1970).

---

