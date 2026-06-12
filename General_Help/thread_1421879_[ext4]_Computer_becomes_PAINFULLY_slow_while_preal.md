---
title: "[ext4] Computer becomes PAINFULLY slow while preallocating large files"
date: 2010-03-04
forum: General Help
---

### Post by mmillman on 2010-03-04
Ok, I'm not really sure what is causing this, but i suspect it to be the ext4 file system...

I am running a fully up to date Ubuntu 9.04 (Jaunty) installation with ext4 partitions... 

Whenever I download large files via bittorrent, the computer becomes painfully slow while preallocating the space for the files... this happens regardless of what client I use (I've tried transmission, ktorrent, and rtorrent... I've also changed the preallocation settings in ktorrent to no avail).  It becomes almost completely unusable until the allocation is complete, and it takes unusually long (a 695mb file takes over 5 minutes to finish allocating... the computer is unusable during this time).

My torrents also seem to be very corrupted when they actually finish... sometimes up to half the chunks either "fail" or "did not download".  This is remedied by starting the torrent again and letting it download the failed/not downloaded chunks... sometimes I have to do this 2 or 3 times (depending on how big the torrent is) to successfully download all the chunks... I'm running rtorrent with the "safe_sync = yes" option which seems to help slightly, but not completely...  I suspect that this, however, could very well be due to the fact that I am using a very old wireless b router and wireless b network card...

The preallocation problem bothers me much much more than the bad chunk problem...


I am not really sure what is causing this, but I expect it to be file system related... it's worth noting that this behavior happens regardless of whether or not I use the "nodelalloc" flag on my ext4 partitions... I've tried both with and without the flag to no avail.

Anyone know how I can fix this(these) problem(s)?

I don't want to switch back to ext3 as I really don't feel like backing up and restoring everything, although if I absolutely need to, I plan on using ext4 for my / and ext3 for my /home...  Any thoughts on this?  I figure this way i can still take advantage of the ext4 speed advantage, especially on bootup, but I won't have to worry about pre-allocation related corruption for my downloads and settings on the ext3 partition.

---

### Post by blueridgedog on 2010-03-04
No real solution here, but a suggestion for testing - as you suspect it is an ext4 issue, it would be great to verify by going back to ext3 for the partition used to store the data.  I use ext4 for / and ext3 for my data drives and have not had the issue.

---

### Post by Mickael2 on 2010-07-11
I've experienced same problem using Vuze (Azureus) program.
I confirm, pre-allocating files on ext4 partitions is very long !

Here's my test on a new 2To Hard drive:

- formatting the whole drive (1 partition) in:
    ext3: 9mn51s (mkfs.ext3 /dev/sdb1)
    ext4: 6mn13s (mkfs.ext4 /dev/sdb1)

- copying a 4GB file to:
    ext3: 1mn54s
    ext4: 1mn51s

- pre-allocating a 880MB torrent using Vuze:
    ext3: 17s
    ext4: 1mn22s ](*,)  (the HD is very noisy;  I can hear the HD-heads travelling a lot on the disk, but I have no data corruption)

The diffenrence is very important !
The ext4 block allocation process is strange (a lot of HD operations)
Is this 'bug' reported to the ext4 dev-team ?

-Edit-
Note: my Vuze program is configured with: 'allocating new files with zero' ! This option seems to bring problems with ext4 partitions !

---

### Post by RJARRRPCGP on 2010-07-11
Sounds like the data is being allocated to the far end of the HDD. 

You want the files to be closest to the beginning region as much as possible.

---

### Post by Mickael2 on 2010-07-11
No, the test is done on a fresh formatted partition and the file is at the beginning of the partition (I've checked with the stat command)

The problem is that ext4 seems to have problem with filling blocks with 0.
I think ext4 has its own way to reserve inodes with the new extend function...
...But I'm not an expert

---

### Post by Neo40 on 2010-08-02
I have the same problem. No solution to this problem until now?

---

### Post by clhsharky on 2010-08-02
mmillman
or Neo40

Are you still using Jaunty kernel?

Sharky

---

### Post by Neo40 on 2010-08-06
> **clhsharky said:**
> mmillman
or Neo40

Are you still using Jaunty kernel?

Sharky

i use Ubuntu 10.04 with kernel default and my partions are ext4.
When I try to D/L a big file (7 GB) with Transmission, it becomes frozen after a few seconds...Transmisson works just fine if files are not big. For examples, I know 700M or 1.2 GB work without problem.

---

### Post by Mickael2 on 2010-08-07
I've just made an update of my ubuntu sytem 09.10 to 10.04 (Kernel v.2.6.32-24-generic #39-Ubuntu SMP) and this ext4 problem has disappear !

---

