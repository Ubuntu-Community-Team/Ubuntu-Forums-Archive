---
title: "is there any recovery app better than testdisk/photorec?"
date: 2009-07-04
forum: General Help
---

### Post by chriskin on 2009-07-04
better in the part of keeping the names intact after the recovery of the deleted files i mean :)

---

### Post by earthpigg on 2009-07-04
not a direct answer to your question, but i have found that testdisk/photorec direct download from the website finds and recovers things that the version in the repos does not.

---

### Post by chriskin on 2009-07-04
yes i know, but it always brings it back in strange names.
i had a whole microSD restored in less than 4 minutes , yet i got all the name really strange, like a series of strange letters and numbers

---

### Post by michy99 on 2009-07-04
I have had success with ext3grep.

---

### Post by chriskin on 2009-07-04
> **michy99 said:**
> I have had success with ext3grep.

is it only for ext3 filesystems? or did it start as such and never changed its name? (like photorec did)

---

### Post by tgalati4 on 2009-07-04
If fsck does not work then you are at the mercy of photorec.  fsck will try to repair the file system.  Run in manual or interactive mode and you can get somewhat agressive in your repair.  

Photorec relies on data headers and follows the sector chain to piece files together.  Since photorec does not rely on the file system, it generates random filenames.  A helpful way to recover filenames is to look for text files of recently-used applications.  You can find a list of the last 10 or so files opened in each application.  Of course, you have to rename the files manually, but at least you have a memory jogger of what some recently modified files were.

For music files, you can use easytag to rename files.  There may be some command line tools that can rename files based on ID3 tags.

---

### Post by chriskin on 2009-07-04
> **tgalati4 said:**
> If fsck does not work then you are at the mercy of photorec.  fsck will try to repair the file system.  Run in manual or interactive mode and you can get somewhat agressive in your repair.  

Photorec relies on data headers and follows the sector chain to piece files together.  Since photorec does not rely on the file system, it generates random filenames.  A helpful way to recover filenames is to look for text files of recently-used applications.  You can find a list of the last 10 or so files opened in each application.  Of course, you have to rename the files manually, but at least you have a memory jogger of what some recently modified files were.

For music files, you can use easytag to rename files.  There may be some command line tools that can rename files based on ID3 tags.


hehe i never thought about using the ID tags to rename them
i think i can find a tool like that, there ought to be something that simple around

thanks for the idea :)

---

### Post by Christophe Grenier on 2009-07-06
TestDisk can recover deleted files from FAT
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_FAT](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_FAT)
It also works for NTFS and ext2, but not ext3/ext4.

  Christophe

---

### Post by chriskin on 2009-07-06
would that really be an answer to the question "do you know anything better than testdisk"
i think not

---

### Post by aysiu on 2009-07-06
> **chriskin said:**
> hehe i never thought about using the ID tags to rename them
i think i can find a tool like that, there ought to be something that simple around

thanks for the idea :)
EasyTag is very powerful but it can also be confusing.

If you prefer a simpler interface for renaming music files based on ID3 tag, you can check out TagTool.

---

### Post by chriskin on 2009-07-06
> **aysiu said:**
> EasyTag is very powerful but it can also be confusing.

If you prefer a simpler interface for renaming music files based on ID3 tag, you can check out TagTool.

thanks but i already know how to use easytag well enough, if i find that it doesn't fit this need, i will try your idea too :)

---

