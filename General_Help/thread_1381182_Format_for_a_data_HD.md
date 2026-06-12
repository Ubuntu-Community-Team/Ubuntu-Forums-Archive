---
title: "Format for a data HD?"
date: 2010-01-14
forum: General Help
---

### Post by rcayea on 2010-01-14
I'm not sure if I am over thinking this but....

I was asked to format two hds.

One is for an OS. OK, I get that. 

But I was asked to format the other one as a "data HD". 

Could someone tell me the difference or what I do different to format for a data HD?

Thanks,
Randy

---

### Post by mk1w86 on 2010-01-14
> Could someone tell me the difference or what I do different to format for a data HD?

I'm not quite sure I understand your question but formatting is the same whatever you want to use the drive for.  :-s

If however you want to know what filesystem to use, what will the drive be used for and how big is it etc.? :-k

---

### Post by falconindy on 2010-01-14
If you knew what kind of files were going to be stored on the drive, you could pick a filesystem to suit the data.

Lots of large files, w/ few small files? Use XFS.
Lots of small files w/ few large files? Use ReiserFS.
Need reliability? Use Ext3.
Like to live on the edge? Use btrfs.

Got lost halfway through this post? Use Ext3.

---

### Post by rcayea on 2010-01-14
Thanks for the information/feedback.

---

### Post by michy99 on 2010-01-14
Want to be able to access the data from Windows? Use NTFS.

---

