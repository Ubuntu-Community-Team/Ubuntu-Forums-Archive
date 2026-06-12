---
title: "Simulate  bad block or sector on drive"
date: 2010-02-14
forum: General Help
---

### Post by bakegoodz on 2010-02-14
I want to simulate a bad block or sector on a drive or even a virtual drive image to test my data recovery distro. I wish I would have bookmarked when I read about it before. It was some type of low level command, I remember something about scsi subsystem or kernel thingabob. Any ideas?

---

### Post by nixclusive on 2010-02-15
What happens when the operating system attempts to read a real bad block off a disk? I believe the underlying storage system sends an error code that it was unable to read the specified blocks from itself. Not sure how one would go about simulating that, but just food for thought. :)

---

### Post by nixclusive on 2010-02-15
If you want to test the recovery abilities of your distro from a corrupt *file system* you can always make a raw disk image using dd and then dump anything on it from /dev/urandom on random places and then point your recovery distro to this image.

This however is NOT a case of bad blocks.

---

### Post by bakegoodz on 2010-02-15
That makes sense, I don't logical see how one could simulate a real bad block, but I swear that I saw a guide how to do it. Maybe it uses some kernel level trickery. Anyway that is good comment about sprinkling some random bytes to simulate a corrupted file system. I'll have to test that one.

---

