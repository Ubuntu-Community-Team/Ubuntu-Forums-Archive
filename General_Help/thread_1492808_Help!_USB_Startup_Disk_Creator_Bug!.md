---
title: "Help! USB Startup Disk Creator Bug!"
date: 2010-05-25
forum: General Help
---

### Post by russki_drewski on 2010-05-25
So, here is my problem:

I have an external hard drive that I had partitioned into 3 parts: 2gb for ubuntu livecd, 2 gb for clonezilla, and the rest for backup. I was going to install the new Lucid on a computer for a friend, but on my hard drive I had the karmic livecd installed. So I opened the USB Creator, selected my Lucid iso, selected the partition I wanted to use and told it to format THAT partition so I could install the iso onto fresh. 

...

It formatted and repartitioned the entire hard drive! My 3 partitions are now one and it shows that the disk is totally empty!
I know all the information that I had has to still be on there. The whole process only took like 10 seconds, and so theoretically it didn't erase everything, just the file system ... right?

How can I recover my information?!

Any and all help appreciated!


russki_drewski


Karmic
Acer AO 751h
Atom 1.3 ghz, 2gb RAM, 250gb HD

---

### Post by John Bean on 2010-05-25
It's not a bug, although it can catch you out as you found. You can't "tell it" to format a partition as you claim to have done - the button is clearly marked "Erase **disk**" and it does just what it says.

As to recovery: I'd use testdisk, it will probably be able to recover the partition table for you. Read the documentation before using... and don't assume it means something other than what's written ;-)

---

### Post by russki_drewski on 2010-05-25
Well, actually the utility doesn't say "Erase Disk", but rather it it has a button that says "Format". Maybe in Lucid they changed it? I'm still on Karmic for now.

---

### Post by John Bean on 2010-05-25
> **russki_drewski said:**
> Well, actually the utility doesn't say "Erase Disk", but rather it it has a button that says "Format". Maybe in Lucid they changed it? I'm still on Karmic for now.

Sounds likely that they changed it to avoid confusion; it's intended to be a "quick fix" primarily for flash drives and the like, it's not a bug as such since it does what the programmer intended it to do. 

Anyway, testdisk should be able to undo the deleted partition table for you and the data will be intact if you haven't written anything to the disk.

---

### Post by russki_drewski on 2010-05-25
Okay, well I guess its a false alarm for the bug. Thanks for the response. I think I've found a wiki that will walk me through using testdisk. It'd be really nice if everything showed back up without having to use another program like photorec that I just read about.

I'll post my results once I've got it done.

---

