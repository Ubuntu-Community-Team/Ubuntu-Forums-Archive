---
title: "help deleting encrypted luks drive"
date: 2010-03-17
forum: General Help
---

### Post by UnMeilleurReve on 2010-03-17
So I encrypted my secondary solid state drive with LUKS encryption and must have magickally entered the password wrong twice, perfectly. I want to simply erase and format the drive with a fat32 or somesuch, but the partition states that it is a protected partition with magic.

Can anybody give me a simple runthrough on how to delete and format this drive? There's nothing on it, so I don't mind destroying it, but I can't find anything on how to go about doing this. I'm a bit of a newb, so if you give me code that has to be input any way other than terminal, please be specific on how to go about it. Thanks!

---

### Post by quixote on 2010-03-19
What have you tried?  Is it the Gnome Partition Editor that is giving you that message about magic?  Something else?

fdisk is an old command line way of formatting drives that probably will just ignore whatever is on there.  Type "man fdisk" (no quotes) in a terminal to see what's involved.  You have to be very careful with device names and partitions or you can find yourself reformatting the wrong drive!  Also, search using "fdisk" "solid state drives" and possibly your particular drive model, and see what comes up.  It's an ancient program, and it may not handle SSDs well or at all.

---

