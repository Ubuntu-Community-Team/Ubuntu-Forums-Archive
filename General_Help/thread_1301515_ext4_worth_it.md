---
title: "ext4 worth it?"
date: 2009-10-26
forum: General Help
---

### Post by jake1017 on 2009-10-26
I have two data storage partitions on my computer. One contains documents, videos, pictures, etc. The other virtual machines. Both are formated in the ext3 file system. Is it worth reformatting both drives to ext4? Will there be a significant performance boost?

---

### Post by DeMus on 2009-10-26
> **jake1017 said:**
> I have two data storage partitions on my computer. One contains documents, videos, pictures, etc. The other virtual machines. Both are formated in the ext3 file system. Is it worth reformatting both drives to ext4? Will there be a significant performance boost?

The boost you are talking about won't happen. Maybe you'll experience some extra speed but it's hardly noticeable.
Also it only works when you put data on a EXT4 formatted disk. When you change an EXT3 disk into an EXT4 disk the data which is already there is still using the EXT3 system, so there will be no extra speed at all.

---

### Post by TenPlus1 on 2009-10-26
When you change an Ext3 filesystem to Ext4 you have to copy your files from one place to another so they take advantage of the Ext4 features... 

e.g.   Drag your Pictures to PicturesNew directory and it'll do the job nicely...

---

### Post by m4tic on 2009-10-26
Right now there really isnt a need to unless you realy really have to, EXT4 isn't really noticable unless you write programs

---

### Post by khelben1979 on 2009-10-26
[EXT4 benchmarks - LinuxInsight]("http://www.linuxinsight.com/first_benchmarks_of_the_ext4_file_system.html")

---

### Post by vinutux on 2009-10-26
I don't Think so coz... it is not your /home

---

