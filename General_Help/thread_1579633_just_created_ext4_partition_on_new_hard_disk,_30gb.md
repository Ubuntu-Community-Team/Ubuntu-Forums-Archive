---
title: "just created ext4 partition on new hard disk, 30gb already used?"
date: 2010-09-22
forum: General Help
---

### Post by fuzzylogic25 on 2010-09-22
Hi,

I have a weird issue here. I just purchased a new Hitachi 2TB hard disk and created an ext4 partition using GParted. Once it was created it said size was 1.82TiB (understandable, as its 1024MB per GB) but then used space was 29.42GiB!?!?

Why is that? 

Also then I opened the drive and found some folder called "lost+found" with an X marked on the folder. When I right clicked on the drive under the file browser in MEDIA and clicked PROPERTIES it then said that 93.3GB is used!!

What is going on? Does it take that much space to use an ext4 partition? This drive is intended to be just a data drive, it will not hold any operating systems.

---

### Post by elliotbeken on 2010-09-22
not quite sure.. hmm did you have files on the drive before you partitioned it? ..

i have seen files been put backon the drive after and not allowing you too see them!

try again but format the drive then create the partition.. this might help i hope it does...

(i have seen this happen before with a 256Mb memory card i have if i format it to FAT it is ok but if i format it to NTFS it will use 20-30mb of space.)

---

### Post by fuzzylogic25 on 2010-09-22
This is a newly purchased hard disk - so there is nothing on it at all.

I know what you mean about NTFS taking up 20-30mb but this is 30GB! and what i dont get is the inconsistency, why does GParted show 30GB used and under folder properties it shows 93GB used?

---

### Post by drs305 on 2010-09-22
The ext3 and ext4 filesystems reserve 5% of the the partition for system use, so the amount lost on a large drive seems about right. The 5% was set long ago when drives were much smaller.

You can adjust the % of reserved space with *tune2fs*:
```
sudo tune2fs -m /dev/sdXY
```
where *m* is the percentage and XY is the partition (example sda5).

See the man page for tune2fs for a bit more info.

---

### Post by fuzzylogic25 on 2010-09-22
ok thanks for that!

but what purpose would i need 30GB of system space reserved, especially for a data drive? Just want to make sure im not doing something stupid. Also what is an acceptable space that the system needs reserved for a data drive?

And, more importantly, why does GParted say 30GB is used and when i check the folder properties for that drive, it says 93GB is used? This is very odd.

---

### Post by drs305 on 2010-09-22
> **fuzzylogic25 said:**
> 
but what purpose would i need 30GB of system space reserved, especially for a data drive? Just want to make sure im not doing something stupid. Also what is an acceptable space that the system needs reserved for a data drive?


1-2% would be more than enough.

> 
And, more importantly, why does GParted say 30GB is used and when i check the folder properties for that drive, it says 93GB is used? This is very odd.
I would imagine it's because *nautilus* is a linux app whereas *gparted* is looking at the physical aspects of the disk and not the requirements of the filesystem. Personally, I think it teams up with Disk Usage Analyzer just to provide conflicting information to confuse us. ;-)

---

### Post by mcduck on 2010-09-22
Nautilus runs under your user, and is about the contents of the file system. Thus, it tells you the amount of space *available* for your user on that file system. (space not being available to a certain user is different than space actually used as in having files in it.)

Gparted, and really any tool that's about *partitions* simply looks at the partition size and the amount of data written to it, regardless of the file system and what amount of that space is available to a certain user.

What comes to the amount of reserved space, like already said that's a rather old setting and it's in *percentages* so the amount measured in bytes has grown over time (5% of a 256MB drive is a bit different thing than 5% of a 2TB drive). Nevertheless, the performance of Ext filesystem starts to decrease when the drive gets too full, so you probably won't ever want to fill your drive more than 90% full anyway. Still, if it's not your root partition, even completely disabling the reserved space would be safe.

---

### Post by fuzzylogic25 on 2010-09-22
I did the following:

~$ sudo tune2fs -m 1 /dev/sdc1
tune2fs 1.41.11 (14-Mar-2010)
Setting reserved blocks percentage to 1% (4883780 blocks)

However, my disk usage still has not changed?

