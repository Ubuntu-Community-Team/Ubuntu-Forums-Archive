---
title: "dd growth, rm not working?"
date: 2010-09-14
forum: General Help
---

### Post by OmahaVike on 2010-09-14
hoping someone might be able to help my understanding of what may be happening.

i have a 14 gig USB thumbdrive and installed ubuntu on it, bootable.

for all the below reported information, i used the following command to backup the drive:

```
dd if=/dev/sdh | gzip > webbackup.gz
```

after the intial OS install, and some supporting packages, i backed up the drive.  the resulting .gz file was 2.6g

i added some data to a new directory, then deleted the new directory (rm -fr in cli).  backed up, and now the .gz file length is 4.8g.

ran the drive some more, adding more data and then, again, removing it through a bash shell.  backed up again, and now the resulting file is 9.5g.

i searched through the entire drive for anything .Tra* and couldn't find any trash directories.

First is a question:  why are the dd files growing in size, even though i've deleted the files?
Second is a request:  how do I free up that space so that dd doesn't pick it up and my backup files stay small?

Thank you in advance for any and all help!

---

### Post by asmoore82 on 2010-09-14
`dd` does a binary dump of a device - totally oblivious to "used space" or "free space"
As the drive becomes cluttered with "freed" but non-zero data, the efficiency of zipping it suffers greatly.

You need to use a filesystem cloning utility such as `partimage` -
it will do a smart, sparse backup of only the used data blocks.

This may lead you to wonder why `dd` is still around at all -
`dd` is about as Old-School as it gets, but it still has it strengths and uses.
It is more suited to "bare-metal" or emergency situations when the
underlying hardware is starting to show signs of failure.

---

### Post by OmahaVike on 2010-09-15
thank you!

---

