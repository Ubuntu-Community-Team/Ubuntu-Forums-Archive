---
title: "What is wrong with my directory permissions?"
date: 2009-06-26
forum: General Help
---

### Post by Stugol on 2009-06-26
Hi.
I think I have a serious permissions issue, and would appreciate any help you can offer me.

I have tried to install three different database servers - MySQL, Firebird and PostgreSQL - on my Ubuntu 9.04 system. In each case, they worked fine until I told them to store their databases in a non-default location. For example, a subdirectory of my home directory; or on a different hard drive mounted somewhere in /mnt. At this point, each database server keeled over sideways and died, complaining about insufficient file permissions.

Yeah, okay. Except my permissions are fine. The location in /mnt has full permissions right across the board, as it is a TrueCrypt-mounted NTFS partition mounted with 'umask=000'. Anyone can access it.

As for my home directory, well, I've tried 'CHMOD o=rw' on the subdirectory and things like that. It just doesn't help. The permissions look fine - I've done 'ls -l' dozens of times and it looks right - but the database servers just won't touch it with a barge pole.

I don't know what I'm doing wrong. Can someone more experienced help me out?

---

### Post by ad_267 on 2009-06-26
The files probably have to be owned by the user the database runs as. MySQL database files should be owned by the mysql user. I'm not sure you can store the files on an NTFS partition then.

---

### Post by Stugol on 2009-06-26
You might be right. I will try creating a small file-hosted TrueCrypt container, and mounting that in /mnt with ownership of MySQL, and see if that works.

But it's a bit silly, innit? Why should MySQL need to OWN the folder? Shouldn't access permissions be enough??

---

### Post by mcduck on 2009-06-26
> **Stugol said:**
> You might be right. I will try creating a small file-hosted TrueCrypt container, and mounting that in /mnt with ownership of MySQL, and see if that works.

But it's a bit silly, innit? Why should MySQL need to OWN the folder? Shouldn't access permissions be enough??

Many services require certain file ownerships and permissions, simply to protect themselves from other users. Full read/write permissions for everybody is rarely a smart setup and services are designed with certain level of security in mind.

So, it's not really a question of giving MySQL the required permissions to work with, but making sure everybody else doesn't have the same permissions.

---

### Post by Cheesemill on 2009-06-26
Take a look at your AppArmour config. I remember having to change settings in it when I moved my MySQL database location because it restricts file access for certain daemons to specific locations.

---

### Post by Stugol on 2009-06-26
FINALLY!!!! Thank you!!! That was the problem!

---

