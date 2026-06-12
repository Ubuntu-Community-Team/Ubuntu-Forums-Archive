---
title: "Creating Primary Partition with GParted"
date: 2011-03-05
forum: General Help
---

### Post by Veld on 2011-03-05
Due to a problem which I could not solve, I had to format the hard drive.
I am running a dual boot of WIndows XP and Xubuntu 10.10 and I want to have an NTFS partition so I access files in both OSs. From what I understand, it has to be a Primary Partition, not a logical one, right? 
The thing is, GParted doesn't give me the option to create a Primary Partition, only a Logical one inside sda2 (Xubuntu). Am I doing something wrong? 
Thanks.

P. s.: I am running GParted from inside the Live CD.

---

### Post by jerome1232 on 2011-03-05
sda1-4 are always primary partitions.

I think you forgot to put the gparted window up in your screenshot so I can't really help you with specifics. Get a new screenshot up!

---

### Post by Veld on 2011-03-05
Here it is!

---

### Post by jeremyjjbrown on 2011-03-05
Your Unallocated space is inside the Extended partition SDA2. You can create and NTFS logical partition there and use it to store and share file between Ubuntu and Windows with out issue. It does not need to be a Primary.

---

### Post by Veld on 2011-03-05
Isn't it safer to be Primary so it's outside the OS partition, in case something happens?

---

### Post by jerome1232 on 2011-03-05
I missed the part about it being a storage partition. As the previous post said it does not need to be a primary partition unless you plan on booting Windows from it.


In addition to the previous post if you DID require it to be a primary you could shrink sda2 down and add in up to 2 more primary partitions in the space after sda2.

edit: It doesn't matter really if it's primary or logical, logical partitions are just a trick to allow more than 4 partitions on a msdos partition table.

---

### Post by jeremyjjbrown on 2011-03-05
By the way the package ntfs-config is a useful graphical control panel for ntfs partitions in ubuntu.

It's not installed by default.

---

### Post by jeremyjjbrown on 2011-03-05
> Isn't it safer to be Primary so it's outside the OS partition, in case something happens?

Not really. Just back up your files.

---

### Post by Veld on 2011-03-05
My idea was to have an independent partition for storage so I could access the files from one OS in case something happened to the other... How do I move the allocated space? 

I really appreciate you help, thanks! :)

---

### Post by jeremyjjbrown on 2011-03-05
> How do I move the allocated space? 


That's a lot of work for nothing. The partition table is an element completely separate from any OS. Even if you completely nuked both OS's you could put the HD in an external case, attach it to another box and browse your info as if nothing ever happened.

---

### Post by Veld on 2011-03-05
OK, I see. I'll just make the free space into a logical partition, then! 

Everything is OK like this, then?

---

### Post by jerome1232 on 2011-03-05
Yes.

---

### Post by Veld on 2011-03-05
Many thanks once again for your help! :D

---

### Post by srs5694 on 2011-03-05
> **Veld said:**
> Isn't it safer to be Primary so it's outside the OS partition, in case something happens?

I realize you've got a solution to the problem, but I just want to point out that your /dev/sda2 isn't an "OS partition;" it's an extended partition, which can hold partitions used by any number of different OSes. The fact that your extended partition initially held only Linux partitions is irrelevant.

---

