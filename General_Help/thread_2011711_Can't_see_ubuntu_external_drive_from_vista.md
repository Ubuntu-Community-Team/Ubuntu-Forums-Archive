---
title: "Can't see ubuntu external drive from vista"
date: 2012-06-27
forum: General Help
---

### Post by Gh0zt36 on 2012-06-27
I like to update my music and pictures from vista to ubuntu or vica verca to keep them up todate on both drives incase one or the other fails . But I always have to boot from Ubuntu and go into windows drive which is a pain in the *** when Im on vista. 

So is there anyway to make ubuntu on the external drive visible on windows vista so I dont always have to switch when Im using vista?

---

### Post by Basher101 on 2012-06-27
Ubuntu uses the ext4 filesystem, which is [COLOR="Red"]unreadable[/COLOR] by windows. If you wish to store files for both OSs, you should make a new partition with the NTFS filesystem.

regards

---

### Post by holycow131415 on 2012-06-27
windows does not recongize ext4. youll have to reformat/reinstall ubuntu on ntfs partitions

---

### Post by Basher101 on 2012-06-27
> **holycow131415 said:**
> windows does not recongize ext4. youll have to reformat/reinstall ubuntu on ntfs partitions

no need to do so...he just needs one NTFS partition where he can store files for both operating systems. Besides, you cannot install ubuntu on ntfs..

---

### Post by Cheesemill on 2012-06-27
Or you can install ext2fsd in Windows to give you read/write access to ext4 partitions.
[http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html](http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html)

I wouldn't recommend it though, instead it would be better to set up a shared NTFS data partition.

---

### Post by Gh0zt36 on 2012-06-27
> **Basher101 said:**
> no need to do so...he just needs one NTFS partition where he can store files for both operating systems. Besides, you cannot install ubuntu on ntfs..


Ok so forgive the patition noob. Are you saying I make a partition for the OS and then a seperate partition for the media?   will I still be able to read these partitions by default in music , pictures , video folders in ubuntu?

---

### Post by cprofitt on 2012-06-27
Windows needs to have a special program to see ext# formatted drives (partitions).

You can use: [Ext2Fsd]("http://sourceforge.net/projects/ext2read/")

Though in most cases making a data partition that is NTFS works well.

---

### Post by Gh0zt36 on 2012-06-27
> **cprofitt said:**
> Windows needs to have a special program to see ext# formatted drives (partitions).

You can use: [Ext2Fsd]("http://sourceforge.net/projects/ext2read/")

Though in most cases making a data partition that is NTFS works well.


Awwww yea.....   That program did exactly what I wanted done THANKS ALOT .   That was a simple solution as opposed to creating partitions and all that .

---

### Post by Gh0zt36 on 2012-06-27
Thanks to all who replied!!!!

---

### Post by Cheesemill on 2012-06-27
> **Gh0zt36 said:**
> Awwww yea.....   That program did exactly what I wanted done THANKS ALOT .   That was a simple solution as opposed to creating partitions and all that .
Although it appears to work OK, I wouldn't rely on it if I were you.

Just the same way as accessing your Windows OS partition from Ubuntu can sometimes break Windows without any warning, accessing your Ubuntu partition from Windows can also sometimes break Ubuntu.

The best option is to create a shared NTFS partition for all of your data.

---

### Post by Gh0zt36 on 2012-06-27
> **Cheesemill said:**
> Although it appears to work OK, I wouldn't rely on it if I were you.

Just the same way as accessing your Windows OS partition from Ubuntu can sometimes break Windows without any warning, accessing your Ubuntu partition from Windows can also sometimes break Ubuntu.

The best option is to create a shared NTFS partition for all of your data.
  

I think you think  i' referring to a dual boot scenario.   I have a dedicated harddrive for vista 500gb and a seperate dedicated  external drive 250gb for ubuntu. 

So I'm not accessing a windows partition Im accessing a completely seperate drive with windows on it and vica versa.  

Can I still break windows or ubuntu accessing them? Or was your post just about accessing one partition from another? :guitar:

---

