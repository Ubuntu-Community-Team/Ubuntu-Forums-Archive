---
title: "Can't boot up using Ubuntu..PLEASE HELP!"
date: 2009-08-05
forum: General Help
---

### Post by Saltwaterfishin on 2009-08-05
Hi all,

While trying to boot up last night, I got the following message:

Checking Root File System
136
FSCK 1.41.4 (27-Jan-2009)

/lib/init/rw/rootdev contains a file system with errors, check forced
/lib/init/rw/roodtdv: Inodes that were part of a corrupted orphan linked list found
lib/init/rw/rootdev: unexpected inconsistancy;run fsck manually (ie; without -a or -p options)
fsck died with exit status 4

When the computer went into "safe" mode, I typed in fsck, then ctrl d to exit and reboot.  I got the same message.

Can anyone help me figure out what is going on and how to fix it?  I can't boot up my computer with Ubuntu on it.  I think I'm using Jaunty Jackalope since I've done all the updates.  I'm using my old computer with windows on it to post this.

Thanks,

Jay

---

### Post by merlinus on 2009-08-05
You need to specify your root partition, e.g. fsck /dev/sda1

---

### Post by gldearman on 2009-08-05
I'm no expert, but that's bad.

Is your filesystem ext3?

What output did you get when you ran fsck?  Did you specify what drive/partition you were running on, eg:

```
# fsck /dev/sda2
```

It's better to run fsck on an unmounted partition, so make sure you unmount your root partition before you try this.  I'd run from a LiveCD, myself.

Do you have a separate /home partition?  If you do, your data should be safe, even if your installation is unrepairable.

---

### Post by Saltwaterfishin on 2009-08-05
Hi Merlin,

I typed what you said and here's the results:

fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda1:clean 128026/4792320 files 1126055/19161520 blocks

Still can't boot up.

---

### Post by merlinus on 2009-08-05
Are you sure that sda1 is your root partition?  You can probably find out by running from the live cd, open a terminal, and post results of

```
sudo fdisk -l
```

Since you cannot get to the login screen, your partition is not mounted, so not to worry about that.

---

### Post by Saltwaterfishin on 2009-08-05
Yippee, Yahoo....hey Merlin,

You gave me an idea and I typed in fsck /lib/init/rw/rootdev

that seemed to work...the program automatically found the errors and asked me if I wanted to fix them...there were about 8 or 10 times I typed "Y" when asked if I wanted to fix the errors.

Yippee, Yahoo....it booted up.

Thanks everyone who tried to help

---

