---
title: "File system is NOT clean."
date: 2011-04-04
forum: General Help
---

### Post by baddogpher on 2011-04-04
Chrome crashed on me, and started writing to the HD (I think).
I rebooted => corrupt file system.
It won't boot now. Version 10.10

So, I made up a start-up CD (v10.04). I tried to use fsck:


ubuntu@ubuntu:~$ sudo fsck /dev/sda6
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda6
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ 

It was *not* mounted. I don't know what program "opened exclusively"

Then I tried the Disk Utility:

<disk utility, check filesystem>
File system check on "Linux" (Partition 6 of Partition 4 of ATA WDC WD10EADS-00M2B0) completed

File system is NOT clean.


So, what can I do if some phantom program is stopping me from doing anything with the Linux partition?
The other partitions are all fine.

Any help appreciated!

---

### Post by cheapie on 2011-04-04
Try the alternate CD in rescue mode with no root selected.

---

### Post by baddogpher on 2011-04-04
> **cheapie said:**
> Try the alternate CD in rescue mode with no root selected.

Ah!
I read:
**8.3.**  How to use a Ubuntu installation CD to gain root user access?
   

[LIST=1]
[*]Boot-up computer into                                 Ubuntu Installation CD
[*] At “boot:” prompt, add                                     “rescue” to the argument
 boot: rescue
[/LIST]

I haven't seen this prompt, but I'll have another look....
Thanks!

---