Also, can you go below 1%? like 0.5%

---

### Post by scouser73 on 2010-09-22
Is the new drive an internal or an external hard drive?

---

### Post by fuzzylogic25 on 2010-09-22
It is an internal drive.

---

### Post by mcduck on 2010-09-22
> **fuzzylogic25 said:**
> I did the following:

~$ sudo tune2fs -m 1 /dev/sdc1
tune2fs 1.41.11 (14-Mar-2010)
Setting reserved blocks percentage to 1% (4883780 blocks)

However, my disk usage still has not changed?

Also, can you go below 1%? like 0.5%
Sure, although I'm not sure if you can do that if you define the reserved space as percentage. If you use blocks instead then you can easily set it to zero:
```
sudo tune2fs -r 0 /dev/sdc1
```

What comes to the value changing in different applications, you'll most likely have to unmount & remount the filesystem for the change to show correctly.

---

### Post by linux-hack on 2010-09-22
why don't you format and make a new clean partition ? and may be try using fdisk is old but rely efficient

---

### Post by fuzzylogic25 on 2010-09-22
thanks for that, i will definitely try it out. 

also, what is the best way to actually determine the REAL/ACTUAL disk space used/free?

---

### Post by fuzzylogic25 on 2010-09-22
> **linux-hack said:**
> why don't you format and make a new clean partition ? and may be try using fdisk is old but rely efficient

thats exactly what i did. except i didnt use fdisk. i dont believe i can use that for an ext3/4 partition.

---

### Post by mcduck on 2010-09-22
> **fuzzylogic25 said:**
> thanks for that, i will definitely try it out. 

also, what is the best way to actually determine the REAL/ACTUAL disk space used/free?

Well, all the ways you have used give you real values. It's just that they are real values of different thing. One is telling you the used/unused space on the partition, the other is telling you the available/unavailable space on the same partition. Both values are real and correct. What tool you should use depends on which of these things you are interested in.

In other words the partition manager tells you the absolute value of used/unused space of the partition, while the file manager tells you the only value that actually has meaning from the user's point of view, the available space for that user.

edit: that being said, I usually just run "df -h" in a terminal. That gives me the value most relevant in daily use, the amount of space available for my user. (of course just checking it in Nautilus does the same, but df gives a nice view of all my partitions at once)

---

### Post by CharlesA on 2010-09-22
Also note that the journal does take some space as well. 30GB on a 2TB drive is a drop in the bucket tbh.

---

### Post by Chame_Wizard on 2010-09-22
30 GiB is not really much if you have 1/2 TiB HDD.

---

### Post by fuzzylogic25 on 2010-09-22
Thats true, but why would you want to have 30GB of system reserved space? I don't see the point? Especially considering that this is just a data drive, no system files/applications will be held on it.

So I have changed the system reserved space to 128MB. Do you think this is ok? If you could tell me why I might need more, that would be great (provided I do need more).

---

### Post by CharlesA on 2010-09-22
Question: If by "30GB" Do you mean that it shows "usable space" as 1970GB instead of 2000GB?

If so, that's normal, since manufacturer's calculate disk space by using "1000" instead of "1024," so a megabyte is 1,000,000 (1000*1000) bytes, not 1,048,576 (1024*1024).

I just checked my 2TB backup drive and this is what it said:

```
charles@thor:~$ df -BGB
Filesystem          1GB-blocks      Used Available Use% Mounted on
/dev/sdc1               1970GB    1580GB     390GB  81% /cdrom

```

---

### Post by fuzzylogic25 on 2010-09-22
Well I believe I have fixed the issue now. I reduced the Reserved Blocks down to 31250, which is around 128mb. So now the only space used according to the system was under 200MB.

---

### Post by CharlesA on 2010-09-22
You can probably change it to 0. I've done that on my drives.

```
charles@thor:~$ sudo tune2fs -l /dev/sdc1 | grep Reserve
Reserved block count:     0
```

Also, please mark the thread as solved from thread tools. :)

---

### Post by nepenthe on 2010-10-31
> **mcduck said:**
> In other words the partition manager tells you the absolute value of used/unused space of the partition
But why does gparted say there is around 15 gb used space on a *newly formatted* ext4 partition?

---

