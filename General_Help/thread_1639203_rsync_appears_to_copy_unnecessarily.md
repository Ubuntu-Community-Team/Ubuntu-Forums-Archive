---
title: "rsync appears to copy unnecessarily"
date: 2010-12-06
forum: General Help
---

### Post by ceperman on 2010-12-06
I'm having to rebuild my home server following a failed upgrade from 8.04 to 10.04 :( .

All data lives in /shared on this server, the contents of which are mirrored weekly to a USB HDD which is mounted at /backup, using rsync:

sudo rsync -av --progress --delete /shared /backup

I recovered the contents of the backup drive to the rebuild server's /shared directory using the cp command with the archive flag set to preserve ownership, timestamps etc. Everything looks fine to me. However, when I do a test rsync (adding -n to the command above) then it looks like rsync wants to recopy everything, and I'm at a loss to see why. 

For example, below is a test on the subdirectory /shared/backgrounds. The file attributes look identical:

```

chris@quadra:~$ ls -la /shared/backgrounds
total 8112
drwxr-xr-x  2 chris chris    4096 2009-04-12 11:06 .
drwxr-xr-x 23 root  root     4096 2010-11-27 15:41 ..
-rwxrw-rw-  1 chris chris  347462 2009-04-04 23:26 alaska-1680x1050.jpg
-rwxr--r--  1 chris chris  605927 2007-03-11 21:47 beach.jpg
-rwxr--r--  1 chris chris 1410922 2007-03-11 21:47 fountain2.jpg
-rwxr--r--  1 chris chris  119913 2007-03-11 21:47 kilchurn.jpg
-rw-r--r--  1 chris chris  931865 2009-04-12 11:06 lighthouse-1680x1050.jpg
-rwxr--r--  1 chris chris 1200139 2007-03-11 21:47 pool.jpg
-rwxr--r--  1 chris chris  592709 2007-03-11 21:47 rockies1.jpg
-rwxr--r--  1 chris chris  609502 2007-03-11 21:47 rockies2.jpg
-rwxr--r--  1 chris chris  932456 2007-03-11 21:47 rockies3-1280x1024.jpg
-rwxr--r--  1 chris chris  323971 2007-03-11 21:47 rockies4.jpg
-rwxr--r--  1 chris chris 1157983 2007-03-11 21:47 rockies5.jpg
chris@quadra:~$ ls -la /backup/backgrounds
total 8112
drwxr-xr-x  2 chris chris    4096 2009-04-12 11:06 .
drwxr-xr-x 22 root  root     4096 2010-11-25 10:49 ..
-rwxrw-rw-  1 chris chris  347462 2009-04-04 23:26 alaska-1680x1050.jpg
-rwxr--r--  1 chris chris  605927 2007-03-11 21:47 beach.jpg
-rwxr--r--  1 chris chris 1410922 2007-03-11 21:47 fountain2.jpg
-rwxr--r--  1 chris chris  119913 2007-03-11 21:47 kilchurn.jpg
-rw-r--r--  1 chris chris  931865 2009-04-12 11:06 lighthouse-1680x1050.jpg
-rwxr--r--  1 chris chris 1200139 2007-03-11 21:47 pool.jpg
-rwxr--r--  1 chris chris  592709 2007-03-11 21:47 rockies1.jpg
-rwxr--r--  1 chris chris  609502 2007-03-11 21:47 rockies2.jpg
-rwxr--r--  1 chris chris  932456 2007-03-11 21:47 rockies3-1280x1024.jpg
-rwxr--r--  1 chris chris  323971 2007-03-11 21:47 rockies4.jpg
-rwxr--r--  1 chris chris 1157983 2007-03-11 21:47 rockies5.jpg
chris@quadra:~$ sudo rsync -navvi --progress /shared/backgrounds /backup/backgrounds
sending incremental file list
delta-transmission disabled for local transfer or --whole-file
cd+++++++++ backgrounds/
>f+++++++++ backgrounds/alaska-1680x1050.jpg
>f+++++++++ backgrounds/beach.jpg
>f+++++++++ backgrounds/fountain2.jpg
>f+++++++++ backgrounds/kilchurn.jpg
>f+++++++++ backgrounds/lighthouse-1680x1050.jpg
>f+++++++++ backgrounds/pool.jpg
>f+++++++++ backgrounds/rockies1.jpg
>f+++++++++ backgrounds/rockies2.jpg
>f+++++++++ backgrounds/rockies3-1280x1024.jpg
>f+++++++++ backgrounds/rockies4.jpg
>f+++++++++ backgrounds/rockies5.jpg
total: matches=0  hash_hits=0  false_alarms=0 data=0

sent 355 bytes  received 49 bytes  808.00 bytes/sec
total size is 8232849  speedup is 20378.34 (DRY RUN)

```
I'm a relative newbie to Linux, but this looks to me like rsync wants to copy the files. On another subdirectory that I let it copy, it now tells me that the files are uptodate.

What am I missing? Is there some condition that rsync can detect that I can't see? Is rsync sensitive to the way the HDD is mounted? (the USB HDD is actually mounted at /media/backup, and /backup is a soft link to this.)

Chris

---

### Post by ceperman on 2010-12-09
I've just been conducting a test with rsync, and maybe I'm misunderstanding what it's supposed to do.

I'd assumed that an archive copy in one direction would synchronise source and target such that they were identical. That is:
```
rsync -a /source /target
```would make source and target identical such that a subsequent archive operation in either direction would copy nothing (assuming no changes of course). This doesn't seem to be the case. If I repeat the above command, it does indeed copy nothing. But if I copy target -> source, rsync wants to recopy everything. Why is this?? This obviously explains the problem I originally posted, but it's not what I expected.

Is this the way rsync is supposed to work, or is it something peculiar to my setup?

Chris

---

### Post by Dave_L on 2010-12-09
I can't answer your question, but I know that some rsync experts are on the rsnapshot discussion list:

[https://lists.sourceforge.net/lists/listinfo/rsnapshot-discuss](https://lists.sourceforge.net/lists/listinfo/rsnapshot-discuss)

---

### Post by ceperman on 2011-02-12
I think I've resolved this, and it's down to not fully understanding how to define the source, specifically the use of a trailing '/'.

My simple example of syncing data:

rsync -a /source /target

was intended to copy the contents of directory /source into the directory /target. In fact it doesn't do this - this command would copy the source directory itself, creating /target/source. The reverse command:

rsync -a /target /source

intended to re-sync (effectively restore) in the opposite direction would in fact again copy the source directory, creating the directory structure /source/target/source. And so on, each time the directory structure is compounded. This obviously isn't what I want.

To avoid copying the source directory itself, and just copying the contents, a trailing '/' is needed:

rsync -a /source/ /target

The reverse sync of this is:

rync -a /target/ /source

This now works as expected - the second command copies nothing if source and target haven't changed. :D

---

