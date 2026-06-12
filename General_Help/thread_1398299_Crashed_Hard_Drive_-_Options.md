---
title: "Crashed Hard Drive - Options?"
date: 2010-02-04
forum: General Help
---

### Post by Gerhardt on 2010-02-04
So the HDD in my wife's ubuntu machine (Lenovo Thinkpad x60 or x61, can't remember) starting going out. It was clicking and still trying to load to the OS but never made it. I took it out, attached it to my Windows 7 desktop and thought maybe I'd be able to pull some data off.

Unfortunately, I believe I made the situation worse as when I went to see if I could assign the disk a drive letter, windows asked me what I wanted to do with this data so it could utilize it. I had two options, and the one I chose was MBR (master boot record I believe). There was no "any data will be lost!" but instantly the drive was seen as unpartitioned space. 

At this point I at least knew to stop. My question is, is there a way to return this build back to ext3 and attempt to salvage anything off of here? My wife was writing a story and is devastated that it is gone. (Yes I know - back things up!).

Any help or suggestion would be greatly appreciated. Thanks.

---

### Post by Ordes on 2010-02-04
mbr is, as you said the boot record, so no files are stored in there.

I dont know what you did exactely, but if you deleted the partition table things might be worse.

Anyways, windows normally cannot read ext3 partitions. So no way to recover your data through windows. Unless you do some hacks in windows to enable it to read ext3.

It might be better to load up a ubuntu live, and try to recover the data through the ubuntu live, instead of windows.

---

### Post by Gerhardt on 2010-02-04
Thanks, that makes sense. But what do I do when I'm in there? I'm guessing the drive is going to show up as unpartitioned or incorrectly partitioned. I.E., yes the table is probably deleted. So what step can I take at that point?

---

### Post by egalvan on 2010-02-04
Questions & clairifcatioins...

you state that you want to *return this build back to ext3*

does this mean it was ext3 to begin with?

What OS was the TP running?


There are drive recovery tools.

TestDisk is a good one...
it can recover entire MBR's, or just the partition tables.
(note, because of journaling, ext3 partitions can be easier to recover than other types. the journal information is not in the MBR.
or partition table, for that matter.)

Photorec is another good one, oriented towards file recovery...
it shines at image files (jpeg, img, gif, png etc)  but works well for any file types.

Download PartedMagic Live CD... it's an excellent mini-distro,
and it has Testdisk and photorec, among others.

Google "partition recovery in linux" to find more information.

Also the testdisk and photorec websites have good info.


Whatever you do, **DO NOT USE THE DRIVE**. Even starting the OS on it will write data, possibly erasing needed data.


The best bet to recover the maximum data is to clone it
mount it 'read-only' and clone it to another drive using 'dd'...
and run any recovery on the cloned drive.
This way the original data is always on the original drive, 
and you can try multiple times.
Reduces the stress levels tremendously.

You may find that buying two new drives, the same size as the 'bad' drive, may be cheaper in the long run...
use one to clone the original, 
and use the second to save any recovered data.

(or AT LEAST a large as the space used on the original drive,
 but the same total capacity may make it easier.
they don't have to be the same type, you can use desktop drives to clone and save data.)

---

### Post by coldraven on 2010-02-04
[I]Egalvan is right.
Testdisc saved my bacon, I even sent the author some money.
But like [/I][I]Egalvan said make a clone first because if you have never used testdisc before you could make matters worse. It is a VERY powerful bit of software.
Maybe best to run PhotoRec first as I think it's mostly automatic. You will end up with lots of directories that contain multitudes of files but hopefully the ones you want will be in there somewhere.
Good Luck!
[/I]

---

