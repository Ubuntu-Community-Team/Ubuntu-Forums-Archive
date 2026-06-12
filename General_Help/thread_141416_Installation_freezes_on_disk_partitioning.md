---
title: "Installation freezes on disk partitioning"
date: 2006-03-08
forum: General Help
---

### Post by treuss on 2006-03-08
Hi,
after purchasing two new sata disks, I wanted to re-install breezy onto a big new partition, but unfortunately cannot get past the partitioning state. What happens:[list][*]Last message I see is "Starting up the partioner", after that there is a blue screen (could it have any other color ???) with an empty grey bar at the bottom
[*]Last message on tty3 is "Reading all physical volumes. This may take a while...". I assume "a while" does not refer to hours..
[*]On tty4, the last message is DEBUG: virtual package harddrive-detection
[*]When I run ps on an opened terminal I see the following processes[list][*]ntfsresize -f -i /dev/scsi/...
[*]grep ^You might resize at (surprisingly without any quotes...)
[*]sed s/^You might resize at ..../
[*]tail -n1
[*]grep ^[0-9]*$
[/list]
[*]Trying to run fdisk -l /dev/sda on that terminal freezes
[/list]
I've tried expert mode, but after gotting through a lot more questions I came to the same point. Any idea on how to prevent this. **I definitely do not want to resize my ntfs partition**, there is plenty of unpartitioned space available.

Any help appreciated,
                                 Torsten

---

### Post by issueperson on 2006-03-08
i had some error messages and screwed up my computer the first time i tried to install breezy.  my problem was that my downloaded .iso was corrupt somehow, so i just re-downloaded breezy, re-burned it and it worked fine.

(if you have a scratched disk it could possibly affect it.  but this probably isn't your problem.  just sort of a last-case scenario if no one else comes up with any ideas).

issueperson

---

### Post by treuss on 2006-03-12
Thanks issueperson,

your post made me actually get a new CD and retry, but with no effect. Still freezes at the partitioner.

The problem seems to be kernel related, as when I open up a terminal and try to e.g. manually mount a partition, it freezes as well. The driver via_sata is loaded, and /dev shows correctly the partitions on both disks, so they have been recognized, but any attempt to access those freezes.

I guess I now wait for dapper and live with my 2GB partition for now :(

---

