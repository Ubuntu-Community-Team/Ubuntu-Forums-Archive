---
title: "Best way to partition a shared hard drive for data and programs?"
date: 2011-12-08
forum: General Help
---

### Post by natpat on 2011-12-08
I'm currently running Ubuntu (and will soon be dual booting windows) off a 64GB SSD - however, I have a 1TB hard drive which I wish to use for programs and data. The disk will be used equally by Windows and Ubuntu - what is the best way for me to partition my 1TB hard drive?

---

### Post by searchfgold6789 on 2011-12-08
If you're going to install windows on the 1 TB, and install Ubuntu on th 64 GB, and use the 1 TB for programs and other data for ubuntu, I would split the 1 TB cleanly in half. You can always change it later. Just put the Ubuntu data on the first partition and Windows on the second, because the Ubuntu filesystem will be easier to shrink and the Windows partition will be easier to grow ;)
I would put /home, /usr, and /boot on the 1 TB for sure but beyond that I don't know much about the linux file structure.

---

### Post by natpat on 2011-12-08
> **searchfgold6789 said:**
> If you're going to install windows on the 1 TB, and install Ubuntu on th 64 GB, and use the 1 TB for programs and other data for ubuntu, I would split the 1 TB cleanly in half. You can always change it later. Just put the Ubuntu data on the first partition and Windows on the second, because the Ubuntu filesystem will be easier to shrink and the Windows partition will be easier to grow ;)

I was planning to have windows on the SSD as well hopefully, but if that wouldn't be a good idea then I'll go with that. For the file systems I'm assuming ext4 for the ubuntu data and ntfs for windows?

---

### Post by searchfgold6789 on 2011-12-08
Well, by all means, if you're putting Windows on the 64 GB SSD as well, then you're putting Windows on the SSD as well :D I know I said to put boot on the 1 TB, but in reality it would Ideally be put on the first partition of the hard disk you're booting from. To answer your other question and put things in better perspective I will make a simple text chart below:
64 GB:
{Ubuntu 32 GB ext4} {Windows 32 GB ext4}
1 TB:
{Ubuntu with /usr /home and maybe /boot, 500 GB ext4} {Windows 500 GB}

Now, a disclaimer:

[LIST]
[*]If you want to take full advantage of having all your programs run faster, you may consider keeping you /usr on the solid state drive. This will also use more disk space.
[*]If you are using Windows more than Ubuntu, you may want to alter the sizes of the partitions to allow for that, and same with Ubuntu.
[*]Use ext4 for Ubuntu and of course NTFS for Windows.
[*]Your swap partition should be kept on the SSD.
[*]You should install Windows first, then Linux. It's easier that way.
[/LIST]
 - search

---

### Post by ezsit on 2011-12-08
Yet one more opinion:

64GB SSD

/boot   -- ext3 -- 500MB
C:      -- NTFS -- 30GB
/       -- ext4 -- remainder of drive

1.00 TB

2GB   --  Linux Swap Space -- primary partition
498GB --  Windows NTFS -- primary partition
498GB --  Extended Partition containing:
          /usr - logical volume - ~15GB
          /var - logical volume - ~15GB
          /tmp - logical volume - ~15GB
          /home - logical volume - ~Remainder of drive

The reason to put /var and /tmp on the hard drive is these directories will have constantly changing data - lots of read/write cycles and better not left on a SSD. /usr will need space to grow as you add programs and Linux swap space should be obvious. /etc might be another candidate for the hard drive rather than the SSD, but this probably isn't as important as /var and /tmp.

---

### Post by dFlyer on 2011-12-08
> **natpat said:**
> I'm currently running Ubuntu (and will soon be dual booting windows) off a 64GB SSD - however, I have a 1TB hard drive which I wish to use for programs and data. The disk will be used equally by Windows and Ubuntu - what is the best way for me to partition my 1TB hard drive?

Will windows and linux os be on the ssd or just windows and is just the 1tb drive going to be used for data?

---

