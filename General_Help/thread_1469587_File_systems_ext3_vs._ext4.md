---
title: "File systems: ext3 vs. ext4"
date: 2010-05-02
forum: General Help
---

### Post by FinnMan on 2010-05-02
):P Hi. I am new to Ubuntu, previously ran OpenBSD as a server, but haven't really delwed too deep into it, because it works out of the box. :) Which file system does Lucid Lynx use by default and where should I look to find Ubuntu technical information?

I've been looking into the differences between the various file systems on Linux and trying to decide, if I should have my data partitions in ext4, but I don't really need nanosecond-precision for my file dates. :D

Also, the delayed allocation may pose problems, but it should improve speed and avoid fragmentation. Although, it can probably be turned off? I also learned that ext3 doesn't store creation dates for files! :?

I am still undecided and would welcome advice. Most of my files are pretty large, so block suballocation doesn't probably yield me a lot of gain. Is it possible or advisable/inadvisable to use ext4 for system partitions?

I'm slightly suspicious because ext4 is rather new and it stores more metadata leaving less space for actual data... Then again, if it's good enough for Google, then it'll probably do for me too. ;)

---

### Post by llamabr on 2010-05-02
ext4 is pretty new, and still messing up a bunch of people's stuff.

if you're not sure why you need ext4, then ext3 is still probably good enough for you.

---

### Post by cascade9 on 2010-05-02
I use EX4 for /, but EXT3 for /home and my data partitions. Sooner or later I'll probably move /home to EXT4. I'd really rather have my data partitions in a safer filesystem, even if it does mean its slightly slower than the newer EXT4. 

When BTRFS is stable, and mature, I will probably move my data filesystem over to that, not EX4.

---

### Post by Pjotr123 on 2010-05-02
> **llamabr said:**
> ext4 is pretty new, and still messing up a bunch of people's stuff

Nonsense. EXT4 is quite stable nowadays, even stable enough for the default file system of an LTS version like 10.04.

EXT4 is the better choice, because it's faster and more advanced than EXT3. Not drastically different from EXT3, either. It's simply the successor of EXT3, based on it's predecessor. Some incremental improvements, nothing revolutionary.

---

### Post by sarthorks on 2010-05-07
is there no problem in using different filesystems for different partitions.
Eg. i want to format my 8.04 root and install 10.04 there. Suppose i use ext4 for /; but i keep my /home partition ext3 only. Is that fine? or there will be problems?

---

### Post by StuartN on 2010-05-07
> **sarthorks said:**
> is there no problem in using different filesystems for different partitions.

No, none at all, certainly EXT3 is fine for /home.

As far as EXT4 and EXT3 go, real world benchmarks are not conclusive, with use cases where EXT3 is better than EXT4, and there is no overall faster choice.

(For instance this Phoronix benchmark report: [http://www.phoronix.com/scan.php?page=article&item=linux_2632_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2632_fs&num=1))

---

### Post by mb_webguy on 2010-05-07
The only problem with using a mix of different filesystems is that if you use a filesystem like FAT or NTFS that doesn't support linux file permissions then the partition has to be mounted with a fixed set of permissions that applies to the partition as a whole.  But as long as the filesystems support linux-style permissions, it doesn't matter if you're using a dozen different partitions with different filesystems.  Your / could be ext3, your /home could be ext4, your /var could be reiserfs, etc., and it wouldn't matter a bit.

---

### Post by jis on 2010-05-08
> **Pjotr123 said:**
> Nonsense. EXT4 is quite stable nowadays, even stable enough for the default file system of an LTS version like 10.04.

EXT4 is the better choice, because it's faster and more advanced than EXT3. Not drastically different from EXT3, either. It's simply the successor of EXT3, based on it's predecessor. Some incremental improvements, nothing revolutionary.

dpkg runs slower on ext4 than on ext3 according to [ubuntu 10.04 release notes]("http://www.ubuntu.com/getubuntu/releasenotes/1004#Performance%20regressions%20with%20ext4%20under%20certain%20workloads").

---

### Post by FinnMan on 2010-05-10
Thanks for all the input. I was hoping for a clear answer, so I wouldn't have to think myself. ;) I believe ext4 became officially stable in late 2008, so I'd expect it to kinda work, but I am skeptical.

I will have a lot of data and I have not yet even decided if I will keep it under Windows, where it is now, and in any case, I will have a full backup, so a disaster would not be catastrophic. :)

I did fight with Windows for almost an hour today, had to reset twice, and still in the end was unable to get the job done. It's just an incredible pile of ... well, you know. Journaling should make ext4 reliable?

---

### Post by jappie on 2010-06-30
> **mb_webguy said:**
> The only problem with using a mix of different filesystems is that if you use a filesystem like FAT or NTFS that doesn't support linux file permissions then the partition has to be mounted with a fixed set of permissions that applies to the partition as a whole.  But as long as the filesystems support linux-style permissions, it doesn't matter if you're using a dozen different partitions with different filesystems.  Your / could be ext3, your /home could be ext4, your /var could be reiserfs, etc., and it wouldn't matter a bit.

I'm new to Ubuntu and just took the big step to erase XP and do a clean install of 10.04 netbook remix on my Acer AspireOne. Almost everything seems to be working ok (so far.....3hrs after installation and still testing!) except  for: 
1: My main partition is formated as ext4, but when I try copy back any (video .iso) file that is larger than 4.1 gb I get a memory error and so only copies the file incomplete up to 4.1 gb .....
I know this problem under windows FAT vs NTSF but I have read that ext4 was beyond this...So what did I do wrong?
Is the solution to swith the ext4 to ext3 and can this be done without loss of installed programs or files. 

2: my micophone is not working in Skype but it does with Sound-Recorder...I know is probably a different forum but just mentioning it hoping to a refering solution )

Pura Vida!
Jappie

---

### Post by mb_webguy on 2010-07-04
Memory isn't the same as storage.  If you're actually getting a *memory* error, then you have insufficient memory/swap.  OTOH, if the error says something about insufficient *space*, then that pertains to the amount of storage remaining on the partition.  And I don't know what the specific error would be if you hit the filesize cap for a particular filesystem, but ext4 supports file sizes up to 16TB, so... yeah.

---

