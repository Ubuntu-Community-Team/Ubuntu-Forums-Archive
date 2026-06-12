---
title: "Trying to recover a partition with TestDisk"
date: 2011-11-27
forum: General Help
---

### Post by Mosto on 2011-11-27
Hi, i'm trying to recover a partition with TestDisk. It's on a 500 GB hard drive which has 3 partitions, the big one, a 100 MB partition, and the HP recovery partition.

I've done a deep search and this is what it finds.

[img]http://img825.imageshack.us/img825/2696/12752499.png[/img]

I think the data is on partition 3, but when I try to open it gives me this message, "Can't open filesystem. Filesystem seems damaged".

I can open partition 2 but it's empty. Seeing the numbers it seems that the partition 3 has an incorrect start and end, but I'm not sure how can I solve this.

Anyone knows?

Regards.

---

### Post by sudodus on 2011-11-27
Welcome to the Ubuntu Forums

There is also gpart [http://www.brzitwa.de/mb/gpart/](http://www.brzitwa.de/mb/gpart/)
that can guess in an intelligent way what a damaged partition table should look like. Try that one too!

Please describe some more details about your hard drive, what happened (or what you think happened! That makes it easier for us to help.

A final step would be to use PhotoRec to recover your files from the damaged drive. This works as long as the file data are still there (that the files are not overwritten). I can work without any partition table. But it does not recover the file names and no directory structure, so there will be a lot of organizing work.

Good luck :-)

---

### Post by ottosykora on 2011-11-27
looks like one of those HP setup.

The first looks ok (primary bootable), the last too.

Then select the second partition, it is now D (deletd) then go and try to reset it so it becomes again P. Select it and the -change and follow the instruction.
This will be the main windows partition then and all might boot then.

The 3rd is also marked now D but this could be the TOOL partition which is not so much important. But could be recovered then later.

---

### Post by Mosto on 2011-11-27
> **sudodus said:**
> There is also gpart [http://www.brzitwa.de/mb/gpart/](http://www.brzitwa.de/mb/gpart/)
that can guess in an intelligent way what a damaged partition table should look like. Try that one too!

Please describe some more details about your hard drive, what happened (or what you think happened! That makes it easier for us to help.

A final step would be to use PhotoRec to recover your files from the damaged drive. This works as long as the file data are still there (that the files are not overwritten). I can work without any partition table. But it does not recover the file names and no directory structure, so there will be a lot of organizing work.

Thanks sudodus, i'll try also with gpart :)

The problem started after a power outage when Windows 7 was starting.

I've tried PhotoRec and seems to recover the files, but before using it I want to try to recover the partition as it was.

> **ottosykora said:**
> looks like one of those HP setup.

Thanks for the response ottosykora :)

It is a hard drive from a HP computer. It comes with 3 partitions, but I don't know why they are appearing 4 in the results.

The partition 2 shows the entire partition space, 465 GB, but when I access to it appears empty. The partition 3 has 385 GB occupied, so I think this is the partition that it has the data, but I can't access to it.

---

### Post by sudodus on 2011-11-27
Another option is to attach your hard drive to a(nother) Windows computer and let Windows try to repair the drive. Sometimes after a power failure, it is enough with a simple chkdsk command from dosprompt (the Windows terminal window)
```
chkdsk [COLOR=SeaGreen]G:[/COLOR] /r
``` where [COLOR=SeaGreen]G:[/COLOR] is the volume ID, and should be adjusted to fit each of the partitions on your hard drive.

---

### Post by Mosto on 2011-11-27
Thanks sudodus, I'll try :)

---

### Post by ottosykora on 2011-11-29
the factory image might be hidden, no problem with that, only under windows itself it is not appearing, but this can be done with every partition.

---

