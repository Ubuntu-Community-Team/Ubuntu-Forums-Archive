---
title: "Partition My Drive"
date: 2010-03-02
forum: General Help
---

### Post by FinalShot on 2010-03-02
I want to partiton my hdd so I can dual boot XP SP3 & Ubuntu 9.10. Currently I just made 1 partition (NTFS) on 1 320GB hdd. And I need to make a partition for ubuntu.

Any good tutorials for this? Also I'd rather not have to use 3rd party tools for this.

And just a quick question, after I do this, will the files be sharable between the 2 os's. Provided the file type can be used in both.

---

### Post by tom4everitt on 2010-03-02
The most common solution to this is the following:

You have 3 partitions: 1 for windows, 1 for ubuntu, and one for all your files.

Assign for example 20gb each for the ubuntu and the windows partition, and the rest to the data partition. 

The table would look something like this:

1. Windows, 20gb, NTFS
2. Ubuntu, 20gb, ext4
3. Data, 260gb (or whatever is left), NTFS

Then you can access the data partition from both systems.

---

### Post by zvacet on 2010-03-02
[Here]("https://help.ubuntu.com/8.04/switching/dualboot-concepts.html")

---

### Post by tom4everitt on 2010-03-02
To do the actual partitioning:

Boot from your ubuntu live cd and use gparted. You can start it from a terminal (in the live cd) with:

sudo gparted


Also, one last note, install windows xp first and then ubuntu. Otherwise windows might mess up your boot loader (which is certainly fixable, but leads to extra work).

---

### Post by tom4everitt on 2010-03-02
> **zvacet said:**
> [Here]("https://help.ubuntu.com/8.04/switching/dualboot-concepts.html")

Allright, why reinvent the weel :)

---

### Post by FinalShot on 2010-03-02
Ok thanks.

But atm the moment, I have xp installed on 1 partition with some files, can I split xp and the files up?

---

### Post by FinalShot on 2010-03-02
No one?

---

### Post by dabl on 2010-03-02
> **FinalShot said:**
> Ok thanks.

can I split xp and the files up?

Not with a disk partitioning tool.  Just shrink the XP/NTFS partition, using GParted, but don't squish it to where it has no free space.  Then use the space you have freed up to make your Linux partitions.

When you have Ubuntu installed, you'll be able to copy your data files over to your data directory.

Best to back up all your important data before doing hard drive partitioning -- errors can happen.  ;)

---

### Post by FinalShot on 2010-03-02
Ok that's clearer thanks, though just to be sure.

Shrink the Xp partiton with some free space 2GB?

Create a partition for ubuntu ext4 file system how big?

Install ubuntu on that partition

Create another partition for my files, then copy over my files from the xp partiton.

That correct?

---

### Post by FinalShot on 2010-03-02
Also real quick, I have a 64bit capable CPU, but only 2GB ram, I guess there is no point going 64bit is there?

---

### Post by dabl on 2010-03-02
You can use 64-bit -- the RAM size is irrelevant to that.

On your partitioning, (and given 2GB of RAM) you really should include a swap partition.  Make it 2.2GB, and you'll be able to suspend to disk.

So:

1. Shrink the existing XP partition so there's a couple of GB of space left on it.

2. In the empty unallocated space, make 3 more partitions:

- 8GB for the root filesystem (format ext4)
- 2.2GB for swap space (format "Linux swap")
- all the rest of it for a data partition. (format ext4)

---

### Post by FinalShot on 2010-03-02
Ok great.

---

### Post by dabl on 2010-03-02
BTW, have you booted the Live CD on that hardware, and tested such things as networking/Internet, and audio?  It's good to beat it around a little in Live CD mode before you install it, just in case there's some "deal killer" hardware issue.

---

### Post by zvacet on 2010-03-02
@ **FinalShot**

Use 32 bit Ubuntu version.

> You can use 64-bit -- the RAM size is irrelevant to that.

I don´t think this is truth,but I can be wrong.Reason for using 64 bit version is ram ,but if you are going to install Karmic you can install linux-image-generic-pae and you will be able to see and use all your ram.But that is not your case,because you have only 2GB of ram.I will partition this way ( I don´t know how much free space do you have so this is just example):

1.root=10GB      ext4
2.home=this in your case depends.On home partition you will have settings and data and in general this is biggest partition.But you want to have shared one so maybe you can give 10GB to home and format as ext4.

3.swap= 2GB

4.shared= rest of free space and format as NTFS because Windows can not see ext4 AFAIK.

---

### Post by dabl on 2010-03-03
Maybe "irrelevant" was too strong, but the amount of installed RAM should NOT be the deciding factor when considering whether to install the 32-bit or 64-bit architecture:

[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/69585-should-you-choose-32-bit-64-bit-linux.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/69585-should-you-choose-32-bit-64-bit-linux.html)

[http://www.linux.com/archive/articles/114024?tid=121](http://www.linux.com/archive/articles/114024?tid=121)

[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

As it says, there are many other considerations.  The 64-bit Live CD is a very useful way to evaluate whether there are any hardware issues on YOUR system.  64-bit will run just fine on any size of RAM that you can run the 32-bit OS on, and up to 256 terabytes or some such **irrelevant** number.  :)

---

