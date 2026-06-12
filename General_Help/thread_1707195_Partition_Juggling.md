---
title: "Partition Juggling"
date: 2011-03-15
forum: General Help
---

### Post by Reynbow on 2011-03-15
So, all I want to do is to shrink sda5 (Ubuntu partition) to 145GBs.
Extend sda3 (Windows7) to 145GBs 
Leave the middle chunk (aprox 400GBs) as it's own free space partition as sort of a file sharing folder for Windows and Ubuntu to share.

I use Ubuntu as my main OS and download movies etc. through it but use Windows Mediac Center and other apps on Win7 that (obviously) can't be run in Ubuntu.

[IMG]http://img.photobucket.com/albums/v633/Sting81/Screenshot-2.png[/IMG]

So, can anyone give me some help at all. I'll use a live USB version of GParted to do the partition editing but I just want to double check with you guys before I touch anything. =]

Thanks in advance.

---

### Post by MARP1961 on 2011-03-15
What you plan to do sounds fine; but take precautions by backing up any important personal files on flash drive, cd, external hard drive first (data can sometimes get deleted when resizing partitions). I have resized Windows ntfs partitions using gParted before and had to carry out a repair using my Windows Vista installation disk. Do you have a disk to carry out repairs to your Windows 7 if Windows complains?

---

### Post by Reynbow on 2011-03-15
I don't really care about if it breaks to be honest. Everything I want kept is on two other internal HDDs. 
But I really just want to know how to go about doing it to be honest.

When I tried to do what I thought was right, the middle partition I wanted to use as the in-between partition for both OSes to share was inside the"sda2 extended" partition group thing... I don't really know what that means to be honest so I'm not sure if I did it right.

It had the lite blue outline around it, like it does in the screenshot for sda5. So yeah, will Windows still see it if it's like that?

---

### Post by plucky on 2011-03-15
1) Boot the Live Cd and run Gparted
2) Select the /dev/sda5 partition and shrink by 145 Gb (might take a while,so be patient)
3) You will now see the unallocated space inside the extended partition.
4) You can now create another partition inside the extended partition which I assume will be NTFS if you want to share it with win 7. (It will be a logical partition.)
5) If you want to create a primary partition you will have to select the /dev/sda2 partition and shrink it so the un-allocated space moves outside of the extended partition.

**Please backup your important data first**

> So yeah, will Windows still see it if it's like that? 


Windows doesn't like to boot from a logical partition but will use a logical partition if it is NTFS or Fat32.

Good Luck

---

### Post by Reynbow on 2011-03-15
Excellent, thank you very much =]

EDIT: I have one last question, I have completed everything you've said plucky. However there was one last thing I wanted to do. Extend the Win7 partition to be 145GBs as well. Now I was able to do that, but when I clicked apply a warning came up saying something along the lines that it may fail to boot. Should I just not bother as this is very likely to occur, or would it be a rare thing to happen?

---

### Post by plucky on 2011-03-15
> **Reynbow said:**
> Excellent, thank you very much =]

EDIT: I have one last question, I have completed everything you've said plucky. However there was one last thing I wanted to do. Extend the Win7 partition to be 145GBs as well. Now I was able to do that, but when I clicked apply a warning came up saying something along the lines that it may fail to boot. Should I just not bother as this is very likely to occur, or would it be a rare thing to happen?

I don't use win 7 but from the posts I have seen you should use the windows 7 Disk management tools to move and resize windows partitions.Windows knows best how to move windows partitions.

Good Luck

---

