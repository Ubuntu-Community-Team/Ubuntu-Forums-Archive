---
title: "FAT32 formatted external drive ONLY works with ubuntu"
date: 2012-02-05
forum: General Help
---

### Post by Willberto on 2012-02-05
So I underwent a series of unfortunate hard drive and computer failures in the past couple months which has basically forced me to consolidate all my files onto a 1TB external drive which I formatted using Ubuntu (which turned out to be a terrible mistake) 700GB of files in all

This drive will not work on ANY windows machine or operating system and appears under "unallocated space" in Windows7 even though the drive is recognized.

I tried a couple repair utilities which didn't do anything and I don't want to go too far out of fear of losing my data. So my only solution is to try and fix an old desktop, install ubuntu, fill it full of whatever working hard drives I can find, transfer via USB 700GB of files to it, reformat using windows, move all the files back to the external than all the files onto my new laptop. I suspect this will take a day and a half of continuous effort unless someone can think of a better solution.

With unity and all these other problems I've been having with ubuntu I've become disappointed with the whole thing. I actually stopped recommending it to friends the moment unity came out because I could no longer hand it to them and say "here, you already know how it works" and if I go to try and help them, I don't even know how to because I cannot find the necessary utilities, in the menu, I have to type into command line or the search bar which doesn't really work unless you already know what you're looking for (QED for new users). Anyway, as one could probably tell, I'm frustrated.

---

### Post by xyzzyman on 2012-02-05
Could you perform a 

```
sudo fdisk -l
```

while booted on an Ubuntu LiveCD or install with that HDD plugged? And post the contents here? Make sure to place within code tags so it's easy to read.

Also, Windows Vista/7 Disk Management will only show FAT32 partitions up to 32GB's. Depending on how it was formatted it can read/write to FAT32 up to 2TB's but not always.

---

### Post by Willberto on 2012-02-05
Thanks for the help, here's the results of the command
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00076ada

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   970532863   485265408   83  Linux
/dev/sda2       970534910   976771071     3118081    5  Extended
/dev/sda5       970534912   976771071     3118080   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a38bee2

   Device Boot      Start         End      Blocks   Id  System

```

---

### Post by xyzzyman on 2012-02-05
Either there are no partitions on that external HDD or you didn't copy paste everything.

---

### Post by Willberto on 2012-02-05
I noticed that too, I did copy and paste everything. If I go to disk utility it tells me it's FAT

---

### Post by xyzzyman on 2012-02-05
Then you need to try to take a screenshot of gparted. It's on livecd's, but not installed by default. So

```
sudo apt-get install gparted
```

And in the upper right switch to /dev/sda2. Take the screenshot with Alt+Printscreen so it takes it just of the gparted window. Then add it as an attachment to your reply.

---

### Post by oklokl on 2012-02-05
usb Chipset bug.

or..

Partition death

testdisk > tools > Recovery
[http://www.youtube.com/watch?v=EncqYP1ijFg](http://www.youtube.com/watch?v=EncqYP1ijFg)

---

### Post by Willberto on 2012-02-05
gparted is showing sdb as having 931.51GB of unallocated space. I could screenshot but that's the only info available

---

### Post by Willberto on 2012-02-05
I should clarify that when I plug the drive in it comes up as an external drive and I can edit and move files as normally.

---

### Post by xyzzyman on 2012-02-05
Yup. It's corrupt. You're lucky that Ubuntu can even see it. Testdisk is more if Ubuntu couldn't even see it. You could try fixing the partition table but you need to backup the data first anyways. What sort of data do you have that's 700GB's? Take lots of RAW files with a DSLR or edit raw video?

---

### Post by Cheesemill on 2012-02-05
Your issue is probably beyond this now as it looks like you've managed to screw up your partition table somehow, but you can access files on a Ubuntu drive using windows, you just needed to install this:
[http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html](http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html)

---

### Post by Willberto on 2012-02-05
It's been like this since I got it and formatted it I guess. I brought it over to a friend's house and it wouldn't shop up on his computer either. I think it was created like this.

---

### Post by xyzzyman on 2012-02-05
> **Cheesemill said:**
> Your issue is probably beyond this now as it looks like you've managed to screw up your partition table somehow, but you can access files on a Ubuntu drive using windows, you just needed to install this:
[http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html](http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html)

He already said he formatted as FAT32. Unless he formatted as an extX inadvertently that utility wouldn't have worked.

You could try to see what the output of a 'mount' command gives you and paste it here. It'll show us what format and partition # it's somehow pointing to.

---

### Post by Willberto on 2012-02-05
Anyway, thanks, I'm working on plan A. It would appear my house is a haunted black hole of computer destruction and error.

Went to do a restart of my Windows laptop... "please do not turn off or unplug.... installing updates 1 of 43" arrrrgggghhHHHH!!! 

rage

---

### Post by mac67 on 2012-02-05
> **Willberto said:**
> So I underwent a series of unfortunate hard drive and computer failures in the past couple months which has basically forced me to consolidate all my files onto a 1TB external drive which I formatted using Ubuntu (which turned out to be a terrible mistake) 700GB of files in all

This drive will not work on ANY windows machine or operating system and appears under "unallocated space" in Windows7 even though the drive is recognized.

...



In my opinion (I am not a Linux expert) your hard drive is not at all corrupted if you can access it from Ubuntu. Since you formatted it with Ubuntu, you have probably formatted it as ext4 or ext3 filesystem. Windows sees only NTFS filesystems. Just a wrong formatting choice.

Transfer everything somewhere and format the hard drive again, I do not see other easy solutions.

---

### Post by xyzzyman on 2012-02-05
> **mac67 said:**
> In my opinion (I am not a Linux expert) your hard drive is not at all corrupted if you can access it from Ubuntu. Since you formatted it with Ubuntu, you have probably formatted it as ext4 or ext3 filesystem. Windows sees only NTFS filesystems. Just a wrong formatting choice.

Transfer everything somewhere and format the hard drive again, I do not see other easy solutions.

Then gparted and fdisk would show it as an ext4 or ext3 filesystem and not show unallocated and blank respectively. I used to use damn small linux all the time to do data recovery on fat32 and ntfs partitions that no other OS would even recognize existed. It's possible he originally formatted it in ext3/4, but somewhere's while trying to get it to work it's corrupted to the point that Ubuntu doesn't even see the partition table as correct anymore.

Windows 7 also would show the partition as an unknown type, not as unallocated.

---

