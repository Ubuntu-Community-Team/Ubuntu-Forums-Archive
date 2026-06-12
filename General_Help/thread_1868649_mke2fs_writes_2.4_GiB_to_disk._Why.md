---
title: "mke2fs writes 2.4 GiB to disk. Why?"
date: 2011-10-24
forum: General Help
---

### Post by mrmendel on 2011-10-24
Using the Ubuntu 11.10 64-bit Desktop LiveCD, I created a 149.04 GiB partition using gdisk on an unpartitioned SSD. I opened gparted to notice that nothing has been written to the new partition. Then I used mke2fs like this:

```
sudo mke2fs -t ext4 -O ^has_journal /dev/sda1
```

Right after, I opened gparted to notice 2.40 GiB has been written to this partition. I thought the following part

```
-O ^has_journal
```

makes sure a journal isn't created. So what was actually written to the partition? Thanks.

---

### Post by ajgreeny on 2011-10-24
Is it written to or simply not available as it is reserved for super-user filesystem operations?

See this from "man mke2fs"
> -m reserved-blocks-percentage
              Specify  the  percentage  of  the filesystem blocks reserved for the super-user.  This avoids fragmentation, and allows root-owned daemons, such as syslogd(8),  to  continue  to  function correctly  after  non-privileged processes are prevented from writing to the filesystem.  The default percentage is 5%.

---

### Post by mrmendel on 2011-10-24
Thanks for the fast reply. Unfortunately, I didn't check in time and already installed Ubuntu on that partition. The only thing I can tell right now is under the File Systems tab of System Monitor, the /dev/sda1 partition has a listed "total" of 146.7 GiB, which is 2.3-2.4 GiB less than my initial gdisk partitioning result of 149.04 GiB. This would seem consistent with how the mke2fs procedure took up 2.4 GiB of disk space. To clarify, after I used mke2fs and loaded gparted, it displayed a rectangle of 149.04 GiB that was filled with 2.4 GiB.

When installing Ubuntu, I used the regular desktop CD and selected manual partitioning and selected this partition to mount / and chose NOT to format it. Am I correct in assuming this 2.4 GiB is simply not available?

As a side note, I chose NOT to format it during regular install because I felt formatting again would override my previous arrangements and enable journaling? Am I right?

I don't know how this bit of info affects things, but I'm throwing this out there. During the regular install, I set the bootloader to go on sda, not sda1.

I did not mess with the -m that you mentioned, and the default is 5%. 2.4 GiB is not 5% of the 149.05 GiB SSD capacity, 149.04 GiB initial sda1 partition size after gdisk procedure, or ~146.7 GiB total as reported by System Monitor post-install. It's ~1.6% for all these cases.

If I were to secure erase my SSD and repeat this whole process of using gdisk, mke2fs, and regular install, what should I be looking out for to determine if it's "written" or "simply not available." What exactly do you mean when you say "written" or "simply not available"? By "written," do you mean there are viewable files on the partition? And by "simply not available," do you mean there are not any viewable files on the partition? Thanks again.

---

### Post by dcstar on 2011-10-25
**Every** single filesystem requires space to keep the data on the structure and contents of the filesystem. Some need more than others and **all** are a trade-off between space used and overall filesystem performance.

---

