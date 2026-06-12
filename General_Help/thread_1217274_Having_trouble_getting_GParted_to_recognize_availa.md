---
title: "Having trouble getting GParted to recognize available space"
date: 2009-07-19
forum: General Help
---

### Post by Ownager on 2009-07-19
I have a small problem with gparted. I run Live Ubuntu cd. I am trying to put sda2 into sda1. But it refuses to accept to have more space. I unmounted sda1. I can't increase anymore space for sda1. 

It should be 250 GB Media instead 

200 GB Media 

50 GB Media

Let me upload a screenshot here. 

And I want to mount sda1 again. Please write back and thanks

---

### Post by Cheesemill on 2009-07-19
You just need to delete sda1 then expand sda2 to take up all of the free space.

---

### Post by credobyte on 2009-07-19
Oh, sorry .. seems that you've some data on sda2 ! Well, as previous said - delete sda1 and resize sda1 :)

---

### Post by Ownager on 2009-07-19
sda2 got junk stuff. I used write from testdisk. That's why sda2 got stuff. It's really useless. I am scared of deleting sda2 because delete probably cause "small gb" or something like that.

---

### Post by Cheesemill on 2009-07-19
You are going to have to delete one of the partitions to create free space to expand the other partition into.
 
What is "small gb" ???

---

### Post by credobyte on 2009-07-19
Then delete your sda2 and resize sda1 - gParted is awesome, you can design your layout without changing it ( you need to press Apply to take changes ) :) Don't be so scared - you'll can't ( obviously :D ) lose your space because of partitioning.

---

### Post by Ownager on 2009-07-19
Yeah I did it but I got an error like this. 

I can't grow it...

---

### Post by Cheesemill on 2009-07-19
You need to click on the arrow next to Grow so we can see the error details.

---

