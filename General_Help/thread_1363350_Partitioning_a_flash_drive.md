---
title: "Partitioning a flash drive"
date: 2009-12-24
forum: General Help
---

### Post by nishant.singh28 on 2009-12-24
I have a 4 GB flash drive with 3.73 GB usable capacity. I want to partition it into two parts.
> 1.73 GB for Ubuntu ISO
> 2 GB for Data
I don't need to transfer large files using the flash drive. I need to keep a bootable flash drive as I have messed up my Ubuntu installs frequently and like to keep a bootable drive accessible. How do I solve both purposes using the same flash drive? Is it possible to make one part of my flash drive bootable and the use the other part for transferring Data?

---

### Post by nishant.singh28 on 2009-12-24
Bump!!!!

---

### Post by SuperSonic4 on 2009-12-24
For partitioning purposes it will act like a hard drive. Therefore use gparted to make it into two parts - make one bootable using your favourite method and leave the other for data

---

### Post by nishant.singh28 on 2009-12-24
> **SuperSonic4 said:**
> For partitioning purposes it will act like a hard drive. Therefore use gparted to make it into two parts - make one bootable using your favourite method and leave the other for data
Tried it. Did not work. So put up this post. :D

---

### Post by nishant.singh28 on 2009-12-24
Is there a specific method, order or setting?

---

### Post by nishant.singh28 on 2009-12-25
Bump!!!!

---

### Post by bodhi.zazen on 2009-12-25
> **nishant.singh28 said:**
> Tried it. Did not work. So put up this post. :D

When you say it "did not work" you need to give us more details. What did not work exactly ?

---

### Post by nishant.singh28 on 2009-12-25
When connected to an XP system, it did not detect the bootable partition. It simply detected only the 2 GB partition. When I tried booting my own system from it, it said there was some file missing, i.e, it did not detect the bootable partition.

---

### Post by bodhi.zazen on 2009-12-25
So, partitioning worked but you can not boot from it ?

That could be either a BIOS problem (you need to set your BIOS to boot to USB) or the necessary files are not on the first partition.

How did you put the files on the UDB from the iso ? 

I advise unetbootin, handles such things automatically, although you can do it manually as well.

---

### Post by nishant.singh28 on 2009-12-25
Yes. I used the usb startup disk creator in Ubuntu.As far as BIOS is concerned, I am using Ubuntu installed from that itself. Thanks anyways. Will try unetbootin and get back.

---

### Post by nishant.singh28 on 2009-12-25
Ubuntu detects both partitions, windows does not. It detects only the 2 GB part

---

### Post by nishant.singh28 on 2009-12-25
bump

---

### Post by SecretCode on 2009-12-25
I see the same thing. Windows only sees 1 partition.

I think this is a limitation of Windows (XP at least, not sure about other versions) - it only recognises a single partition on a removable USB drive. To get around this, you need to flip the "removable bit" on the USB drive - **which may damage it**. Google for instructions and a tool, and proceed at your own risk!

---

### Post by bodhi.zazen on 2009-12-26
> **nishant.singh28 said:**
> Ubuntu detects both partitions, windows does not. It detects only the 2 GB part

I have not seen that. If Ubuntu is recognizing the partitions, then it is not really a partitioning problem.

I suggest you post on a windows forum.

---

### Post by nishant.singh28 on 2009-12-26
But the BIOS also does not recognise it....that is the whole problem. And as I said earlier, the BIOS does recognise USB drives. I have installed Karmic that way.

---

### Post by SecretCode on 2009-12-26
> **nishant.singh28 said:**
> But the BIOS also does not recognise it....that is the whole problem.

What do you mean by this? You want to boot from a second partition on a flash drive? Have you installed GRUB on the flash drive?

---

### Post by bodhi.zazen on 2009-12-26
> **nishant.singh28 said:**
> Ubuntu detects both partitions, windows does not. It detects only the 2 GB part

You will need to ask this question on a windows forum as the USB seems to be working in Ubuntu.

In terms of booting, did you try unetbootin ? Or did you ignore this advice? If you do not follow advice, how is you expect further assistance?

It seems the USB creator did not set up your usb device, unetbootin is an alternate option. If you are having problems, reformat the FAT partition.

In terms of your BIOS, that you would have to ask your hard ware manufacturer.

Last, some USB devices apparently will not boot. I personally have not seen this, although I have seen the "USB Creator" fail.

---

### Post by nishant.singh28 on 2009-12-26
> **bodhi.zazen said:**
> You will need to ask this question on a windows forum as the USB seems to be working in Ubuntu.

In terms of booting, did you try unetbootin ? Or did you ignore this advice? If you do not follow advice, how is you expect further assistance?

It seems the USB creator did not set up your usb device, unetbootin is an alternate option. If you are having problems, reformat the FAT partition.

In terms of your BIOS, that you would have to ask your hard ware manufacturer.

Last, some USB devices apparently will not boot. I personally have not seen this, although I have seen the "USB Creator" fail.
First of all:
If Windows does not recognise the drive I want to put Ubuntu into, how do I use unetbootin? If there is a way in Ubuntu, please tell me.

I have done the formatting many times.

I told you. I am running a copy of Ubuntu installed on the same machine from the same flash drive ( when it was unpartitioned ) as the ones in consideration. When I mean same, I am not talking about make. They are physically the same ones. So the questions regarding hardware issues are pointless as the combinaton does work.

---

### Post by bodhi.zazen on 2009-12-26
> **nishant.singh28 said:**
> First of all:
If Windows does not recognise the drive I want to put Ubuntu into, how do I use unetbootin? If there is a way in Ubuntu, please tell me.

