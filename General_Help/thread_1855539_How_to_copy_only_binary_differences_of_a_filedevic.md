---
title: "How to copy only binary differences of a file/device?"
date: 2011-10-06
forum: General Help
---

### Post by qiet72 on 2011-10-06
Here is my dilemma:

# Create the original file
dd if=/dev/urandom of=file1.bin bs=1M count=100
# Create an exact copy.  Both files are now exactly the same
cp file1.bin file2.bin
# Change some bytes in the original file so it is different from the copy
dd if=/dev/zero of=file1.bin bs=1M seek=10 count=1

Now I want to copy just the 1MB of data that is different from file1.bin to file2.bin - how?
I tried to use rsync but it copies the whole 100MB.
zsync works but it is mainly for downloading files from the net.

Any ideas?

qiet72

---

### Post by Slim Odds on 2011-10-06
Try xdelta: [http://xdelta.org/](http://xdelta.org/)

---

### Post by The Cog on 2011-10-06
From man rsync:
>        -W, --whole-file
With  this  option  rsync&#8217;s  delta-transfer  algorithm  is not used and the whole file is sent as-is instead.  The transfer may be faster if this option is used when the bandwidth between the source and destination machines is higher than the bandwidth to disk (especially when the "disk" is actually a networked filesystem).  This is the default when both the source and destination are specified as local paths, but only if no batch-writing option is in effect.
I don't see a way of making it use the delta algorithm on local files, but then again, I don't see a need to either. The delta should work when using remote files.

---

