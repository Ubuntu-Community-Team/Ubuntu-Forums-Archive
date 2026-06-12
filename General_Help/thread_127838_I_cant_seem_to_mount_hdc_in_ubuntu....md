---
title: "I cant seem to mount hdc in ubuntu..."
date: 2006-02-09
forum: General Help
---

### Post by ttallos on 2006-02-09
I cant seem to mount hdc in ubuntu... when I type fdisk -l   as root

I get the following    hda  hda1   etc...etc...etc
                            hdc  hdc1  fat32  etc...etc...

then I try to type  as root    /dev/hdc       access denied
                                       /dev/hdc1      access denied
                                       /mnt/hdc       no such file or partition
                                       /mnt/hdc1     no such file or partition

It would seem easy to slave in a drive and get the data off of it. But I don't seem to have the right touch. I have all brand new hardware. Help me Spock!

---

### Post by Sutekh on 2006-02-11
I just want to make sure we're on the same page.  You have a hard drive identified as /dev/hdc and you want to mount this hard drive, correct?  The file format is FAT32, yes?

That should be pretty straightfoward.  I think this link can help you.

[Mounting Windows Partitions in Ubuntu - by]("http://www.psychocats.net/linux/mountwindows.php")[aysiu]("http://ubuntuforums.org/member.php?u=21941")

Right down the bottom is a section on mounting FAT32 partitions.  Sing out if you get stuck.

---

### Post by ttallos on 2006-02-11
Thanks I will get back to you and let you know if it worked.

---

### Post by Lord Illidan on 2006-02-11
The fat32 partition is not /dev/hdc

/dev/hdc is the harddisk itself.

What you are looking for is /dev/hdc1 - or so I gathered from your info

To mount it:

```
sudo mount /dev/hdc1
``` 
First, however, check your /etc/fstab to see if it was mounted at bootup. Generally, when you install Ubuntu, it will configure itself so it will mount ntfs and fat32 drives at bootup.

If not:

Create an extra folder.

```
sudo mkdir /media/fat_drive
``` You can rename fat_drive to whatever you wish.

then do this..

```
sudo mount /dev/hdc1 /media/fat_drive
```

Also, check the Ubuntu Documentation for more info: [https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

---

### Post by ttallos on 2006-02-11
Thanks for all the input I am getting to it now.....

---

### Post by ttallos on 2006-02-11
Thanks for the info I liked the easy page explanation the best both wrer great. I have a RAID 5 server running ubuntu 5.10 and I am going to see if that plan works good to get the data to or from the RAID 5. You guys rock!

---

