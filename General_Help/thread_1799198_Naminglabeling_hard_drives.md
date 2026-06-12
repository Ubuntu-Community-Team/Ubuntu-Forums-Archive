---
title: "Naming/labeling hard drives"
date: 2011-07-07
forum: General Help
---

### Post by mitk0o0o0 on 2011-07-07
Hello, i'm dual booting windows 7 and ubuntu 10.10 and for torrents it's really annoying how on every boot the hard drives get random names like 0A3FJC03J9CJ3C and i have to re-locate everytime the files.

I was wondering is it possible to name or label them so it can be like in windows C:\ D:\, etc..

I heard it's dangerous, is it?

---

### Post by mitk0o0o0 on 2011-07-07
Or i think they're not randomized but need to be mounted first, is there a way to auto-mount on startup?

---

### Post by Grenage on 2011-07-07
> **mitk0o0o0 said:**
> Or i think they're not randomized but need to be mounted first, is there a way to auto-mount on startup?

There is indeed, and it's relatively easy to do.

First go to a command line and enter this:

```
sudo blkid
```

This will output various info, make a note of the UUID for the partition you are mounting; here's mine:

```
/dev/sda1: UUID="f3d2d07c-f275-4954-bc0e-1c47c000d1e4" TYPE="ext4" 
/dev/sda5: UUID="e6626634-7cc2-4bfe-bc15-5c8c5d6bf721" TYPE="swap"
```

Now you need to make a mount point; anywhere will do, but lets use /media.  Anything in this directory will show up automatically in the Nautilus navigation pane.  I personally use /mnt.

```
sudo mkdir /media/torrent
```

Now add an entry to /etc/fstab; which is the file which controls mounting:

```
gksu gedit /etc/fstab
```

Here's an entry for one of my ext4 partitions:

```
UUID=f3d2d07c-f275-4954-bc0e-1c47c000d1e4  /media/torrent  ext4   defaults  1  2
```

Here is the sort of format you'd use for an ntfs drive (I think)

```
UUID=f3d2d07c-f275-4954-bc0e-1c47c000d1e4  /media/torrent ntfs-3g defaults 0 0
```

You can test your fstab, and check for errors using:

```
sudo mount -a
```

We could have used /dev/sda1 instead of a UUID, but it can be risky.  sd*xx* names are given based on detection order, and on some machines it's not always the same when you turn on the PC.

---

### Post by mitk0o0o0 on 2011-07-07
Thanks alot for the detailed guide, but i'm getting not 2 but 6 of these thingies after the first command:

> /dev/sda1: UUID="78801C1A801BDD86" TYPE="ntfs" 
/dev/sda5: UUID="88D8092BD8091958" TYPE="ntfs" 
/dev/sda6: UUID="ed9878e6-e533-45cb-bd87-b5fc93529f8c" TYPE="ext4" 
/dev/sda7: UUID="fd38045b-0dc3-4094-a081-7c909905bc2a" TYPE="swap" 
/dev/sda8: UUID="770c4dba-0e2d-41d2-9262-ece15eed1f42" TYPE="ext4" 
/dev/sda9: UUID="c45a7119-002c-4aa5-a038-0fc352963f29" TYPE="swap" 

Also is this 100% safe if i screw up?

---

### Post by Grenage on 2011-07-07
> **mitk0o0o0 said:**
> Thanks alot for the detailed guide, but i'm getting not 2 but 6 of these thingies after the first command:



Also is this 100% safe if i screw up?

That's normal, those are all partitions; I imagine it will be one of these two, if it's a partition you can access in Windows:

```
/dev/sda1: UUID="78801C1A801BDD86" TYPE="ntfs"
/dev/sda5: UUID="88D8092BD8091958" TYPE="ntfs"
```

Type this to see which partitions (sda1/sda5/etc) are which:

```
sudo fdisk -l
```

If you are unsure, you can simply mount one as a test, and see if it contains what you expect.  A quick way would be:

```
sudo mkdir /media/test
sudo mount /dev/sda5 /media/test
```

You can then unmount it and remove the test directory with:

```
sudo umount /dev/sda5
sudo rmdir /media/test
```

You can then look in /media/test and check that it contains the files, and that it's the right partition.  It should show up in Nautilus once mounted.

You can't do any harm by adding the wrong drive to fstab - you're not writing to the partitions.

---

### Post by mitk0o0o0 on 2011-07-07
The test command doesn't seem to work, this is very confusing. :o

> mitko@mitko-MS-7309:~$ sudo mount dev/sda5 /media/torrents
[sudo] password for mitko: 
mount: special device dev/sda5 does not exist
mitko@mitko-MS-7309:~$ sudo mount dev/sda6 /media/torrents
mount: special device dev/sda6 does not exist


EDIT: Nevermind, i missed the slash at the beginning.

It seems to have mounted it, was that all?

Thanks!! :D

---

### Post by Grenage on 2011-07-07
Go Linux terminal warrior! :)

That's good; now open Nautilus (file manager), and browse to /media/torrent, or look for it listed in the left panel of Nautilus.  Make sure that the files in there are the files you expect to see; if they aren't, then it's probably not the partition you want.

If it is, then you simply need to add the entry to /etc/fstab, as described in my first post.  If you don't add it to fstab, it won't be mounted automatically when you restart the machine.

---

### Post by mitk0o0o0 on 2011-07-07
It's the files that i wanted, thank you so much.

But last question, i'm a little scared right now.

