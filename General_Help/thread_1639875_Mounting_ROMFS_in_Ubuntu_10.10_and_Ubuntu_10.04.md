---
title: "Mounting ROMFS in Ubuntu 10.10 and Ubuntu 10.04"
date: 2010-12-07
forum: General Help
---

### Post by kNemo on 2010-12-07
Hi, friends.
Sorry for my bad english.
I'm try to solve a problem.

I'm want to mount image ROMFS in Ubuntu 10.10


file <imagefile>


returns:

"<imagefile>: Linux Compressed ROM File System data, little endian size <xxxx> version #2 sorted dirs CRC <xxxx>, edition 0, <xxxx> blocks, <xxxx> files"


mount -o loop <imagefile> <dst>


Mounting successful. In <dst> I see a tree of directories.
But when I'm try to open/copy files from <dst> Midnight Commander shows error message:

Cannot read source file <filename>
Input/Output error (5)

and in /var/log/syslog appears next strings:


cramfs: bad blocksize <xxxx>


and many strings:


error -3 while decompressing
error -5 while decompressing


Same problem in Ubuntu 10.04

In Ubuntu 9.04 all OK. All files opens/copying successful.

Is there anybody know how to solve this problem?

---

### Post by nniico on 2012-03-22
Same problem here. Still no clue?

---

### Post by nniico on 2012-04-05
Answering to myself for future reference.

It is possible, if you follow [those explanations]("http://wdtvforum.com/main/index.php?action=printpage;topic=2922.0"):

[LIST=1]
[*]Get the source code of cramfs-1.1,
[*]modify [FONT=Courier New]cramfsck.c[/FONT] :
at line 68, change [FONT=Courier New]#define PAGE_CACHE_SIZE (4096)[/FONT]
with [FONT=Courier New]#define PAGE_CACHE_SIZE (4096 * 4)[/FONT]
at line 88, change [FONT=Courier New]#define ROMBUFFER_BITS   13[/FONT]
with [FONT=Courier New]#define ROMBUFFER_BITS   14[/FONT]
[*]rebuild and run.
[/LIST]

Voilà.

---

