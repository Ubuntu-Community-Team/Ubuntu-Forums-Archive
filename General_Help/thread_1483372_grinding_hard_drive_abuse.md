---
title: "grinding hard drive abuse"
date: 2010-05-14
forum: General Help
---

### Post by yyyc186 on 2010-05-14
Since upgrading to 64-bit AMD 10.04 KUbuntu with multiple 1TB hard drives and multiple EXT4 partitions, I have suffered profusely with extreme hard drive activity.  Once every hour or so, one or more of the hard drives will spin up to what sounds like maximum RPM and begin doing some kind of IO which does not light the IO controller.  This will continue for at least 10 minutes, slowing the computer down some.  I have seen others complaining of the same problem and it appears to be some kind of bug/feature with EXT4 journaling.  Since SATA and all IDE drives are lower quality and built for dramatically shorter usage levels than SCSI drives were, I'm really worried this will drastically shorten drive life world wide.

---

### Post by moep on 2010-05-14
What drives are they specifically? Are you running any type of RAID?
There are issues with the Western Digital Green drives that can cause issues such as the one you described.

---

