---
title: "grouping of partitions"
date: 2010-02-24
forum: General Help
---

### Post by alphageek89 on 2010-02-24
when using gparted why does dev/sda2 have the remaining sda*. as dropdown. when using solaris i am having problems specifying sda10 as it all comes under ext-dos.
[http://bit.ly/cwdZJ9](http://bit.ly/cwdZJ9)

---

### Post by cong06 on 2010-02-24
are you Dual booting?

Generally when you set up a partition for ubuntu with an existing boot partition, the install will resize the first partition (/dev/sda1) making space for (/dev/sda2).
Then inside /dev/sda2 they put all the linux partitions, which includes the boot partition and the swap partition.
There's a specific term for nested partitions that I forget... is it 'virtual' partitions? I forget.

---

### Post by alphageek89 on 2010-02-24
Initially i had 3 50 gb partitions. I basically broke up the 3rd partition and split it into 15gb,15gb,20,1gb(swap)

is there any way i can seperate the /dev/sda10 partition coz its recognizing it as a chunk of 100 gb which i dont want.

---

### Post by cong06 on 2010-02-24
> **alphageek89 said:**
> is there any way i can seperate the /dev/sda10 partition coz its recognizing it as a chunk of 100 gb which i dont want.

Well, it's probably a good idea to paste a full printout of your disk:
```

fdisk -l

```

But probably you could just delete it **if you're absolutely sure you don't need it** and resize the other partitions to use up that space. (assuming I understand your question)

---

### Post by alphageek89 on 2010-02-24
Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x97be5b6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6774    51211408+   7  HPFS/NTFS
/dev/sda2            6775       20673   105076409    5  Extended
/dev/sda5            6775       13548    51211408+   7  HPFS/NTFS
/dev/sda6           13549       13562      105808+  83  Linux
/dev/sda7           13563       13701     1050808+  82  Linux swap / Solaris
/dev/sda8           13702       15733    15360000   83  Linux
/dev/sda9           17765       20673    21992008+   7  HPFS/NTFS



/dev/sda10 is not showing since i have deleted the partition and has not fs on it.


All i want is to install a solaris2 partition on it which when booting from a  solaris live cd is just recognizing /dev/sda1(as a 50 gb) and /dev/sda2(as a 100 gb)

---

### Post by cong06 on 2010-02-25
> **alphageek89 said:**
> All i want is to install a solaris2 partition on it which when booting from a  solaris live cd is just recognizing /dev/sda1(as a 50 gb) and /dev/sda2(as a 100 gb)

Could you clarify? Are you saying that you want the install of Solaris to only see a /dev/sda1 and /dev/sda2 after you install?
Or are you saying that when you put the CD in that's all you see?

Answer to the first: Impossible... and not really very practical/useful...
Answer to the second: I can't really speak on that as I haven't tried to install Solaris.

---

### Post by NefariousNobo on 2010-02-25
If what I think is the matter is the matter, I've had that problem as well when dual-booting Solaris and other operating systems. The name for that type of partition is an Extended Partition, and an Extended Partition can contain multiple Logical Partitions (allowing you to have more than the otherwise-maximum four Primary Partitions). As an Extended Partition takes up one of the four Primary Partition spaces, Solaris recognizes it as one Partition, and won't let you do anything to the Logical partitions individually, only the Extended partition as a whole. You can shrink some of the Logical Partitions and, possibly, make a new one but force it to be Primary (unless you already have the maximum number of partitions) which Solaris would then recognize as separate.

---

### Post by alphageek89 on 2010-02-26
> **NefariousNobo said:**
> If what I think is the matter is the matter, I've had that problem as well when dual-booting Solaris and other operating systems. The name for that type of partition is an Extended Partition, and an Extended Partition can contain multiple Logical Partitions (allowing you to have more than the otherwise-maximum four Primary Partitions). As an Extended Partition takes up one of the four Primary Partition spaces, Solaris recognizes it as one Partition, and won't let you do anything to the Logical partitions individually, only the Extended partition as a whole. You can shrink some of the Logical Partitions and, possibly, make a new one but force it to be Primary (unless you already have the maximum number of partitions) which Solaris would then recognize as separate.

I think this is what is happening in my case.I will shrink a primary partition.Thanks!

---