The partition i just mounted there, is where ubuntu is installed and so what if i can't boot anymore? Is it safe to turn off my computer or i should immediately undo these changes?

Cause now i see on Transmission that it can't find those files, it appears i'll need to re-locate them to /media/torrents

What about the boot, is it safe?

Also i have a seperate partition thingy called "File System" so i guess it's safe?

EDIT: Sorry for all the questions but another thing, every file and folder i try to delete, a popup shows up saying "This item can't be moved to trash" and that it will just permanently delete it. o.O

---

### Post by Grenage on 2011-07-07
> **mitk0o0o0 said:**
> It's the files that i wanted, thank you so much.

But last question, i'm a little scared right now.

The partition i just mounted there, is where ubuntu is installed and so what if i can't boot anymore? Is it safe to turn off my computer or i should immediately undo these changes?

Cause now i see on Transmission that it can't find those files, it appears i'll need to re-locate them to /media/torrents

What about the boot, is it safe?

Also i have a seperate partition thingy called "File System" so i guess it's safe?

Don't worry too much, you can't destroy your system by mounting a partition.  I should probably explain how mounts work, just to clear it up.

In Windows you see C: or D: as partitions, and that's about all you see.  In Linux, you create what are called mount points, which are basically just directories/folders.  When you mount a partition to a directory, it's not petting the data *in* that directory; think of a mount point as a window to another partition - a portal to make it accessible.

When you mount or unmount a partition, you're just opening or closing that window; any data you add is put on whatever partition is mounted there.  I apologise if my analogy is childish or simplistic, but it's the best way I can describe it, lol.

You can reboot without fear, but remember that you'll need to mount the partition again unless you add it to /etc/fstab.  Anything in /etc/fstab will be automatically mounted when you turn on the machine.

---

### Post by mitk0o0o0 on 2011-07-07
Thank you very much for everything, this eased up my life a lot.

Last question, really sorry for so many questions:
Every file and folder i try to delete on the partition i mounted, a popup shows up saying "This  item can't be moved to trash" and that it will just permanently delete  it. o.O

But on the other one that i didn't touch, it deletes normal.

---

### Post by Grenage on 2011-07-07
> **mitk0o0o0 said:**
> EDIT: Sorry for all the questions but another thing, every file and folder i try to delete, a popup shows up saying "This item can't be moved to trash" and that it will just permanently delete it. o.O

No apology necessary, questions are good.

I imagine that because the partition you've mounted is an NTFS (Windows) partition, there's no ext (Linux) trash directory.  I would have thought that these days Ubuntu could handle a Windows recycle bin, but obviously not.  It's probably more complicated than it seems.

On any ext (Linux) partitions, when you delete a file, it will get put in the trash directory.

---

### Post by mitk0o0o0 on 2011-07-07
I heard it has something to do with this "UID" but how do i know what it is for my second ntfs partition as i get so much when i type that command to list them.

---

### Post by Grenage on 2011-07-07
> **mitk0o0o0 said:**
> I heard it has something to do with this "UID" but how do i know what it is for my second ntfs partition as i get so much when i type that command to list them.

Do you want to mount the second ntfs partition?

---

### Post by mitk0o0o0 on 2011-07-07
> **Grenage said:**
> Do you want to mount the second ntfs partition?Yes, the one that i want mounted for torrents is the second one.

But on your first reply to my thread the UID you showed me looks a lot different than the ones shown on my ntfs drives.

---

### Post by Grenage on 2011-07-07
> **mitk0o0o0 said:**
> Yes, the one that i want mounted for torrents is the second one.

But on your first reply to my thread the UID you showed me looks a lot different than the ones shown on my ntfs drives.

It's quite likely that the UUID will vary depending on the utility used to partition them.  Your first two are ntfs partitions, and were likely created by windows.  Either way, sorry not; you can use whatever is listed as the UUID, even if it looks a little different.

---

### Post by mitk0o0o0 on 2011-07-07
Wow not only that but i can't open up txt files directly.

I'll try that, thanks. Gonna let you know.

---

### Post by mitk0o0o0 on 2011-07-08
It's all good now, thank you very much for the help.

---

### Post by Grenage on 2011-07-08
Wonderful; good job!

---

### Post by ssreddy555 on 2011-07-08
Can't the labeling be done more simply with gparted? One can simply type in whatever label one wants on right clicking the partition & choosing "Label"?

Or have I wrongly understood your question?

Following is my configuration:


/dev/sda1: LABEL="System Reserved" UUID="6EE26202E261CEC1" TYPE="ntfs" 
/dev/sda2: LABEL="Windows 7" UUID="8EBE0A93BE0A73CD" TYPE="ntfs" 
/dev/sda5: LABEL="Ubuntu" UUID="fa056c87-b266-4661-8eb6-daed330d3090" TYPE="ext4" 
/dev/sda6: UUID="8e2bf3c9-f8d6-48c2-9e36-7c49c4fbdeda" TYPE="swap" 
/dev/sda7: UUID="6fd09d42-bc9a-40b7-94e4-bfb137fe7fd3" TYPE="ext4" 
/dev/sda8: UUID="a284a4b1-6831-49d0-8e5a-9bdcb0a339fb" TYPE="swap" 
/dev/sda9: LABEL="Mint 64" UUID="c3151866-7e73-48df-aa82-ef7c34e6b0b5" TYPE="ext2" 


sda7 could not be labelled for the time being because that partition is mounted & i'm working from it. I can do it any time by mounting another partition.

---

