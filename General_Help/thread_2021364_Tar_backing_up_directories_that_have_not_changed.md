---
title: "Tar backing up directories that have not changed"
date: 2012-07-09
forum: General Help
---

### Post by Azdour on 2012-07-09
Hi,

We've been using tar for several years to make a full backup on Monday and an incremental one on the other days.

Last week we moved from Ubuntu 10.04 to Xubuntu 12.04 and we are using the same tar script.

On Monday 2nd July it did the full backup making the snapshot like usual.

On Tuesday 3rd July it looked like it had done a full backup again. Looking in the log file it produces I saw:

tar: /home: Directory has been renamed

I know /home has not been renamed.

On Wednesday and Thursday it did an incremental backup with only the changed files.

On Friday 6th July once more the log file said:

tar: /home: Directory has been renamed

I've run stat on /home:

```

File: `/home'
  Size: 4096      	Blocks: 8          IO Block: 4096   directory
Device: 801h/2049d	Inode: 17301505    Links: 21
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2012-07-07 23:00:01.850233832 +0100
Modify: 2012-05-31 15:55:18.000000000 +0100
Change: 2012-06-28 12:04:34.117972675 +0100
 Birth: -

```

If the directory had been renamed then the modify date or change date should be in July.

Going through the output logs I also found a lot of these for lots of directories that I know have not been renamed:

```

Verify /home/fred/.barry
tar: /home/fred/.barry/: Cannot savedir: Not a directory
tar: /home/fred/.barry: Directory has been renamed

```

Any help would be great.

---

### Post by matt_symes on 2012-07-09
Hi

Take a look at this..

[http://www.mail-archive.com/bug-tar@gnu.org/msg03359.html](http://www.mail-archive.com/bug-tar@gnu.org/msg03359.html)

Kind regards

---

### Post by Azdour on 2012-07-09
Hi,

Thanks, that may answer the verify failure messages - I did check in the backup file and they are there which is good. I first thought it was missing them.

I think it still does not shed any light on why an incremental tar would see /home as renamed when it has not.

---

### Post by matt_symes on 2012-07-09
Hi

> **Azdour said:**
> Hi,

Thanks, that may answer the verify failure messages - I did check in the backup file and they are there which is good. I first thought it was missing them.

I think it still does not shed any light on why an incremental tar would see /home as renamed when it has not.

Maybe the two are related... but i don't know.

Kind regards

---

### Post by Azdour on 2012-07-11
Hi,

I'm beginning to think there is either a bug in tar or the filesystem on the machine is messed up.

Yesterdays backup log includes this:

```

Verify /home/store/Development/
tar: /home/store/Development/: Cannot savedir: Not a directory
tar: /home/store/Development: Directory has been renamed from `/home/fred/.java/deployment/cache/6.0/25'

```

I know that the directory has not been renamed and that both:

/home/fred/.java/deployment/cache/6.0/25

and 

/home/store/Development/

exist. I do not know why it believes that /home/fred/.java/deployment/cache/6.0/25 was renamed to /home/store/Development/

In fact in the log there are lots of directories it thinks have been renamed from /home/fred/.java/deployment/cache/6.0/25.

I've checked the inode values for them and they are different.

What ever tar does to compare/check if a directory has been renamed is broken.

We do not have the files from the old machine we moved from but checking on another Ubuntu 10.04 that version of tar is different to Xubuntu 12.04:

10.04: v1.22
12.04: v1.26

---

### Post by Azdour on 2012-07-11
Hi,

I've downloaded the source for tar 1.22 and built it.

After fixing the buffer overflow error because of using a newer gcc ([http://lists.gnu.org/archive/html/bug-tar/2010-04/msg00023.html](http://lists.gnu.org/archive/html/bug-tar/2010-04/msg00023.html)) it seems to be working.

I have now altered my backup script to use this tar instead and I will report back the results.

---

### Post by matt_symes on 2012-07-11
Hi

> I have now altered my backup script to use this tar instead and I will report back the results.

Please do. I am very interested.

Kind regards

---

### Post by Azdour on 2012-07-18
Hi,

Ok, so I've been using tar 1.22 instead of 1.26 for the last seven days without a repeat of the problem.

So it looks like tar 1.26 or a version down to 1.22 has a bug in it that does not perform incremental backups correctly because it thinks directories have been renamed when they have not.

---