### Post by credobyte on 2009-07-19
Delete both partitions/disks and create a new one, allocating 100% space to it ( that's what I would do ).

---

### Post by Ownager on 2009-07-19
Ok here it is. You can look at this error. I forgot to open arrow next. You can see error3.png. It shows you more now.

---

### Post by louieb on 2009-07-19
Did I get this right you want to put 1 big partition on th drive?  And any data on the drive is garbage to be discarded?

Then select Device>New disk label - put a msdos (default)  label.

This will write a blank partition table to the MBR. The disk will show up as blank (no partitions) and you  add a new partition - taking up the whole space.

---

### Post by Ownager on 2009-07-19
I put error3.png now. You can click on page 1 and find error3.png. I just added it now. I forgot to open arrow next.

---

### Post by Cheesemill on 2009-07-19
As credobyte and louieb said, if you don't have anything you need to keep on either partition then just delete both of them and create a new partition from scratch.

---

### Post by Ownager on 2009-07-19
ok you meant you want me to delete sda1 and sda2 and then resize sda1 to full size. I can make it as ntfs. right?

---

### Post by raymondh on 2009-07-19
> **Ownager said:**
> ok you meant you want me to delete sda1 and sda2 and then resize sda1 to full size. I can make it as ntfs. right?

When you delete SDA1 and sda2, you have nothing else to resize.  That is why they are saying (since you have no data you wish to save) to start from scratch after deleting both partitions.

---

### Post by Ownager on 2009-07-19
I am not sure about scratch. I am using chkdsk /r now. I am following this error details.

---

### Post by Seq on 2009-07-19
Yes, do follow the instructions in the error message (chkdisk, etc). Also note that I would not trust a disk with bad sectors. If I were you, I'd toss the disk and get another.

---

### Post by Ownager on 2009-07-19
I would just format sda1 with ntfs. Then I think I can resize it. Problems will be less instead of having bad sectors.

---

### Post by Ownager on 2009-07-19
It works successful now. Let's see if it's a perfect size while I install an operating system.

---

### Post by Ownager on 2009-07-19
Strange... The operating system says it's C: Partition1 (Unknown) 32254 MB (32254 MB free)

Is this normal?

I already made it to be 232.88 GB total.  Hard Drive shows "250 GB". I already put from sda2 into sda1. It works successful. Now the operating system I am going to install says 32254 MB (32254 MB free).

---

### Post by raymondh on 2009-07-19
> **Ownager said:**
> Strange... The operating system says it's C: Partition1 (Unknown) 32254 MB (32254 MB free)

Is this normal?

I already made it to be 232.88 GB total.  Hard Drive shows "250 GB". I already put from sda2 into sda1. It works successful. Now the operating system I am going to install says 32254 MB (32254 MB free).

Are you questioning why you only have 232 GB and the HD is supposed to take 250GB?  If so, short answer is the multiplier 1024. Storage formats use the SI definition of 1kb = 1000 bytes.  But, OS' use the binary definition of 1kb = 1024 bytes.

---

### Post by Ownager on 2009-07-19
Numbers on Hard Drive says 250 GB. It normally reduces from that to 232.88 GB. 

But it's strange to see C: Partition1 (Unknown) 32254 MB (32254 MB free)


I saw 232.88 GB in gparted. Now it shows 32254 MB. I wonder if it's normal.

---

### Post by Ownager on 2009-07-19
Oh man I installed the operating system. Now it says 

> Couldn't open drive multi(0)disk(0)rdisk(0)partition(1)

NTLDR: couldn't open drive multi(0)disk(0)rdisk(0)partition(1)

---

### Post by cariboo on 2009-07-19
Could you boot from the Live CD, once at the desktop open an Application-->Accessories-->Terminal and type:

```
sudo fdisk -l
```

that is a lower case L. Paste the output in your next post.

---

### Post by Ownager on 2009-07-19
ok I am going to give it a try. I hope it can load without this issue.

---

### Post by Ownager on 2009-07-19
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sda4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


I did sudo fdisk -l just now. Is there something wrong?

---

### Post by merlinus on 2009-07-19
What do you think?  Errors galore, unfortunately.

For example: This doesn't look like a partition table
Probably you selected the wrong device.

and partitions do not end on cylinder boundaries.

If you have data that you did not back up, you might try testdisk and photorec:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by louieb on 2009-07-19
> **Ownager said:**
> I did sudo fdisk -l just now. Is there something wrong?

Yes. At this point you got nothing to loose by writing a new partition table like I described ot post #11. Don't bother to partition or format just let the installer handle it. I guess you are trying to install windows on the drive. Is it a legal copy?

---

### Post by cariboo on 2009-07-19
As the previous poster said, your partition table is all screwed up, I don't think you can save anything.

It almost looks like you tried to edit the partitions while they were still mounted. the best thing to do would be to remove all the partitions and start from new.

Make sure you hard drive isn't mounted, If there is a hard drive icon on the desktop, right-click it and select unmount. then in the same terminal type:

```
sudo fdisk /dev/sda
```

You should get something that looks like this:

```
The number of cylinders for this disk is set to 30401.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help):
```

Press d to delete a partition. THe program should ask which parttition to delete. Choose 4 to delete partition 4 then press d to delete partition 3 and so on.

Once you have deleted all the partitions press w to write the new information to the partition table then press q to quit.

The above will completely remove any partitions, you should now be able to install XP and setup the partitions the way you want. Boot from the XP install disk, and when you get to the partition section create your partitions.

---

### Post by Ownager on 2009-07-19
Yeah, I already installed Windows XP. It doesn't load XP. 

I already write partitions through testdisk. It made sda1 into sda2 and unallocated. 

I was putting them back to sda1 from sda2 and unallocated today. I already copy all backups (pictures and stuff) 5 weeks. I am gonna let cariboo907 to look into this result from sudo fdisk -l.

---

### Post by Ownager on 2009-07-19
> **cariboo907 said:**
> As the previous poster said, your partition table is all screwed up, I don't think you can save anything.

It almost looks like you tried to edit the partitions while they were still mounted. the best thing to do would be to remove all the partitions and start from new.

Make sure you hard drive isn't mounted, If there is a hard drive icon on the desktop, right-click it and select unmount. then in the same terminal type:

```
sudo fdisk /dev/sda
```

You should get something that looks like this:

```
The number of cylinders for this disk is set to 30401.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help):
```

Press d to delete a partition. THe program should ask which parttition to delete. Choose 4 to delete partition 4 then press d to delete partition 3 and so on.

Once you have deleted all the partitions press w to write the new information to the partition table then press q to quit.

The above will completely remove any partitions, you should now be able to install XP and setup the partitions the way you want. Boot from the XP install disk, and when you get to the partition section create your partitions.

I chose 4. It said like this 

Warning: partition 4 has empty type

I am going to choose 3 and all of them next now. I hope it helps. I am following your instruction.

---

### Post by Ownager on 2009-07-19
> Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 2: No such file or directory.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

Do I need to restart my computer now?

---

### Post by cariboo on 2009-07-19
Yes, you won't have any partitions, so you'll have to reinstall windows.

---

### Post by Ownager on 2009-07-19
ok I am going to install it again. Be right back about 10 minutes. Let's see if it's successful for now.

---

### Post by Ownager on 2009-07-19
cariboo907, Thank you for solving this issue. It loads successful. But I don't understand why do I have 31.4 GB total size. 28.6 Free Space. 

It should be 383.88 GB instead of 31.4 GB. Do I have to resize sda1 again?

---

### Post by merlinus on 2009-07-19
If you can run from the ubuntu live cd, post results of

```
sudo fdisk -l
```

and a screenshot of gparted.

---

### Post by Ownager on 2009-07-19
ok I am going to put 4 pictures. 

You will see bad result at first. 

2nd picture will say It should be 232.88 GB

3rd It shows you an error. I already followed it. I rebooted it two times. I still get this same error. 

4th sudo fdisk -l shows a result.

---

### Post by cariboo on 2009-07-19
It looks like you have the full partition now. During the Windows installation when you get to the partitioning screen do you see the full size of the hard drive?

---

### Post by Ownager on 2009-07-19
I have done everything again. A bad news is that Windows XP installation forces me to use 32254 MB. I can't increase more than that to 232.88 GB. After I install it, I saw about 31.4 GB and 28.6 Free Space.

---

### Post by Seq on 2009-07-19
> **Ownager said:**
> I have done everything again. A bad news is that Windows XP installation forces me to use 32254 MB. I can't increase more than that to 232.88 GB. After I install it, I saw about 31.4 GB and 28.6 Free Space.

You are telling Windows to format the drive as NTFS, right? iirc, XP originally had the ability to install on FAT32 (though maybe only if you already had a FAT partition). FAT32's maximum size is 32GB.

Reading through the thread it is unclear if you are creating the partition in the Windows installer or with Linux and just formatting it from the Windows installer.

**EDIT**: I was partially incorrect. FAT32 can be larger, but Windows 2000/XP will not create one larger than 32GB for some reason.

---

### Post by cariboo on 2009-07-19
When you deleted all the partitions, you should have had an empty hard drive, are you saying that when you use the Windows partitioner, that it will only create 32Gb partition? As Seq said are you creating and NTFS partition or a vfat partition?

Some hard drives had a jumper to limit the size of the partition to 32Gb, could that be the problem?

---

### Post by Ownager on 2009-07-19
Windows XP needs ntfs. I run Live Ubuntu cd. I am trying to make it to be 232.88 GB instead of 31.4 GB. I made it as ntfs. You can see screenshots in my posts in here.

---

### Post by Ownager on 2009-07-19
> **cariboo907 said:**
> When you deleted all the partitions, you should have had an empty hard drive, are you saying that when you use the Windows partitioner, that it will only create 32Gb partition? As Seq said are you creating and NTFS partition or a vfat partition?

Some hard drives had a jumper to limit the size of the partition to 32Gb, could that be the problem?

I pressed D for delete on partition1 and then click on L. It's empty. I clicked C for creating a new partition. It says max size is 32254. I use ntfs. Should I test fat32?

---

### Post by cariboo on 2009-07-20
I wouldn't. Can you check your hard drive to see if is jumpered to only allow 32Gb partitions?

It is either that, or you BIOS has a 32Gb limit.

---

### Post by Ownager on 2009-07-20
I saw 33 gb in bios. I am gonna try smart extended self-test. Maybe it increases from that to 232.88 GB

---

### Post by cariboo on 2009-07-20
That won't make any difference. It looks like all the BIOS is capable of seeing is 32Gb. How old is your computer system?

---

### Post by cariboo on 2009-07-20
I have an older system out in my shop that had WinMe on it when I got it, I tried to put a brand new 80Gb hard drive in it the other day, it wouldn't even detect the drive.

---

### Post by Ownager on 2009-07-20
I only remember that I bought a pc right after Quake 4 was released. I had to upgrade everything for Quake 4. Quake 4 is a poor game. I don't like it very much. It's too easy for me to win. I like Doom 3 better. I play Quake 3 10 years. 

By the way, does gparted really change sda1's space after you add more, click on apply, and then click on quit from gparted or close gparted window? Do I have to mount it first? I am thinking about how to make it as 232.88 GB for real. Does fdisk /dev/sda affect sda1 into 31.4 GB?

---

### Post by cariboo on 2009-07-20
If your bios only shows 33Gb than thats all you are going to get, unless you use something ontrack emulation, or check and see if there is a bios update.

---

### Post by Ownager on 2009-07-20
Let's see with the result after using write from testdisk. Testdisk is almost done. I think it has a file for the hard drive's driver.

---

### Post by Ownager on 2009-07-20
I checked all results in testdisk. All these partitions are empty now.

---

