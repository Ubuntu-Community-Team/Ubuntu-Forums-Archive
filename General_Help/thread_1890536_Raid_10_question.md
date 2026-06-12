---
title: "Raid 10 question"
date: 2011-12-03
forum: General Help
---

### Post by Apv507 on 2011-12-03
Is raid 10 the same as raid 0+1? Some sites say it is, some say it isn't. Okay now for my real question: If I understand Raid 10 correctly the information is mirrored, then stripped. 

Visual aide (Letters represent data groups):

Mirrored:
HDD 1: A B C D E F G H
HDD 2. A B C D E F G H            

Stripped:
HDD 3: A C E G 
HDD 4: B D F H

My question is this: If in Raid 1 you need twice the HDD space as you want to use and in Raid 0 you keep 100% of your space, wont you need the '0" part of the raid 10 to be two drives that are half the size of the other two? For instance two 512gb HDDS in raid 1 gives you the same storage space as two 256bg HDDS in raid 0. The visual aide shows how data fills up two drives twice as quickly as the other two. Thanks for your responses.

---

### Post by dcstar on 2011-12-04
> **Apv507 said:**
> Is raid 10 the same as raid 0+1? Some sites say it is, some say it isn't. Okay now for my real question: If I understand Raid 10 correctly the information is mirrored, then stripped. 

Visual aide (Letters represent data groups):

Mirrored:
HDD 1: A B C D E F G H
HDD 2. A B C D E F G H            

Stripped:
HDD 3: A C E G 
HDD 4: B D F H

My question is this: If in Raid 1 you need twice the HDD space as you want to use and in Raid 0 you keep 100% of your space, wont you need the '0" part of the raid 10 to be two drives that are half the size of the other two? For instance two 512gb HDDS in raid 1 gives you the same storage space as two 256bg HDDS in raid 0. The visual aide shows how data fills up two drives twice as quickly as the other two. Thanks for your responses.

Anything with Striping is **anti_RAID** because you lose redundancy. A Striped drives means that if **either** one of the pair fails you lose **all** the data.

Raid 0 means you halve the MTBF of the drives (they are now **twice** as likely to fail). Making a Striped set RAID 10 means you are adding a redundant set of drives (RAID 1) to bring the MTBF back to the same as a single drive.

Why waste 4 drives in a RAID 10 group when you only get the total capacity of two of the drives when you can have 4 drives in a RAID 5 array and get the total capacity of 3 of the drives?

---

