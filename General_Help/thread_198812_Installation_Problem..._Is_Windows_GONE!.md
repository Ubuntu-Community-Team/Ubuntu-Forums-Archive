---
title: "Installation Problem... Is Windows GONE?!"
date: 2006-06-17
forum: General Help
---

### Post by dejay703 on 2006-06-17
I tried installing ubuntu onto my current windows partition.  I used the manual parititioning table to resize my 32 gig harddrive to 27 gigs.

After the partitioning table finished, something went wrong.  I could not see the new partitions I created (ext3 and linux-swap) to mount.  I then clicked back, and saw that the 32 gig partitoin that was ntfs is now "Not Allocated".  It still has the boot flag.  The system->disks says that this partition is unformatted.

Does this mean that all my files are gone?  Is there anyway to make sure that everything's deleted?

Thanks

---

### Post by dejay703 on 2006-06-17
Oh, btw, I quit the ubuntu install, and tried booting normally, and it said the operating system could not be found...

---

### Post by Sef on 2006-06-17
> ntfs is now "Not Allocated". It still has the boot flag. The system->disks says that this partition is unformatted.

Does this mean that all my files are gone? Is there anyway to make sure that everything's deleted?

It sounds like it.  Do you want to recover those files, or do you have them backed up?

---

### Post by dejay703 on 2006-06-17
I have some of them backed up, but is it possible to access any of it anymore?

---

### Post by Sef on 2006-06-17
You would need something like one of these two:

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

---

