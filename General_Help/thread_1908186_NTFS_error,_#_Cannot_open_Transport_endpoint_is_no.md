---
title: "NTFS error, # Cannot open: Transport endpoint is not connected"
date: 2012-01-12
forum: General Help
---

### Post by GoldenStake on 2012-01-12
Sorry to dig up an old thread, but I recently recieved this error. It is making my Windows partition unusable in Ubuntu. 
But like the others are implying, there does seem to be some harddrive corruption. I was forced to recently run chdsk on my windows machine. as ntfsfix found nothing. 
CHDSK found and fixed a lot of errors, but the inputoutput error still occurs.

Now if i try to transfer or do anything with several files at once. (copied a directory and unarchived an targz) after a few files complete it throws a
# Cannot open: Transport endpoint is not connected
and I'm forced to remount the partition.

Here's the output of fdisk -l; cat /etc/fstab/; df -h
[http://pastebin.com/CnGrMGFc](http://pastebin.com/CnGrMGFc)
since I've had problems with my mounting permissions before.

I will try to run a fsck on my Linux partition to see if anything comes up.
is there a fsck for windows and NTFS partitions that I don't know about?

---

### Post by oldos2er on 2012-01-12
Post moved to its own thread.

---

