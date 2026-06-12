---
title: "change partition to create more space for ubuntu"
date: 2009-10-01
forum: General Help
---

### Post by tvkpz on 2009-10-01
Hi

I have a dual boot system with win xp and ubuntu 9.04.

I just realized that I need to allocate more space to ubuntu to get some softwares installed. 

Here is what Gparted shows me when I check for the partitioning

Partition       File System    Mount Point     Label        Size        Used        Unused      Flags
/dev/sda1    fat16                                 Dell Utility   31.35MiB  7.23 MiB  24.12MiB
/dev/sda2    ntfs              /media/disk                     40GiB      22.81GiB  17.19GiB    boot
/dev/sda3    ntfs              /media/DATA                   77.19GiB  2.24GiB   74.96GiB
/dev/sda4    extended                                            31.78GiB
/dev/sda5    ext3             /                                     10.0GiB    8.4GiB     1.6GiB
unallocated  unallocated                                          20GiB
/dev/sda6    linux-swap                                           1.78GiB

As you can see I have an unallocated partition and I am probably using /dev/sda5 for my ubuntu. Any advice on how I can use the unallocated space and add to my present partition /dev/sda5.

I am new to this. Can anyone explain what is /dev/sda4 do and /dev/sda6 indicating. Is it also free space that I can use. I know that ntfs indicates the windows partitions so I am not going to touch that one. I previously had Fedora installed in thos computer and the linux-swap partition is from that time onwards. I never touched it and installed Ubuntu in /dev/sda5. Any help on how I can organize my partioning to give myself more space on ubuntu. I am looking at the GParted GUI interface. 

I am new with this so I do not want to mess up. Thanks in advance for your advice.

---

### Post by Muscovy on 2009-10-01
It looks like you've got logical partitions. For some reason you can only have 4 "real" ones, so logical partitions is how you get past it. That seems to be what sda4 is. sda5 is your actual Ubuntu section, and sda6 is the swap space (basically hard drive space for if you need more ram).
  Is the unallocated block part of sda4? I thnk you made a mistake, because the numbers don't add up to me.

---

### Post by rreese6 on 2009-10-01
Here you go. sda4 is the extended partition.
Logical drives are created within extended partitions.
because 4 primary partitions is all that are allowed (as previous post explained). Since Ubuntu is on sda5 is it inside of sda4, basically.
to expand the size for sda5 you must fist expand sda4, then make sda5 larger.
I would do it as two steps.
make sda4 grab all the unalloted space. hit Apply
then expand sda5 Hit Apply.
Be happy!

---

### Post by egalvan on 2009-10-01
> **rreese6 said:**
> sda4 is the extended partition.
Logical drives are created within extended partitions.
Ubuntu is on sda5 is it inside of sda4,.
to expand the size for sda5 you must fist expand sda4, then make sda5 larger.
I would do it as two steps.
make sda4 grab all the unalloted space. hit Apply
then expand sda5 Hit Apply.
Be happy!

the un-allocated space appears to be inside sda4.

if so, there is no need to expand sda4. It already has the space inside it.

Just use the "re-size" option in gparted to move the right side of sda5 all the way to the start of 'swap'.

Also, remember that you cannot work on mounted partitions,
so you must use a LiveCD to do this work.

Either the LiveCd you used to instlal Ubuntu,
or download PartedMagic LiveCD (recommended)
which always has the latest gparted.

boot with PartedMagic, then run the disk partitioner (gparted)
to check the partitions.


And finally, if you want more assurences, 
then attach a screenshot of gparted showing the drive.
and run
```
sudo blkid
sudo fdisk -l
```
paste the output in the same post.

---

### Post by tvkpz on 2009-10-01
Hi

I am attaching the screen shot of GParted in case I miscommunicated anything by the text write up of the output.

egalvan: Does your advice still remain the same or is there anything easier to do.

Thanks a lot!

---

### Post by louieb on 2009-10-01
> **tvkpz said:**
> ...Does your advice still remain the same or is there anything easier to do...

Doesn't get any easier. There is unallocated space and its in the right place. 

Follow egalvan's advice and your good to go. - Just remember you will need to run Gparted after booting with a Live CD.

---

### Post by drs305 on 2009-10-01
If gparted doesn't let you perform the operation, don't forget to turn off swap by highlighting the swap partition. Select the swap partition and then Partition, Swapoff.

It doesn't look like you will need it at this point, but here is a guide about resizing the / partition that offers some pointers:
[ Expanding an Ubuntu System Partition  ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

