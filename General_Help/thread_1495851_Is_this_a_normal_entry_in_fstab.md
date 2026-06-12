---
title: "Is this a normal entry in fstab?"
date: 2010-05-28
forum: General Help
---

### Post by blindenvy on 2010-05-28
I do a lot of folder mapping on my ubuntu box so I have lots of entries in my fstab file, when I was going through the file today I saw an entry I did not add. I was wondering if anyone can tell me if its an odd listing or not, (ie is someone doing something on my box remotely)

binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

in the /proc/sys/fs/binfmt_misc folder there are the following files

cli  python2.6  register  status

Any feedback would be greatly appreciated. If you need more info please let me know.

---

### Post by kiddykoff on 2010-05-28
I have those files, with an additional jar file

anything else?

---

### Post by blindenvy on 2010-05-28
No those are the only files. So I guess its normal. Can one more person confirm they also have that entry in fstab?

Thanks in advance.

---

### Post by Joe of loath on 2010-05-28
You could always comment it out and see if anything breaks?

---

