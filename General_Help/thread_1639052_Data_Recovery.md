---
title: "Data Recovery"
date: 2010-12-06
forum: General Help
---

### Post by dizzy1 on 2010-12-06
So here's my predicament, I accidentally formatted over an ext3 partition with an lvm2. The ext3 partition had one file I need. A virtual machine disk drive. I know my files are still there because I ran an undelete at sector level and got some of the pngs I had stored on the vm. 

So I'm wondering if someone can recommend a way to find the superblock of partition of the vm drive or the physical drive? Or any other way I could possibly recover the contents with filenames intact. I have dd'd th drive to another drive. 

Also if this is of any help it was a wd 2tb green drive. formatted with an old version of fdisk. So the partition was made with 512 byte sectors instead of the native 4k and was formatted with mkfs.ext3

---

### Post by searchfgold6789 on 2010-12-06
testdisk should allow you to do that.

---

### Post by dizzy1 on 2010-12-06
I tried testdisk and all it found was the lvm. I tried both the lost partition search and i tried going into expert and searching for the superblock.

---

### Post by oldfred on 2010-12-06
part of Testdisk is photorec which recovers most file types, but cannot recover file names as those are gone. If photos or music the file has internal data that you can use to recover names. If you have a huge drive photorec may take all night or longer as it has to search for all files. On my system I had save a text file many times and it found almost all the versions, but it was hard to sort thru them.  A lot of grepping to search files and find and copy to sub directories to allow a smaller set of files to review.

Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

---

