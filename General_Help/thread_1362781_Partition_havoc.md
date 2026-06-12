---
title: "Partition havoc"
date: 2009-12-23
forum: General Help
---

### Post by rules on 2009-12-23
Hi all

Let me start from the beginning to give you a clear picture of what's happening ...

When I install windows on a machine, I always use 2 partitions,one for windows install (C DRIVE) and one for file storage (D DRIVE)(makes reinstallation easier). The bug then bit again (linux has been like malaria to me, keeps coming back :)) and I resized my C DRIVE to give me a 10G partition for linux. This left me with 3 primary partitions (oh yes, forgot to mention the windows restore partition) and 1 extended.

I later on resized D DRIVE, stealing 2G for a swap drive, but it now gives me the usual you can only have 4 primary partitions. I can't/don't want to reformat any of the drives. What can I do?

[IMG]http://www.imagehost.co.za/image-9CD8_4B327A4B.jpg[/IMG]

Cheers.

---

### Post by dcstar on 2009-12-24
> **rules said:**
> Hi all

Let me start from the beginning to give you a clear picture of what's happening ...

When I install windows on a machine, I always use 2 partitions,one for windows install (C DRIVE) and one for file storage (D DRIVE)(makes reinstallation easier). The bug then bit again (linux has been like malaria to me, keeps coming back :)) and I resized my C DRIVE to give me a 10G partition for linux. This left me with 3 primary partitions (oh yes, forgot to mention the windows restore partition) and 1 extended.

I later on resized D DRIVE, stealing 2G for a swap drive, but it now gives me the usual you can only have 4 primary partitions. I can't/don't want to reformat any of the drives. What can I do?
Cheers.

Expand the Extended partition and put the Swap inside it.

---

### Post by rules on 2009-12-24
I initially didn't want to shrink my C Drive to much, but this morning I did just that ... this did however,for some reason, kill my mbr and after trying all the "quick fix" mbr repairs I ended killing all my linux partitions, shrunk C Drive even more and then created 2G swap, 9G root and 9G home partition.

Works nice now :)

Thanks.

---

### Post by running_rabbit07 on 2009-12-24
[s]After repairing the Windows MBR, you have to reinstall grub. Is MS working now?[/s]

Looks like you got it all working now?

---

### Post by rules on 2009-12-25
I did, thanks :)

---

