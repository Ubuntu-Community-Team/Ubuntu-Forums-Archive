---
title: "I/O error on external hard drive"
date: 2011-07-09
forum: General Help
---

### Post by gavdari on 2011-07-09
Hi all,
A few days back, I was moving a file from my home directory to a 1TB WD external hard drive (NTFS). In the middle of the process, the power went out so moving was interrupted. Now, the file I was trying to move is there on the external hard drive, but it can not be read, moved, renamed or removed. Besides, the destination folder on the external hard drive and all other files in it can be read, but they can't be removed or renamed. When I try rm -rf on the folder I get the following error:

```
rm: cannot remove 'x': Input/output error
```

deleting it from dolphin results in this error:

```
Could not rename file /media/x/y...
```

I'm using Kubuntu 11.04 if it matters.

---

### Post by gavdari on 2011-07-10
bump

---

### Post by Ad@m on 2011-07-10
Can you remove the folder using sudo?

Perhaps it would be best to run chkdsk under Windows.

---

### Post by gavdari on 2011-07-10
sudo doesn't work either.
I will try chksdisk. thanks.

---

### Post by wildmanne39 on 2011-07-11
Hi, that kind of error can mean a disk problem or file corruption, you do know that you need to be very careful using that remove command right?

---

### Post by CharlesA on 2011-07-11
> **wildmanne39 said:**
> Hi, that kind of error can mean a disk problem or file corruption, you do know that you need to be very careful using that remove command right?

Yep.

I'd suggest running a SMART check on the drive using the manufacturer's diagnostic tools to make sure the drive is ok.

---

