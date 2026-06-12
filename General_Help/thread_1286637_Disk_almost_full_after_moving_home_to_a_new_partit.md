---
title: "Disk almost full after moving home to a new partition"
date: 2009-10-09
forum: General Help
---

### Post by nick_nik on 2009-10-09
Hi All, 

I've been trying to move my home dir to a new partition using [these instructions]("http://www.psychocats.net/ubuntu/separatehome"). It never worked correctly following them exactly but after a few trys i seem to have everything copied over and my system loads happily to my desktop. 

The only problem being that under the disk partitioner my new home partition seems to be showing more used space than i was expecting. 

using the gnome disk usage anayliser my home dir is about 15 gb however gparted shows the used space at almost twice this?

Can anybody shed some light on this? is my home partition actually this full?

Screenshot attached.

Thanks in advance 

nick

---

### Post by mechro on 2009-10-09
... and your home-backup is mounted on...???

---

### Post by nick_nik on 2009-10-09
home_backup is the original home directory located on /dev/sda1

---

### Post by mechro on 2009-10-09
> **nick_nik said:**
> home_backup is the original home directory located on /dev/sda1

It's just that you say "it never worked correctly" so the mount location might be relevant.

What is the *home-backup* location shown in the folder's properties?

---

### Post by nick_nik on 2009-10-09
i had a few issues when copying the files over as the copied files in the new home were now owned by root, preventing my desktop from loading. I chown'ed the files which resolved the issue. 

screen shot attached of home-backup properties

thanks,


Nick

---

### Post by mechro on 2009-10-09
Hmm. Looks OK.

Daft suggestion but have you checked Trash?

---

### Post by nick_nik on 2009-10-09
trash is empty.

I'M STUMPED :-(

---

### Post by mechro on 2009-10-09
Sorry for delay in getting back to you.

I've run similar scans on my system and GParted is reporting more usage than Disk Usage Analyzer. Admittedly it's not as great a difference as yours but still a quite significant near 2GB for my root partitition  (which contains home).

There's probably some command line magic to give you your true usage but I can't help you there.

---

### Post by CatKiller on 2009-10-09
> **nick_nik said:**
>  using the gnome disk usage anayliser my home dir is about 15 gb however gparted shows the used space at almost twice this?

> **nick_nik said:**
> i had a few issues when copying the files over as the copied files in the new home were now **owned by root**,

Run ```
gksudo baobab
```to run the Disk Usage Analyser as root. Maybe you missed some.

---

### Post by mechro on 2009-10-09
> **CatKiller said:**
> Run ```
gksudo baobab
```to run the Disk Usage Analyser as root. Maybe you missed some.

Hmmm... possibly the way baobab works. My earlier underreported 2GB has now increased to nearer 7GB. I notice that some of my non-default user Folders are not shown when doing gksudo baobab.

---

### Post by nick_nik on 2009-10-10
Problem Solved, 

at some point during one of the failed migration attempts copies of my home folder where saved in /home/.Trash

Deleted all those files and disk usages now as expected. 


Thanks, 


Nick

---

