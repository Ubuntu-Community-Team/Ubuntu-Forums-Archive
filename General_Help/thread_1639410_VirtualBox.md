---
title: "VirtualBox"
date: 2010-12-06
forum: General Help
---

### Post by Mr Nemo on 2010-12-06
Im trying to install opensuse 64 bit on virtualbox, but it keeps telling me virtualbox is a 32 bit machine. Is there anyway to do this, I'm pretty sure i'm using 64 bit virtualbox.

---

### Post by NCLI on 2010-12-06
> **Mr Nemo said:**
> Im trying to install opensuse 64 bit on virtualbox, but it keeps telling me virtualbox is a 32 bit machine. Is there anyway to do this, I'm pretty sure i'm using 64 bit virtualbox.
Please post the output of this command:
```
uname -a
```

---

### Post by Mr Nemo on 2010-12-06
Thanks for the quick reply.

```

2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux

```

---

### Post by snowpine on 2010-12-06
There is some pretty good information on 64-bit guest OS in the VirutalBox Manual:

[http://www.virtualbox.org/manual/ch03.html#intro-64bitguests](http://www.virtualbox.org/manual/ch03.html#intro-64bitguests)

---

### Post by CharlesA on 2010-12-06
Make sure the machine type is set to 64-bit.

---

