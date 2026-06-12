---
title: "Format external drive as ext4 or NTFS?"
date: 2011-07-05
forum: General Help
---

### Post by jcd29 on 2011-07-05
I use Ubuntu 90% of the time, but I sometimes boot into Windows either to play a game or edit a video.

If ext4 is better for the external drive, I wouldn't mind not being able to see it in Windows, especially since I'll be deleting and replacing files as I go along.

- Would ext4 also copy files faster?
- Would eSATA port on my eHDD work with ext4?
- Would formatting this drive as ext4 take up more space initially than if I formatted it as NTFS?

---

### Post by zaphod777 on 2011-07-05
- it may or may not be faster but it would probably be a lot more stable and less prone to error since it is a native Linux file system.

- eSata doesn't care about the file system type.

- the formatted size should be pretty much the same. When it is formatted it is not taking up any space &#3232;_&#3232; however I believe NTFS has a limitation of a max size of 2TB. 

here is some info on reading ext4 from windows though [http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html](http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html)

---

### Post by jcd29 on 2011-07-05
Would there be any problems with permissions or could I use the drive in any Linux machine to copy, erase and create files?

---

### Post by zaphod777 on 2011-07-05
> **jcd29 said:**
> Would there be any problems with permissions or could I use the drive in any Linux machine to copy, erase and create files?

either way you go you will probably need to open up the permissions. For NTFS in Windows make sure "everyone" has read and write access. For Linux use "chmod 777" and then the location of the drive. 

A lot of routers these days give you the option to plug in a USB HDD and share it over the network as a NAS. That may be a better easier option in this case because then you don't need to wory about any of this kind of stuff.

---

### Post by jcd29 on 2011-07-05
> **zaphod777 said:**
> either way you go you will probably need to open up the permissions. For NTFS in Windows make sure "everyone" has read and write access. For Linux use "chmod 777" and then the location of the drive. 

A lot of routers these days give you the option to plug in a USB HDD and share it over the network as a NAS. That may be a better easier option in this case because then you don't need to wory about any of this kind of stuff.

It's okay, I'll just 777 that mofo :D Thanks!

---

### Post by dFlyer on 2011-07-05
I would say to leave it ntfs. At least windows will be able to access the disk without have to install special software. I have never noticed any access speed difference. I use externals for my backup drives and have always used ntfs even though I don't run windows.

---

### Post by pjd99 on 2011-07-06
I would say that ext3/4 is the better filesystem, but if you want full access in windows and linux without hassle, use NTFS.

You can make an ext2/3/4 filesystem available in windows by installing Ext2 IFS, but it only supports ext file systems with an inode size of 128 bytes (mkfs.ext3 -I 128), the Ubuntu default has been 256 bytes for a few years now. Ext4 is supported with some limitations (extents not supported?).
EXT2FSD may have ext4 support.

I've also heard ext3 is better than ext4 in terms of guaranteed writes, something about ext4 caching writes, which could lead to possible data loss on power failure. Not really an issue for single external drives though...

---

### Post by zaphod777 on 2011-07-06
I'm not sure if it is an issue anymore but Ubuntu used to not mount the NTFS drive if it was marked as dirty.

The drive can get marked as dirty if your machine does not safely shut down or you forget to "safely remove" the drive. I would then have to plug it into a Windows machine "safely remove" it and then I could connect it to Ubuntu.

---

### Post by jcd29 on 2011-07-06
Just formatted the drive. 46.8 GB used out of the gate? WTF?

---

### Post by zaphod777 on 2011-07-06
> **jcd29 said:**
> Just formatted the drive. 46.8 GB used out of the gate? WTF?

HDD manufactures and the OS display 1GB differently the HDD manufactures display 1GB as 1000MB and the OS displays it as 1024MB so the space is all there just displayed differently.

---

### Post by jcd29 on 2011-07-06
> **zaphod777 said:**
> HDD manufactures and the OS display 1GB differently the HDD manufactures display 1GB as 1000MB and the OS displays it as 1024MB so the space is all there just displayed differently.

Yeah that's why it appeared as 953 (or around that) GB before formatting, but now there's still around 30-40 GB used right out of the gate after formatting it. I don't remember any external NTFS drives using 40GB after formatting.

---

### Post by zaphod777 on 2011-07-06
> **jcd29 said:**
> Yeah that's why it appeared as 953 (or around that) GB before formatting, but now there's still around 30-40 GB used right out of the gate after formatting it. I don't remember any external NTFS drives using 40GB after formatting.

Hmm fire up gparted and see if there is any blank space not partitioned.

---

### Post by jcd29 on 2011-07-06
No, and the sizes look even weirder when right clicking it and clicking Properties too.

