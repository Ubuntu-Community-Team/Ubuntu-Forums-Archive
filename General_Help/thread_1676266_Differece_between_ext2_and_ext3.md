---
title: "Differece between ext2 and ext3 ?"
date: 2011-01-26
forum: General Help
---

### Post by c2tarun on 2011-01-26
What is difference between ext2 and ext3 partitions?
I am using ext2 partitions, do I have to defragment my partitions after some time?
How can I convert my ext2 partitions to ext3 without loosing any data?
Thanks

---

### Post by hawkmage on 2011-01-26
Here is a description of the differance between ext2 and ext3:
[http://www.linuxnix.com/2009/11/ext2-vs-ext3-file-systems.html](http://www.linuxnix.com/2009/11/ext2-vs-ext3-file-systems.html)

Here is how to convert from ext2 to ext3:
[http://www.troubleshooters.com/linux/ext2toext3.htm](http://www.troubleshooters.com/linux/ext2toext3.htm)

---

### Post by weedeater64 on 2011-01-26
I believe ext3 is journeled, where as ext2 is not. Has to do with data preservation in the event of crashes/power interrupts and the like.

There is no defrag in linux.

Formatting will destroy data, copy/backup data elsewhere before attempting to format.

This may help.

[http://www.tldp.org/HOWTO/html_single/Partition/](http://www.tldp.org/HOWTO/html_single/Partition/)

---

### Post by hawkmage on 2011-01-26
> **weedeater64 said:**
> I believe ext3 is journeled, where as ext2 is not. Has to do with data preservation in the event of crashes/power interrupts and the like.

There is no defrag in linux.

Formatting will destroy data, copy/backup data elsewhere before attempting to format.

This may help.

[http://www.tldp.org/HOWTO/html_single/Partition/](http://www.tldp.org/HOWTO/html_single/Partition/)
There is no reason to format to change an existing ext2 partition to ext3.  Basically all you do is turn on journaling and mount it as ext3.  

There are applications out there to defrag an ext3 file system.

---

### Post by weedeater64 on 2011-01-26
> **hawkmage said:**
> There is no reason to format to change an existing ext2 partition to ext3.  Basically all you do is turn on journaling and mount it as ext3.  

There are applications out there to defrag an ext3 file system.


Hmm, good to know. Guess I was confused by the "format to" in gparted.

I thought I read somewhere that defrag was just unneeded in linux?.?

Did I get the data preservation bit correct?

---

