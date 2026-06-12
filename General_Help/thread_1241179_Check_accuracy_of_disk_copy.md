---
title: "Check accuracy of disk copy"
date: 2009-08-15
forum: General Help
---

### Post by bilijoe on 2009-08-15
When making an exact copy of a disk, what's the best (easiest?) way to verify that the copy is an exact match to the original?

---

### Post by pytheas22 on 2009-08-15
I would compare checksums using the command 'md5sum', but the applicability of this depends on what you copied (was it an entire hard drive, a single partition, a CD, a floppy...?) and how you copied it (burn CD to ISO image, create raw disk image using 'dd', etc...there are lots of possible ways).  What exactly did you do?

---

### Post by bilijoe on 2009-08-15
I used the Brassero "Make An Exact Copy" function to copy a Data CD. I didn't see any way to get an md5sum for an entire disk (not an .iso image of a disk, but the disk).:popcorn:

---

### Post by pytheas22 on 2009-08-15
If you click Edit>Plugins in Brasero, you can enable an md5sum-checking feature.  This is probably the best way to go since you're only dealing with CDs.  Otherwise, you could write a script to recursively calculate md5sums for all the files in your original CD and the iso image and then compare them, but using Brasero's plugin would be much easier.

---

### Post by niteshifter on 2009-08-15
Hi,

Interesting question. I take two possible interpretations of it:

A) You want to know if the files from the source are present on the copy. As pytheas22 said, computing md5sums is required.

B) You want to know if the copy can be accurately read, that it is not some borderline readable disc. For this the CLI utility "cdck" is useful:

```
sudo apt-get install cdck
```

cdck will read a CD or DVD and measure sector read timings. Useful since "bad" areas will take longer to read. cdck can be commanded to produce a data file which can be fed to gnuplot for a graph display of the timings. Really handy to have around if you use CD-RW or DVD-RW discs.

---

