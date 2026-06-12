---
title: "Change Ownership of External USB HDD"
date: 2010-11-16
forum: General Help
---

### Post by DeadlyOats on 2010-11-16
I bought a brand new 2TB external USB HDD.  Using gparted, I deleted the ntfs partition, and created a new partition formatted in ext4.

Then, I tried to write files to it.  I couldn't because root *stole* my HDD from me!  Blast him!

How do I change ownership of the drive so that *I* own it and _NOT_ root? (blasted thief!)

I saw a lot of chmod and chown threads, but they all dealt with files and directories.  I want to own the external drive, itself, and all of its contents (when I am finally able to add contents to it).

Thanks.

---

### Post by nothingspecial on 2010-11-16
> **DeadlyOats said:**
> I bought a brand new 2TB external USB HDD.  Using gparted, I deleted the ntfs partition, and created a new partition formatted in ext4.

Then, I tried to write files to it.  I couldn't because root *stole* my HDD from me!  Blast him!

How do I change ownership of the drive so that *I* own it and _NOT_ root? (blasted thief!)

I saw a lot of chmod and chown threads, but they all dealt with files and directories.  I want to own the external drive, itself, and all of its contents (when I am finally able to add contents to it).

Thanks.

Imagining it is mounted /media/drive........

....... and your username is deadlyoats

```
sudo chown -R deadlyoats:deadlyoats /media/drive
```

Change the imagined stuff to the real thing.

---

### Post by DeadlyOats on 2010-11-16
Thank you, nothingspecial!

Thanks for recognising that I am a simple end user and for your very simple explanation.

Please know that I will always refer to this thread, when I need to do something like this again, in the future.

I think I see a pattern.  It doesn't matter if it's a file name, a folder name, or the name of a drive.  It's all done the same way.

For example:

[COLOR="Red"]sudo chown -R deadlyoats:deadlyoats /media/myharddrive'sname[/COLOR]  This changed the owner of the drive.

While this:

[COLOR="Red"]sudo chown -R deadlyoats:deadlyoats /home/folder/subfolder[/COLOR]  This changed the owner of the directory (folder or subfolder).

And this:

[COLOR="Red"]sudo chown -R deadlyoats:deadlyoats /home/folder/subfolder/file[/COLOR]  This changed the owner of the file within a directory.

1) It's the same command structure.  It's just the path that changes.  Or am I mistaken?

2) If the owner of a drive or directory is changed, does that necessarily change the ownership of the contents too?

3) Also, why "deadlyoats:deadlyoats"?  Why is it repeated like that?

The command you showed me gave me ownership of the drive, but to give myself permission to write to the drive, I right clicked the drive, clicked on properties, clicked on the "Permissions" tab, and changed the "Group" permissions from "Access Files" to "Create and Delete Files".  That permitted me to start copying files to the drive.

---

### Post by matt_symes on 2010-11-16
Hi

To answer your questions.

1. Yes the pattern is the same (although with the drive it is the mount point that changes ownership)
2. No it does not
3. User and group

Kind regards

---

### Post by DeadlyOats on 2010-11-16
Many thanks, matt_symes!

So, then, with the command, as shown above, I am able to change one directory(folder/subfolder) at a time, and within those folders, I can change ownership of the files, one at a time.

How do I change the ownership of all files and folders within a directory or drive with one command (If you don't mind my asking)?

---

### Post by matt_symes on 2010-11-16
Hi

There are a couple of ways to do it.

**But first a word of warning**

You _must_ be sure you are doing it correctly and _only_ to the files you want.
Changing ownership of the files in many system directories will put you in a whole world of pain as many programs and the system itself rely on files having certain permissions and ownerships.
I am not try to be patronising, i just _really_ dont want you to make a mistake or you will be looking at reinstalling.

Anyhow, warning over.

Read this thread. It will save me alot of typing

[http://www.linuxquestions.org/questions/ubuntu-63/sudo-chown-operation-not-permited-543589/](http://www.linuxquestions.org/questions/ubuntu-63/sudo-chown-operation-not-permited-543589/)

Kind regards

---

### Post by DeadlyOats on 2010-11-16
Thanks again, matt_symes!

I read the posts at the link you provided.  It seems then the [COLOR="Red"]-R[/COLOR] is what is needed to change ownership of multiple folders and files within a specific directory, and that was already in the command that nothingspecial taught me (sudo chown [COLOR="Red"]-R[/COLOR] deadlyoats:deadlyoats ...), but correct me if I am mistaken.

Thanks for your advice and teachings.

---

### Post by Verbeck on 2010-11-16
try the manual entry for chown 
```
man chown
```

---

### Post by matt_symes on 2010-11-16
Hi

> **DeadlyOats said:**
> Thanks again, matt_symes!

I read the posts at the link you provided.  It seems then the [COLOR=Red]-R[/COLOR] is what is needed to change ownership of multiple folders and files within a specific directory, and that was already in the command that nothingspecial taught me (sudo chown [COLOR=Red]-R[/COLOR] deadlyoats:deadlyoats ...), but correct me if I am mistaken.

Thanks for your advice and teachings.

Yeah, missed that -R switch. My only excuse is it very late here. Glad its fixed :)

Kind Regards

---