[[IMG]http://img69.imageshack.us/img69/7180/70755142.th.png[/IMG]](http://img69.imageshack.us/i/70755142.png/)

[[IMG]http://img146.imageshack.us/img146/2259/71163295.th.png[/IMG]](http://img146.imageshack.us/i/71163295.png/)

[[IMG]http://img190.imageshack.us/img190/2397/58431543.th.png[/IMG]](http://img190.imageshack.us/i/58431543.png/)

df - h in terminal:

[[IMG]http://img29.imageshack.us/img29/4788/14058915.th.png[/IMG]](http://img29.imageshack.us/i/14058915.png/)

---

### Post by pjd99 on 2011-07-06
[http://ubuntuforums.org/showthread.php?t=1403917](http://ubuntuforums.org/showthread.php?t=1403917)

Just the default space the system reserves (5%). You can modify it after formatting if you wish. Perfectly fine to do if it's just for storage/backup.

```
[FONT=monospace]sudo tune2fs -m 0 /dev/sdc1[/FONT]
```[FONT=monospace]
[/FONT]

---

### Post by jcd29 on 2011-07-06
> **pjd99 said:**
> [http://ubuntuforums.org/showthread.php?t=1403917](http://ubuntuforums.org/showthread.php?t=1403917)

Just the default space the system reserves (5%). You can modify it after formatting if you wish. Perfectly fine to do if it's just for storage/backup.

```
[FONT=monospace]sudo tune2fs -m 0 /dev/sdc1[/FONT]
```[FONT=monospace]
[/FONT]

When would it not be okay to change it?

---

### Post by pjd99 on 2011-07-06
From what i've seen in other posts, the system will use it if space is getting low. So keep it if using it for / or /home partition.

---

### Post by jcd29 on 2011-07-06
> **pjd99 said:**
> From what i've seen in other posts, the system will use it if space is getting low. So keep it if using it for / or /home partition.

So I could remove it from my data partition too.

Also, I still don't get the discrepancy between the 917 GB total capcity shown in Properties, and the 931 GB shown in GParted. Also reserved space, or what?

---

### Post by pjd99 on 2011-07-06
> **jcd29 said:**
> Also, I still don't get the discrepancy between the 917 GB total capcity shown in Properties, and the 931 GB shown in GParted. Also reserved space, or what?

That's a mystery to me...

---

### Post by jcd29 on 2011-07-06
> **pjd99 said:**
> That's a mystery to me...

Gah! Happens to me with every drive. No one else has different sizes under GParted and the disk properties like I showed?

---

### Post by jcd29 on 2011-07-06
I'm marking this as solved since my initial question was answered. I'm starting a new thread about the GParted discrepancy later.

---

### Post by jcd29 on 2011-07-06
One last question.

I set the drive as:

chown -R myuser:myuser

and

chmod -R 777

When I use the drive in another Linux computer, does this mean I'll be able to open any of the files? And also, will thw "owner" of those files be shown as my user in this computer, or will no owner be shown? (Does it even matter?)

---

### Post by jcd29 on 2011-07-06
> **pjd99 said:**
> [http://ubuntuforums.org/showthread.php?t=1403917](http://ubuntuforums.org/showthread.php?t=1403917)

Just the default space the system reserves (5%). You can modify it after formatting if you wish. Perfectly fine to do if it's just for storage/backup.

```
[FONT=monospace]sudo tune2fs -m 0 /dev/sdc1[/FONT]
```[FONT=monospace]
[/FONT]
Oh forgot to ask: Will this external always be mounted as /dev/sdc1? If not I'm guessing this wouldn't help in the long run right?

---

### Post by pjd99 on 2011-07-06
You're right, the /dev/sdc1 is dynamic, it may mount as sdb,sdc,sdd etc depending on how many drives are connected, but that command has modified the file system properties (i.e. the change should persist, only run it again if you want to change the amount of reserved space).

---

### Post by jcd29 on 2011-07-06
> **pjd99 said:**
> You're right, the /dev/sdc1 is dynamic, it may mount as sdb,sdc,sdd etc depending on how many drives are connected, but that command has modified the file system properties (i.e. the change should persist, only run it again if you want to change the amount of reserved space).

Would you recommend putting it at 0% for the external drive (and for my internal data drive, where I have my music, pictures, etc.)? Any downsides?

---

### Post by pjd99 on 2011-07-08
I would think there would only be problems if system processes write data there automatically, otherwise I don't think it would hurt reducing it to 0%.

I just did it to my 500GB ext4 backup partition. Got ~23.5 GiB out of it...

---

### Post by jcd29 on 2011-07-08
Cool, so all the anti-fragmentation properties would still be there in a data drive with that at 0% as long as I didn't have it almost full for a long period of time then?

---

