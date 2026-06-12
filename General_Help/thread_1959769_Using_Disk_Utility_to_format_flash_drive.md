---
title: "Using Disk Utility to format flash drive"
date: 2012-04-16
forum: General Help
---

### Post by craig10x on 2012-04-16
I am getting a San Disk Cruzer 8 gb  usb flash drive which i am going to use to transfer video files from my hard drive on the laptop to the flash drive to play on a dvd player that can use flash drives to play videos...

I never used Disk Utility before...can you format to FAT32 with it?
My friend (who has that dvd player that plays from flash drives) told me i need to format in to FAT32 so it would be compatible with the player...

So the question is: will it format to FAT 32 and is it easy to use?
I heard one can use gparted also, but DiskUtility looks simpler to use...

Second Question: I will also be getting the 32 gb flash drive to use for storage of my videos, pictures, etc that are on my hard drive...since that one will just be for storage,
would there be any advantage to formatting that drive to EXT4 or would FAT32 do just as well?

Thanks...;)

---

### Post by callmemahavir on 2012-04-16
You can stick to FAT32 filesystem Because of its wide compatibility.

Issue the following command ... for FAT32 filesystem.

mkfs.vfat /dev/sdc1

---

### Post by sudodus on 2012-04-16
> **craig10x said:**
> I am getting a San Disk Cruzer 8 gb  usb flash drive which i am going to use to transfer video files from my hard drive on the laptop to the flash drive to play on a dvd player that can use flash drives to play videos...

I never used Disk Utility before...can you format to FAT32 with it?
My friend (who has that dvd player that plays from flash drives) told me i need to format in to FAT32 so it would be compatible with the player...

So the question is: will it format to FAT 32 and is it easy to use?
I have only used the Disk Utility to view drives and partitions, but I see that there is an option edit partitions and format them. So it should work. Try it, but be check that

0. you are editing 'another' partition (not one of your active file system(s) / or /boot or /home)

1. it is the correct device and partition and not something you want to keep

2. it is not mounted

I am using Gparted, which can be installed into Ubuntu with
```
sudo apt-get install gparted
```
> 
I heard one can use gparted also, but DiskUtility looks simpler to use...

Second Question: I will also be getting the 32 gb flash drive to use for storage of my videos, pictures, etc that are on my hard drive...since that one will just be for storage,
would there be any advantage to formatting that drive to EXT4 or would FAT32 do just as well?

Thanks...;)

If you think you will ever use it with Windows, you should format it to FAT32 or NTFS. NTFS is journaled, safer but slower. If you will only use it in linux, select ext2, ext3 or ext4. ext3 and ext4 are journaled, ext4 is faster but more risky, if you are not shutting down correctly (or pulling it out before finished writing). I would recommend ext3 and to mount it with the noatime option to reduce wear.

FAT32 limits the file size to 4 GB, and has no journaling.

---

### Post by philinux on 2012-04-16
> **craig10x said:**
> I am getting a San Disk Cruzer 8 gb  usb flash drive which i am going to use to transfer video files from my hard drive on the laptop to the flash drive to play on a dvd player that can use flash drives to play videos...

I never used Disk Utility before...can you format to FAT32 with it?
My friend (who has that dvd player that plays from flash drives) told me i need to format in to FAT32 so it would be compatible with the player...

So the question is: will it format to FAT 32 and is it easy to use?
I heard one can use gparted also, but DiskUtility looks simpler to use...

Second Question: I will also be getting the 32 gb flash drive to use for storage of my videos, pictures, etc that are on my hard drive...since that one will just be for storage,
would there be any advantage to formatting that drive to EXT4 or would FAT32 do just as well?

Thanks...;)

The disk utility is a doddle to use. As always be careful with this type of utility. No need to use terminal commands.

---

### Post by craig10x on 2012-04-16
Thank you for all the great replies...i have the 8gb flashdrive...it was actually already pre-formatted to FAT32 but just for practice i re-formatted it using 
Disk Utility....

For "FAT" it only showed that in the list of choices...but i went ahead and did it and checking afterwards i see that it automatically format it to the FAT32 which is what i need for the dvd player i will use...

Even for the larger one i will use just for storage, i will format it to FAT32 so it will have the most versatility...no problem on the 4gb file limitation as my videos are only DIVX files...i don't download those big dvd files...and DIVX files are always less then 2gb (usually more in the 800 mb to around 1 GB range)...

So, it went great and that program is so easy to use and fast too ;)
Thanks again for the help...

---

### Post by sudodus on 2012-04-16
I'm glad it works for you :KS

Finally, please click on [COLOR="Red"]**Thread Tools**[/COLOR] at the top of this page and mark this thread as SOLVED!

---

### Post by JC Cheloven on 2012-04-16
May I add a side note: 
As you said, fat32 will not handle a file greater than 4Gb. Please consider whether that may be relevant or not for you in the future. Now adays a film may reach that size... I faced myself with that recently even though I didn't expect that to happen.

---

