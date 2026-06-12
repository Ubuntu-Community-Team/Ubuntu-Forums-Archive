---
title: "File Size Mystery: Total Size of Files v. Size on Disk"
date: 2012-02-17
forum: General Help
---

### Post by meowsus on 2012-02-17
I was in the IRC channel talking about this and it didn't seem like anyone else had a problem like this:

I looted the data from this old, burnt out Mac Book Pro for a friend and copied it onto my big ol internal drive. It was coming from, obviously, an HFS+ drive and going to a EXT4 drive.

On the EXT4 drive, when I right-click on the folder and view Properties, the Total Size Of Files is 57.3 GB whereas the Size on Disk is 458.3 GB.

I've never seen a size discrepancy that huge before, nor do I know why this is happening or essentially what the difference is between these numbers.

Little help?

(thanks dudes)

---

### Post by gordintoronto on 2012-02-17
It might help if you said what OS and file manager you are using.

---

### Post by meowsus on 2012-02-17
> **gordintoronto said:**
> It might help if you said what OS and file manager you are using.

Hmm, good call. Lubuntu 11.10 and PCman file manager.

---

### Post by dcstar on 2012-02-18
> **meowsus said:**
> 
...........
On the EXT4 drive, when I right-click on the folder and view Properties, the Total Size Of Files is 57.3 GB whereas the Size on Disk is 458.3 GB.

I've never seen a size discrepancy that huge before, nor do I know why this is happening or essentially what the difference is between these numbers.
..........

Hidden files, files & folders you do not have permission to access.

---

### Post by meowsus on 2012-02-19
> **dcstar said:**
> Hidden files, files & folders you do not have permission to access.

I might be mistaken, but if it's on my HDD shouldn't root be able to determine the correct size now? If it's just a permissions issue why would 

```
$ du -sh /media/Terrorbyte/NikkitasHDDHomeDir
```

and 

```
$ sudo du -sh /media/Terrorbyte/NikkitasHDDHomeDir
```

both yield **54 G**?

I'm just not sure what the difference between *Total Size of Files* and *Size on Disk* is, and why the latter is almost 10x larger than the former?

Thanks for your responses so far.

---

### Post by dcstar on 2012-02-20
> **meowsus said:**
> 
..........
I'm just not sure what the difference between *Total Size of Files* and *Size on Disk* is, and why the latter is almost 10x larger than the former?


A file of 1 byte will consume a minimum of **n** Bytes on the disk, where **n** is the block size the disk was formatted in.

You could have 1 million 1 byte files which will total 1MB, but if the disk block size is 4096 bytes then the usage on the disk will be 4GB.

---

### Post by meowsus on 2012-02-20
> **dcstar said:**
> A file of 1 byte will consume a minimum of **n** Bytes on the disk, where **n** is the block size the disk was formatted in.

You could have 1 million 1 byte files which will total 1MB, but if the disk block size is 4096 bytes then the usage on the disk will be 4GB.

Okay, thank you for this information. That better explains the discrepancies I see between the two numbers.

Pardon my ignorance, but then why would this be the only directory that's Total Size and Size on Disk are 10x different from each other? Is it because the HFS+ drive had a way different block size than my EXT4 drive? And if so, is there any way to drop this folders Size on Disk down? I have an external HDD, but it's only 250GB and the Size on Disk makes the directory nontransferable.

Thanks again for helping me understand a bit more about this.

---

### Post by csmth on 2012-02-24
I have a similiar problem in my ubuntu 11.10 with LXDE session using PCMan, despite I never used HFS+.

 I had been using ext3 (when using 10.04) and later on converted to ext4. Partition size of /home is 266GB. It is not possible to have 1.8TB space. I guess the PCMan has some problem.

[IMG]http://i.imgur.com/oJK2j.png[/IMG]

---

### Post by dcstar on 2012-02-24
> **meowsus said:**
> 
..........
Pardon my ignorance, but then why would this be the only directory that's Total Size and Size on Disk are 10x different from each other? Is it because the HFS+ drive had a way different block size than my EXT4 drive? And if so, is there any way to drop this folders Size on Disk down? I have an external HDD, but it's only 250GB and the Size on Disk makes the directory nontransferable.

Thanks again for helping me understand a bit more about this.

The block size is set when the filesystem is created and formatted, it cannot be changed.

If the folder in question has many (many) small files then it will use the disk space inefficiently and you can end up with that situation.

You can create a new EXT4 partition manually using a smaller block size than default and the results will probably be a lot different.

---

### Post by meowsus on 2012-02-24
> **dcstar said:**
> You can create a new EXT4 partition manually using a smaller block size than default and the results will probably be a lot different.

What is a good block size to use?

---

