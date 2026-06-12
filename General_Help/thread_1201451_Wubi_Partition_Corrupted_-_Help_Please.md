---
title: "Wubi Partition Corrupted - Help Please"
date: 2009-07-01
forum: General Help
---

### Post by daniele.cico on 2009-07-01
Hi all.
I'm new to this forum.
I ask all you guys helps about a big problem.
I have been working with my ubuntu intrepid on wubi partition for some months when yesterday due to a power off of the system my home.disk partition has been lost.

If I run windows i can see the home.disk file with the correct dimension.
Starting ubuntu it take 0 bytes dimensions and so can't mount my home, and all my documents :,-(


Ubuntu start but when logging in with my daniele user there is no home directory
        now i created a new user and I can access to my ntfs filesystem /host/ubuntu/disk/home.disk

I tried a fsck:

[I]sudo fsck /host/ubuntu/disks/home.disk
[sudo] password for recovery: 
fsck 1.41.3 (12-Oct-2009
e2fsck 1.41.3 (12-Oct-2009
fsck.ext3: Attempt to read block from filesystem resulted in short read durante l'apertura di /host/ubuntu/disks/home.disk
E' possibile che questa sia una partizione di dimensione zero?

[/I]
Are there any way to recover them?
Thank you in advance
Daniele

p.s.  starting ubuntu the message is fs type wrong /dev/loop1

---

### Post by daniele.cico on 2009-07-01
I'm triing to run ddrescue I just can HOPE!!!

---

