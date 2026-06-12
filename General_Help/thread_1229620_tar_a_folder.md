---
title: "tar a folder"
date: 2009-08-02
forum: General Help
---

### Post by toleolu on 2009-08-02
Totally noob question here I know but I just want to make sure I understand what I read.

I have a folder called NewFG that contains everything for my Flight Gear program. 

If I tar -czf /NewFg and then somewhere down the road, I totally jack up that program, I can extract the tar file I created and be back in business??

I understand that I will loose any changes made since the tar file was created, but will the program still run the way it did when I created the tar file??

Thanks

---

### Post by Rob_H on 2009-08-02
Sure, tar can be used to make a backup of a directory,

---

### Post by toleolu on 2009-08-02
Thanks, just wanted to make sure that's how it works.

---

### Post by jms1989 on 2009-08-02
I believe you'll want tar -pczf file.tar.gz /dir/.

Keep in mind, it will archive any parent folders up to the point you want to archive and then any folders or files following your source location.

---

### Post by toleolu on 2009-08-02
OK, well the main thing I wanted to make sure of is that the program would still run. I'm a bit of a Linux noob (SHOCKER!!!!)

Thanks, at some point I'll need to backup the whole install, but for something like that I probably need to use rsync or something like that, is that right??

---

### Post by Rob_H on 2009-08-02
> **toleolu said:**
> Thanks, at some point I'll need to backup the whole install, but for something like that I probably need to use rsync or something like that, is that right??

As the name implies, rsync is good for synchronizing directory contents across a network. And some people do use it directly for backups, although it is a pretty low-level tool. Personally, I use and recommend a tool called [BackupPC]("http://backuppc.sourceforge.net/") for automatic backups to a server. It uses rsync under the hood.

---

