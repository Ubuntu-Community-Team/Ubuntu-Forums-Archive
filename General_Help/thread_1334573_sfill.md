---
title: "sfill?"
date: 2009-11-22
forum: General Help
---

### Post by pwhipped on 2009-11-22
I'm somewhat confused by the sfill command from the secure-delete package. Does it do passes on free space within a partition? Ie: If i have one large partition with ubuntu on it, does it fill the space that is unused(or deleted) in the partition without damaging the used part of the filesystem?

Thanks ahead of time.

---

### Post by YosefKaro on 2009-11-22
A good place to read up on secure-delete commands can be found [here]("http://www.techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/")

-Yos

---

### Post by pwhipped on 2009-11-22
> **YosefKaro said:**
> A good place to read up on secure-delete commands can be found [here]("http://www.techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/")

-Yos
That's actually where I found out about the package. :) It isn't clear however.

---

### Post by ajgreeny on 2009-11-22
I think it does.  See below copied from the webpage [http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html#more-786](http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html#more-786)

> **sfill – secure free space wipe**
 sfill is designed to delete data which lies on available diskspace on mediums in a secure manner which can not be recovered by thiefs, law enforcement or other threats. The wipe algorythm is based on the paper “Secure Deletion of Data from Magnetic and Solid-State Memory” presented at the 6th Usenix Security Symposium by Peter Gutmann, one of the leading civilian cryptographers.
 **sfill Syntax**
 [INDENT]sfill [-f] [-i] [-I] [-l] [-l] [-v] [-z] directory/mountpoint
[/INDENT] **Available Option**
 -f – fast (and insecure mode): no /dev/urandom, no synchronize mode.
 -i – wipe only free inode space, not free disk space
 -I -wipe only free disk space, not free inode space
 -l -lessens the security. Only two passes are written: one mode with 0xff and a final mode with random values.
 -l -l for a second time lessons the security even more: only one random pass is written.
 -v – verbose mode
 -z – wipes the last write with zeros instead of random data
 directory/mountpoint this is the location of the file created in your filesystem. It should lie on the partition you want to write.


---

