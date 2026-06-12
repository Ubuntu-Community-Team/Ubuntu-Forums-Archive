---
title: "ubuntu reads the free space on my drive incorrectly"
date: 2010-10-11
forum: General Help
---

### Post by BcRich on 2010-10-11
hi
i'm using ubuntu 10.04 and it seems to read the size of my hard drive differently from different applications and i'm concerned that i'm not getting a clear indication of how much free space is actually available on the drive. for example the drive i am talking about is my main drive with ubuntu installed on it. Ubuntu is the only OS on it and it is Ext4. it is also western digital caviar black and 500GB.

in **GParted** the drive is read as  being 465.76 GiB with two partitions that ubuntu autamatically creates upon installation 
/dev/sdb1 ext4(file system) 460GiB (Size) 75.46GiB (used) 384.55GiB (unused)
/dev/sdb2 extended(file system) 5.75GiB
as you can see this adds up to 465.76GiB (approximately)
however in Disk Utility this information is different (and also more accurate to what i would expect it to be, knowing approximately how much data i have on the drive)

**Disk Utility** reads
Capacity 500GB
the drive is partitioned into two (as is to be expected) 
/dev/sdb1 ext4 version 1(Type) 494GB (capacity)
/dev/sdb2 extended (Type) 6.2GB (capacity)
as you can see this roughly adds up to 500GB, which is the correct reading 

**Nautilus** on the other hand tells me i have 361GB available on the drive, which does not comply with either one of the other readings. this means that if the drive is 500GB (which it is) i would have used approximately 140GB for nothing more than an operating system (ubuntu) and additional software that i've installed for ubuntu, none of which are greater than a couple of Megs in size each! 

recently i deleted about 40GB of data as root and Nautilus did not seem to update the free space that is available reflecting this. i think this is probably were the problem might be, perhaps?

i've looked around for disk checking utilities like fsck and fdisk but have not found anything yet online that relates how to use these tools to solve my problem. 
does any one have any suggestions?
thank you very much for your help.

---

### Post by Peter09 on 2010-10-11
While not an expert on this I can take you some of the way. The file system itself (ext4, ext3 etc) allocates some space to itself, this is for it to store temporary log files and transient data. Some utilities such as gparted will report this a free space (assuming there is no temporary data there), other utilities will understand that this is not 'user' space and not count it in the tally of free space - thats about all of my knowledge of this subject exhausted.

---

### Post by BcRich on 2010-10-11
hi Peter09
thanks for the reply :) 
i'm certainly no expert either, but was under the impression that the partition that is created as "extended" and "linux swap-space" is used for what you are referring to? ie the space not available for casual user usage but reserved for system usage. 
according to this thread [http://ubuntuforums.org/showthread.php?t=561202](http://ubuntuforums.org/showthread.php?t=561202) this space is 10% of the drive's total size.  this does roughly work out when you look at the extended partitions through both GParted and Disk Utility as they are roughly the same size 
GParted 5.75GiB
Disk Utility 6.2GB
these sizes are pretty much the same just measured in different quantities, and are approximately 10% of the total drive size. This, i think, is correct and a predictable allocated quantity for the extended partition (imho).
But even when taking these values into consideration GParted still displays my drive as only being a total of 465.76GiB with 384.53GiB free and in Nautilus it's slightly less 361.5GB free. where as in Disk Utility the total Drive size is 500GB (which i'm pretty sure it is).
i'm confused as to which one is actually reflecting the true amount of free space available on my drive?
also the approximate 40GB that i deleted from my drive, but did not get reflected as freed space through Nautilus, would if added to the total ext4 partition which GParted lists as 460.00GiB would bring up the tally of total drive space to roughly what it should be ie. approximately 500GB. 
do you or anybody, perhaps know if this is just merely co-incidence or if there is a problem with the way my free space is being tallied within Nautilus and GParted and finally if there is a utility that can fix this?
thanks again for your reply, i really do appreciate your help :)

---

