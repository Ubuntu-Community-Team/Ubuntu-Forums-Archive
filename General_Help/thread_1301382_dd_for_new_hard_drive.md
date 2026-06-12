---
title: "dd for new hard drive"
date: 2009-10-26
forum: General Help
---

### Post by cumptrnrd on 2009-10-26
I am about to upgrade to an SSD, and I was wondering if I could just dd my current drive to a file and dd it back onto the new SSD and have everything work.  In theory, I guess the data should all be fine, but I'm not too sure how copying the MBR and whatever boot partitions and stuff would work out...

---

### Post by undecim on 2009-10-26
If you copied the entire drive (for example, /dev/sda), then this should work, as long as the new drive were at least as large as the old one.

Though I think there will be some other caveats to that involving the drive geometry. The filesystem you have now was built to run on your old drive based on its geometry, and the new drive will almost definitely have a different setup.

It's probably best to just start with a new filesystem. As long as you preserve file permissions (i.e. use the -a flag with the cp command and store the files in a system that remembers permissions), you can just copy the old files over, and everything will work the same, as long as you edit your fstab file accordingly.

---

### Post by jbrown96 on 2009-10-26
I wouldn't copy anything other than the MBR with dd. You can copy that with ```
dd if=/dev/sda of=/dev/sdb bs=512 count=1
``` change /dev/sda and /dev/sdb as needed.

---

### Post by cumptrnrd on 2009-10-26
I guess I'll just wait until 9.10 comes out and start over instead of going through all that.

---

