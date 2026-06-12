---
title: "Restore Windows Vista partition"
date: 2010-11-09
forum: General Help
---

### Post by reklame on 2010-11-09
Hello,

I'm pretty new in this.

I installed Ubuntu 10.10 on my Compaq Presario CQ60 Notebook. 

Now i want to go back to Windows Vista for a while.

I can't find a way to boot the recovery partition. Here's an output from my disks.

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37767   303355904   83  Linux
/dev/sdb2   *       37767       38914     9212929    5  Extended
/dev/sdb5           37767       38914     9212928   82  Linux swap / Solaris

I think its the "Extended" sdb2 disk witch is the recovery disk. I tried to flag the disk with the boot-flag, but it didnt boot.

Any solutions?

---

### Post by nothingspecial on 2010-11-09
I don`t see anything other than Ubuntu :(

You sure you didn`t install over the entire disk?

---

### Post by lordskid on 2010-11-09
sdb2 is an extended partition. you have a very very large swap partition. If I am not mistaken you halved ur hard drive during install 

extended partitions contains other partitions...
sdb1 contains ur linux
sdb2 is a logical partion which contains
  the sdb5 partition which is ur swap.

You will have to download or visit the support for your laptop.

---

### Post by reklame on 2010-11-09
> **nothingspecial said:**
> I don`t see anything other than Ubuntu :(

You sure you didn`t install over the entire disk?

I really don't know! Hoped someone could tell me!?

---

### Post by reklame on 2010-11-09
> **lordskid said:**
> sdb2 is an extended partition. you have a very very large swap partition. If I am not mistaken you halved ur hard drive during install 

extended partitions contains other partitions...
sdb1 contains ur linux
sdb2 is a logical partion which contains
  the sdb5 partition which is ur swap.

You will have to download or visit the support for your laptop.

Thank you for your answear. Does this mean that i have to buy a new version of windows? Cous i cant download windows vista from Compaq support :-(

---

### Post by lordskid on 2010-11-09
try looking for a copy of the restore disc sometimes you can download it from the internet. but buying a copy of windows would be easier. you can also try to borrow a vista installer and look under your machine for a product key. just use your product key to make ur system legit.

---

### Post by reklame on 2010-11-09
> **lordskid said:**
> try looking for a copy of the restore disc sometimes you can download it from the internet. but buying a copy of windows would be easier. you can also try to borrow a vista installer and look under your machine for a product key. just use your product key to make ur system legit.

So the partition with the recovery is gone? And you are sure about that? Cous one time i installed Windows 7 and coudnt find the recovery. Then i just put the other partition "active" and it booted from the recovery partition.

---

### Post by lisati on 2010-11-09
Did you remember to make a set of recovery disks? If not, ouch!

---

### Post by reklame on 2010-11-09
> **lisati said:**
> Did you remember to make a set of recovery disks? If not, ouch!
hehe. no i didnt. i tought it was OK with the recovery partition...

---

### Post by Quackers on 2010-11-09
Can you please go to the site below and download the boot script to your DESKTOP then run it in a terminal using the command given on the first page of that site. It will produce a results.txt file on your desktop. Please copy the contents of this file and paste it between code tags in your next post. For code tags select New Reply then click on the # symbol in the toolbar.
This will confirm your present disk layout.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

