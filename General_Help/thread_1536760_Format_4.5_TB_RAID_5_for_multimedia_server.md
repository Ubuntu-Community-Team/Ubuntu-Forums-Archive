---
title: "Format 4.5 TB RAID 5 for multimedia server"
date: 2010-07-22
forum: General Help
---

### Post by glendo on 2010-07-22
I have created a software raid 5 array which is currently sitting idle all space is unallocated. My plan was to use all 4.5 TB as a single partition for multimedia files. My problem is that I am trying to set up a file server acessible to windows systems al well as linux. Is there a file system I can use to partition this space that will geve me what I want?

---

### Post by davidmohammed on 2010-07-22
you'll need to format it as NTFS if you want windows to automatically recognise it.

---

### Post by Vincentlaborant on 2010-07-22
Depending on your set up, you have the option to do the following things:

* Create a NTFS volume, which can be fully accesed by Windows and Ubuntu has read options.

* Use NFS (network file system), after which you can make it fully accesable for both Windows and Ubuntu using Samba.

The first option is the easiest way to go, and there is not much that can go wrong. I have to say I do not have that much experience with setting up a dual OS network (did it once with option 1 which worked nice).

---

### Post by glendo on 2010-07-22
I tried to format it with NTFS but I got an error saying it was over the maximum size limit

---

### Post by Vincentlaborant on 2010-07-22
NTFS only supports a partition up to a size of 2 TB.

On the dutch site of Microsoft I found this:

>  De maximale grootte van volumes en partities is 2 terabyte (TB) of meer.  Zo kan een dynamische schijf met een standaardclustergrootte (4 kB)  partities van 16 TB minus 4 kB hebben. Zie de *Windows Server 2003  Resource Kit, Server Management Guide* op de website [Microsoft  Windows Resource Kits]("http://go.microsoft.com/fwlink/?LinkID=4681") voor meer informatie over maximale volumes en  partitiegrootten.

Or in English:

[http://technet.microsoft.com/en-us/library/cc779002%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/cc779002%28WS.10%29.aspx")

Basicly you need a dynamic drive with default cluster settings (4Kb) so you can make a partition of about 15,99 TB

---

### Post by davidmohammed on 2010-07-22
you'll need windows x64 to do this I think.

read the first section of this [webpage]("http://carltonbale.com/how-to-break-the-2tb-2-terabyte-file-system-limit") which may give you some ideas.

---

### Post by glendo on 2010-07-26
I decided to partition using gp partition and ext4.

---