unetbootin is in the Ubuntu repositories.

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=unetbootin](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=unetbootin)

Add the universe repository, then use any tool you wish to install unetbootin.

```
sudo ap-get update
sudo apt-get install unetbootin
```

Then run it as root.

```
gksu unetbootin
```

Again, if you have problems, reformat the FAT partition you are installing the iso into.

---

### Post by C.S.Cameron on 2009-12-27
Yes windows only recognizes the first partition on a flash drive.
You can make a bootable persistent Ubuntu flash drive with a Windows recognizable partition as follows:
Boot Live CD, (or live USB).
Plug in flash drive.
Start Partition Editor.
Create first partition as FAT32 for Data, make this less than 650MB so usb-creator will not write to it.
Create a second FAT32 partition with remaining space.
Start up usb-creator.
U-C should only allow you to install to second partition, do so after specifying space for persistence. Remember to leave some free space so that you can increase the size of your first partition later.
Once U-C has finished start Partition Editor and adjust your partition sizes as you like.
Shut down the Live CD and test the flash drive.

You can also do a full install to flash drive using the install option on the Live CD and manual partitioning to get your first partition as FAT32. I recommend disabling your internal hard drive if you use this method.

---

### Post by SecretCode on 2009-12-27
Excellent post, C.S.Cameron!

Question: in this case, will the reserved space for persistence still exist in the second partition, ie the one USB-Creator installs to?

---

### Post by C.S.Cameron on 2009-12-27
Yes, it is just a file in the Ubuntu install named casper-rw.
An alternate method of adding persistence is to create partitions named casper-rw and home-rw and omit adding persistence at the u-c install. This also works with an unetbootin install.

---

### Post by garvinrick4 on 2009-12-27
Use this make a small sba1 for /boot. sdb2 will be / and make sure in page 8 of gparted
you use advanced and tell it /boot or sdb1 is where boot is going to be. Replace b in sdb
with whatever device letter it is. 



On the bottom of page in fdisk -l you will see the flash drive with full persistence.


This is a working USB Flash drive with that operates with full Ubuntu O.S.
Has persistence for all 13 gig partition with boot in seperate partition done
with gparted manually. It works I am using it now on Laptop. 

I have finally got a 16 gig Flash drive to work as independent system. A lot of trial and error.
Used Live CD. 9.10 64 bit and the 16 gig flash drive.
Booted Live CD and selected install.
When it got to partitioning selected USB device of course.
1st partition was 500 meg ext3  /boot as mounting point
2nd partition was 13.5 gig ext3 / as mounting point
3rd partition was 2 gig Swap

IN THE 8TH PAGE YOU HAVE TO CLICK ADVANCED TAB AND SELECT BOOT AS THE SAME
AS YOUR 1ST PARTITION  THAT YOU SELECTED AS /BOOT AS MOUNTING POINT.

 Then add your repositories such as partners, medibuntu, backports, all the same ones as your normal install. You have over 12 gig left to work with so use what you want. Compiz works fine, the only thing in Karmic I have not gotten to work is sound and every install of 9.10 on my HP G71-34OUS has
had sound issues, I will get it. WIFI came right in. Has been a normal install.

Grub menu.  When you upgrade it installs itself onto your systems grub with no partition
number such as sba1 or any device. This works well it just installs a grub selection while
plugged in to USB port with recovery selection.

                                                        here is fdisk.   I am running flash drive now.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       26132   209696248    7  HPFS/NTFS
/dev/sda3           26133       37330    89947935    5  Extended
/dev/sda4           37331       38914    12709888    7  HPFS/NTFS
/dev/sda5           32107       37111    40202631   83  Linux
/dev/sda6           37112       37330     1759086   82  Linux swap / Solaris
/dev/sda7           26133       31856    45977967   83  Linux
/dev/sda8           31857       32106     2008093+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 16.7 GB, 16687038464 bytes
64 heads, 32 sectors/track, 15914 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x0008849e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         954      976880   83  Linux
/dev/sdb2            3831       15914    12374016   83  Linux
/dev/sdb3             956        3830     2944000   82  Linux swap / Solaris
                                                                                               __________________

---

### Post by SecretCode on 2009-12-27
Hmm. I tried this ... made a 400MB partition, some unallocated space, and a 2GB partition on a 4GB USB stick. 

But USB Startup Disk Creator (in Ubuntu Karmic) would not accept the 2GB partition for use ... only the format button was available ... and clicking that formatted the **whole** USB stick, somewhat unexpectedly. Any thoughts?

---

### Post by C.S.Cameron on 2009-12-27
I would think it should work ok as long as the partitions are FAT32. I would try it 400MB partition on the right, the 2GB partition next to this then the unallocated space.
I have not tried it with 9.10 yet but know it works with 9.04.

---

### Post by garvinrick4 on 2009-12-28
I believe USB Start-up disk creator has a limit of 4 gig. By the time you do all your
downloads and get a complete system you have already filled up the 4 gig and system
is stymied there. Not good enough, needs to have full  persistence to satisfy the size of
Flash drives that have become affordiable in todays market place. I am sure there will
be a program such as USB Start-up creator that will become more than just a Live USB
creator and make these flash drives fully functional without using a partitioning software such
as gparted. I myself like gparted.

---

### Post by nishant.singh28 on 2010-01-15
Well...I decided to go for a new 2 GB flash drive. Flash memory is dirt cheap anyways. Got myself a Hi-Speed flash drive for Rs. 350. So...a little lighter wallet but a much lighter mind...don't you agree?:D

---

