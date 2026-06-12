---
title: "Periodically sync folders?"
date: 2011-01-09
forum: General Help
---

### Post by neokyle on 2011-01-09
Using Ubuntu 9.10 64 bit.

Basically i need to sync a folder from a ramdisk to a folder on my hard drive every X minutes to prevent loss of data on that ramdisk if my server were ever to crash. 

I'm new to Ubuntu, so i have no idea what I am doing. I would really appreciate any help. Thanks in advance.

On a side not, I'm using this guide to setup the ramdisk, if it matters.

[http://www.linuxscrew.com/2010/03/24/fastest-way-to-create-ramdisk-in-ubuntulinux/](http://www.linuxscrew.com/2010/03/24/fastest-way-to-create-ramdisk-in-ubuntulinux/)

---

### Post by dcstar on 2011-01-09
> **neokyle said:**
> Using Ubuntu 9.10 64 bit.

Basically i need to sync a folder from a ramdisk to a folder on my hard drive every X minutes to prevent loss of data on that ramdisk if my server were ever to crash. 
.......

The whole point about Ramdisks is that you sacrifice memory (and system resources) for files that **you don't want to keep**.

If the data is important, then don't use a Ramdisk.

---

### Post by neokyle on 2011-01-09
For what i am doing i need this folder to be able to have things loaded from it extremely fast which is exactly what a ramdisk can accomplish. I need speeds much faster than a standard hd which is what i have.

---

### Post by eentonig on 2011-01-09
Another use for a ramdisk is to avoid writing too much to your SSD HD, or to have a screaming fast medium for file access.

For the original poster, look at the manpage for rsync and create the rsync command+options that satisfies your needs. And then put this in a cron job.

> man rsync
man cron

---

### Post by neokyle on 2011-01-09
> **eentonig said:**
> Another use for a ramdisk is to avoid writing too much to your SSD HD, or to have a screaming fast medium for file access.

For the original poster, look at the manpage for rsync and create the rsync command+options that satisfies your needs. And then put this in a cron job.

Thank you :) I have almost no experience with Ubuntu, or even ssh clients so this should be a good learning experience to say the least.

---

