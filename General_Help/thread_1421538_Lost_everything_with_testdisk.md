---
title: "Lost everything with testdisk"
date: 2010-03-04
forum: General Help
---

### Post by myroad on 2010-03-04
Hello,
[U]
What is happening:[/U]
I have a hard disk of 160GB. I lost files so I used Ubuntu Live CD 9.10 and the program testdisk 6.11 to try to recover them. Now I lost all my data !!!

_What I did:_
I used testdisk, make an analyse then a deeper search. I found my linux partition (ext4) but I wasn't sure if my files were there. When I make testdisk show the files in the partition (by tapping p), it was written something like "The file system is corrupted or unreadable". Nevermind, I changed the status of the partition from deleted (D) to logical (L) then I selected "write". The program wanted to reboot ubuntu so I did so... Now, I only have a small extended partition with 10GB of data according to gparted. I don't have anything in my Computer window !!!!

And when I reboot without the Ubuntu Live CD, I have nothing, no message. ](*,)

_What I think happened:_
I think the linux partition type should be extended instead of logical... It destroyed everything !

_What I am doing:_
Right now, I am redoing a deeper search with testdisk, and I hope I can undo what I did !! I make reappear a 20GB which contains only boot files... and a 110 GB which is unreadeable !! I'm trying again..

[U]The partition table:
[/U]Before, there were:
100MB System Reserved
around 140 GB extended partition
a logical 20GB NTFS for Windows Seven
a logical 15GB empty
a logical 110GB NTFS of documents
a 39MB hidden partition

---

### Post by lavinog on 2010-03-05
why was recovery nessicary in the first place?

photorec is part of the testdisk package.  It analizes the raw data for files and can recover them without partition information...you may need to use that from this point.
Make sure your recover your data to another drive (otherwise you will erase your data for good)

---

### Post by myroad on 2010-03-05
Because I lost files in a NTFS partition and I use this partition a lot. Since I had another copy in a deleted partition, I prefered undelete the partition instead of having files without order with photorec.

Anyway, I give up.

---

