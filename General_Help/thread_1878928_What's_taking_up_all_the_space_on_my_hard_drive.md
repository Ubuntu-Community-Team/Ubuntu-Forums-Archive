---
title: "What's taking up all the space on my hard drive?"
date: 2011-11-10
forum: General Help
---

### Post by the_Baffler on 2011-11-10
Ubuntu noob here.  Running Ubuntu 11.10 Desktop.
I've searched and found others with similar problems but nothing has led me to an answer.

Ubuntu has started telling me I'm running out of room on my drive where the OS is installed.

A pictures worth a thousand words right?
Here's a few that may (or may not) be useful.
[IMG]http://img804.imageshack.us/img804/1102/screenshot20111110at315.png[/IMG]
[IMG]http://img444.imageshack.us/img444/7917/screenshot20111110at334.png[/IMG]
(Disk Usage Analyzer in the above screenshot was launched using the `gksu baobab` command.)  This Disk Usage Analyzer ^^ shows the size of "home" as 917.7.  This is incorrect; it doubles the size because it counts the .ecryptfs *and* johnny (me, my USER directory) directories which are really the same content.  And subsequently none of the Usage percentages make sense.

What really doesn't make sense is this:
The size of .Private is shown as 458.8GB.
The files/directories listed inside of .Private do not add up to anywhere close to 458.8GB.

Any ideas? 
Is the space actually in use or just being reported incorrectly?
It's actually impacting my use as I can't download large files.  The system complains that there isn't enough space on the drive.

Thanks.

---

### Post by Gremlinzzz on 2011-11-10
Guess its being reported wrong:popcorn:
did you try cleaning with bleachbit its in software manager.

---

