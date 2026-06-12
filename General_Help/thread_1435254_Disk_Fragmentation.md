---
title: "Disk Fragmentation"
date: 2010-03-21
forum: General Help
---

### Post by joelgsf on 2010-03-21
This is just a big curiosity I have. Any disk system is based on serial read/write operations and the disk is organized in blocks of data. EXT2 filesystem is based on this same paradigm, as it could not be otherwise. Though EXT2 has a kind of pre-allocating contiguous blocks for a new file, it will end up, inevitably, with pieces of file blocks which are apart, which increases the time needed to get it due to extra head seeks operations. Why is it so, then, that Linux does not have a defragmentation utility?:confused:

TIA for any light thrown on this matter for me.

Joel Guilherme

---

### Post by lyall on 2010-03-21
read this about disk fragmentation 
LinuxFilesystemsExplained
[https://help.ubuntu.com/community/LinuxFilesystemsExplained]("https://help.ubuntu.com/community/LinuxFilesystemsExplained")

good luck and have fun learning

---

### Post by _h_ on 2010-03-21
> **joelgsf said:**
> ***

EXT2? We're on EXT4 right now just so you know. :P

---

### Post by joelgsf on 2010-03-22
> **lyall said:**
> read this about disk fragmentation 
LinuxFilesystemsExplained
[https://help.ubuntu.com/community/LinuxFilesystemsExplained]("https://help.ubuntu.com/community/LinuxFilesystemsExplained")

good luck and have fun learning

Thank you for the link. Better than the link itself were the other links in it. I'm reading them all to get a better understanding on how Linux cares about this problem.
A point, though, puzzled me in that first article, when in the last paragraph it says: "No true defragmenting tools exist for the ext3 file system, but tools for defragmenting will be included with the ext4 file system.".  Are there defragmenting tools in Ext4? If yes, then my concerns are not without some reason. ;)
BTY, I don't know why I've mentioned Ext2 fs, when I'm using Ext3 myself, as Ext4 has been presented to me (by Ubuntu) as a sort of still experimental fs, when I've installed it (Jaunty).

---

### Post by joelgsf on 2010-03-22
> **_h_ said:**
> EXT2? We're on EXT4 right now just so you know. :P

For sure I know. Please read my reply to Lyall.

---

