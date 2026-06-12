---
title: "Input/Output Error"
date: 2010-02-26
forum: General Help
---

### Post by Jonny87 on 2010-02-26
Ok so I was trying to copy a video from one drive to another. It starts copying it then stops part way through, stays stoped for a bit, the comes up with an error message. Under the details it says it was an input/output error. What is this all about and how do I get around it?
There is by far enough space on the hard drive that I'm trying to copy to. I can't seem to find away around it.
 
Please help.

---

### Post by cjhabs on 2010-02-26
Is the file larger than 4gb? If it is then maybe the destination filesystem is FAT - which can't handle file sizes that large.

---

### Post by BZF on 2010-02-26
[COLOR="Blue"][FONT="Arial"]ya i was about to say the same thing, depends what kind of FAT it is[/FONT][/COLOR]

---

### Post by Jonny87 on 2010-03-01
Sorry I havn't replyied. forgot to subscribe and have been busy.
 
Niether HDD is on a FAT file system of any sort. I was copying from a NTFS to ext3. 
 
The drive sizes;
     From 500gb to 159gb partition.
 
The file;
     A video of about 800-900mb.
 
As I said there was by far enough free space. Also I copied quite a few other videos, same format and size, FROM and TO the same locations with out any trouble.
 
I have encountered this a couple times in the past but can't work out why it does it. It appears that it for no apparant reason occurs on random files.
 
Any Ideas?

---

