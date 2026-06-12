---
title: "resizing my linux partition"
date: 2009-10-26
forum: General Help
---

### Post by lzoulek on 2009-10-26
I just installed linux ubuntu 9.04 to my laptop and I did the dual partition with my existing windows vista. I selected the side by side option and when i tried to run the ubuntu updates, it told me that i dont have enough memory available. so how do I resize my ubuntu partition to make it larger?

---

### Post by magneze on 2009-10-26
Do you mean memory or disk space? It's not clear.

---

### Post by lzoulek on 2009-10-26
sorry i wasnt clear. Disk space

---

### Post by mem0rex on 2009-10-26
Go to add/remove programs and search for a program called Partition Editor and install it. It will Be located under System>Administration.

---

### Post by drs305 on 2009-10-26
lzoulek,

Welcome to the Ubuntu forums.

Unfortunately, there is a bug that improperly selects the default size of a side by side installation. I've written two guides. One for expanding your existing partition by taking space from Windows.

The other tells you how to reinstall and make sure you select the correct partitioning scheme in Step 4.

You will have to do one or the other if you ened up with a 2.5GB partition. It is too small for normal Ubuntu installation.

[ HOWTO: 2.5 GB System Partition - What Went Wrong?  ]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")

[ Expanding an Ubuntu System Partition  ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by lzoulek on 2009-10-26
ok i installed it but it wont let me move or resize anything.

---

### Post by Zoot7 on 2009-10-26
> **lzoulek said:**
> ok i installed it but it wont let me move or resize anything.
That's more than likely the case because the partitions are mounted. You can't resize partitions if the OS that's running is accessing them. 
Your best bet is to boot off a LiveCD and run the partition editor to resize them however you want.

---

