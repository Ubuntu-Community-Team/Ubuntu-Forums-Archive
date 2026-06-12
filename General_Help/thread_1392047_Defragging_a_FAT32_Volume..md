---
title: "Defragging a FAT32 Volume."
date: 2010-01-27
forum: General Help
---

### Post by chrispche on 2010-01-27
How would I go about doing this if I don't have Windows. I want to defrag my FAT32 external USB hard drive.

Any help appreciated.

---

### Post by chrispche on 2010-02-15
Still not sure how to do this. Anyone???

---

### Post by darolu on 2010-02-15
This link may help you:
[http://www.webupd8.org/2009/10/defragmenting-linux-ext3-filesystems.html](http://www.webupd8.org/2009/10/defragmenting-linux-ext3-filesystems.html)

---

### Post by howefield on 2010-02-15
Don't know of any defragmenting tools in linux for Windows file systems, why would there be ?

Most people who have such file systems already have windows or at least access to it.

One workaround would be to copy the files from your external drive some place, reformat your external and then copy the files back. They will be put back in a contiguous fashion.

---

### Post by howefield on 2010-02-15
> **darolu said:**
> This link may help you:
[http://www.webupd8.org/2009/10/defragmenting-linux-ext3-filesystems.html](http://www.webupd8.org/2009/10/defragmenting-linux-ext3-filesystems.html)

Which part of this will defragment a Fat32 file system ?

---

### Post by jamesisin on 2010-02-15
In Windows I use and recommend highly DisKeeper:

[http://www.diskeeper.com/](http://www.diskeeper.com/)

It is a great Windows utility.

But you are running Ubuntu.  You shouldn't need a defragmentation utility.

If you really want to defrag a drive (FAT32 included), you can move all the files off and then transfer them back on.  This will give your OS the opportunity to better allocate space for all the files.

---

