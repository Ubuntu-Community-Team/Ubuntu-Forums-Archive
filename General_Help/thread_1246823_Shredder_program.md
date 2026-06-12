---
title: "Shredder program?"
date: 2009-08-22
forum: General Help
---

### Post by jbeukema on 2009-08-22
Anyone know where I can find a file/freespace shredder for ubuntu?

---

### Post by sasho_zl on 2009-08-22
You already have one installed. Just type in a terminal: ```
shred filename
```

---

### Post by jbeukema on 2009-08-22
> **sasho_zl said:**
> You already have one installed. Just type in a terminal: ```
shred filename
```

1) what algorithm is used?

2)Can it shred all free space?

3)Can it shred batches or folders?

---

### Post by 3rdalbum on 2009-08-22
```
CAUTION:  Note  that  shred relies on a very important assumption: that
       the file system overwrites data in place.  This is the traditional  way
       to  do  things, but many modern file system designs do not satisfy this
       assumption.  The following are examples of file systems on which  shred
       is not effective, or is not guaranteed to be effective in all file sys&#8208;
       tem modes:

       * log-structured or journaled file systems, such as those supplied with
       AIX and Solaris (and JFS, ReiserFS, XFS, Ext3, etc.)

```

Modern filesystems don't guarantee that overwriting a logical file will actually overwrite it physically on the disk. Reliability and "securely erasing files" are mutually exclusive.

If you set up home-partition encryption, you can retain the reliability of Ext3, and make sure that nobody else can get to your data, whether it has been deleted or if it is still present in the filesystem.

---

### Post by sasho_zl on 2009-08-22
You can create an encrypted private folder and that way you can be sure that any recovery of a deleted file will be almost impossible. Use this tutorial - [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

### Post by bumanie on 2009-08-22
Have a look at this [page]("http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html#more-786").

---

### Post by Andrew.Z on 2009-09-10
> **jbeukema said:**
> Anyone know where I can find a file/freespace shredder for ubuntu?

[BleachBit shreds files and free space](http://bleachbit.sourceforge.net/).  The version in the Ubuntu 9.04 repo is too old, so download the latest from the web site.  You can shred any file by clicking File - Shred Files.  Then, to shred free space there is a checkbox under System (be sure to set the preferences first).

Older versions use the GUI, and [BleachBit 0.6.4](http://bleachbit.sourceforge.net/news/test-bleachbit-064-beta) lets you shred free disk space from the command line (or GUI).

---

