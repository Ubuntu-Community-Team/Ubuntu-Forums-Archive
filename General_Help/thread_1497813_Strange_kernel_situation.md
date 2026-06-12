---
title: "Strange kernel situation"
date: 2010-05-31
forum: General Help
---

### Post by thelugnut on 2010-05-31
I have Ubuntu 9.04 installed on one hard disk, on two separate partitions.

I have initiated "Update Manager" on both partitions. Results for both indicate they are up-to-date.

But one partition shows Linux version 2.6.28-17, with a Dec 2009 date, while the other partition shows 2.6.28-18, with a Mar 2010 date.

> offra@james-laptop:~$ cat /proc/version
Linux version 2.6.28-17-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #58-Ubuntu SMP Tue Dec 1 18:57:07 UTC 2009
offra@james-laptop:~$ 


james@james-laptop:~$ cat /proc/version
Linux version 2.6.28-18-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #60-Ubuntu SMP Fri Mar 12 04:40:52 UTC 2010
james@james-laptop:~$ 


Using the Synaptic Package Manager, I did a search for the kernels.

Both contain the 2.6.28-18 version.

So I am wondering why the first partition has not updated to the 2.6.28-18 version.

---

### Post by BoneKracker on 2010-05-31
Maybe dependencies?

You may have different software installed on the two instances, and one of the instances has an application that requires the earlier kernel release.

---

### Post by thelugnut on 2010-05-31
Yes, never thought of that. Thanks for the reply.

---

