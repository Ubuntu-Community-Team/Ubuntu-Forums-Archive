---
title: "How to separate ~/ settings and other ~/ files"
date: 2011-07-12
forum: General Help
---

### Post by JedMeister on 2011-07-12
I'm not even sure if this is reasonably possible or not but here goes...

What I would like to try and achieve is to have the user's settings (usually contained in hidden folders in ~/ ie folders starting with '.') separated from the rest of the users files and folders.

So basically I want the settings on the system drive (or a separate partition) and the rest of the user's files and folders somewhere else.

I'd like this for a netbook with a very small SSD. That way the bulk of the user's documents could be on an SD card but without any real performance hit for general use (the SD card has much slower access than the SSD so SD load times won't affect general use).

This could also be useful for users accessing their home folder via NFS over a high latency network.

Initially I thought it could somehow be done with UnionFS, which I still think it could but I can't find any info on a use case like this (usually in the case of an SSD it's used to squash /usr to free up space).

Does anyone have any bright ideas?

---

### Post by oldfred on 2011-07-12
This is exactly what I do & recommend, although some others do not suggest a separate /data partition. Often for multi-boot systems so you can have the same data in different systems. But you can do it with just one system also.

Lots of info. If you want specifics they mostly are in my links.
I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Shared /data -see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
With upstart script 
[http://ubuntuforums.org/showthread.php?t=1771773&page=5](http://ubuntuforums.org/showthread.php?t=1771773&page=5)


Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data older but still relavent
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Link XP my docs
[http://www.techsupportalert.com/how_to_move_my_documents.htm](http://www.techsupportalert.com/how_to_move_my_documents.htm)

---

### Post by JedMeister on 2011-07-12
Thank you so much. That is exactly the info I was after! Obviously using the wrong search terms. Thanks for heading me in the right direction. :)

---

### Post by Lars Noodén on 2011-07-13
You can mount the /home partition on the removable SD, or just mount it as /data.

---

