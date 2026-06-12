---
title: "clonezilla migrate to larger HD, but only allows 30 GB to be used"
date: 2011-08-24
forum: General Help
---

### Post by goodbye-windows(tm) on 2011-08-24
I used clonezilla to move my xp and xubuntu (wubi) from it's original 30 GB drive to a new and more spacious 120 GB drive. The transfer went well and I thought I was home free. I can boot to xp or to xubuntu, everything works great.

BUT.......

When I check the drive size in xp or in xubuntu, the new drive is only 30 GB. So, somehow my 120 GB replacement drive ended up with only 30 GB after the transfer.

Is there a fix for this??? 

Please note, I CANNOT create 2 partitions on the 120 GB drive and have one for windows and one for xubuntu-so I need a single partition with xubuntu installed within the xp root directory.

Appreciate any assistance.

TIA.

Art

---

### Post by lmarmisa on 2011-08-24
If you do not want to create a new NTFS partition ( unit D: ), you have to enlarge your 30GB windows partition. You will need a Ubuntu / Xubuntu Live CD. I recommend to use the tool Gparted.

But, I would like to confirm that you have a unique partition defined on your hard drive. Please, boot into Xubuntu, open a terminal and post the result of this command:

```

sudo fdisk -l

```

---

### Post by goodbye-windows(tm) on 2011-08-24
art@ubuntu:~$ sudo fdisk -l
[sudo] password for art: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        3647    29254365    7  HPFS/NTFS
art@ubuntu:~$

---

### Post by lmarmisa on 2011-08-24
Thanks. You have 2 partitions but one of them has Dell utilities. Do not touch this partition.

You have to enlarge the partition **/dev/sda2** until the end of the free space. You can not use xubuntu (wubi) for enlarging this partition. You will need a Ubuntu / Xubuntu Live CD / USB.

You have to boot into the Ubuntu Live CD. 

Then open the tool **Gparted** (System -> Administration -> Gparted).

Select the partition **/dev/sda2** and click on the icon **Resize/Move the selected partition**. Then extend the partition using all the free space and click on button **Resize/Move**.

Finally click on icon **Apply All Operations**.

The resize operation will take a while. Do not interrupt it!!.

Now, boot your system into Windows. Do not worry about a **chkdsk** procedure during the boot. Windows will reboot your system once or twice. This is normal.

I hope that this procedure will work fine.

IMPORTANT: Do not change the information of your 30 GB hard drive until you have verified that the enlarge procedure was successful.

---

### Post by goodbye-windows(tm) on 2011-08-24
> **lmarmisa said:**
> 

You have to enlarge the partition **/dev/sda2** until the end of the free space. You can not use xubuntu (wubi) for enlarging this partition. You will need a Ubuntu / Xubuntu Live CD / USB.

You have to boot into the Ubuntu Live CD. 




By this, you mean I have to boot with the installation cd or usb drive, correct?

In other words, the 'xubuntu live cd' and the installation cd with the iso on it are the same, correct?

Obviously, I'm a newbee, but I'm lovin' ubuntu already! 

ty for the help.

Regards,

Art

---

### Post by lmarmisa on 2011-08-24
> **goodbye-windoze said:**
> By this, you mean I have to boot with the installation cd or usb drive, correct?

In other words, the 'xubuntu live cd' and the installation cd with the iso on it are the same, correct?

Obviously, I'm a newbee, but I'm lovin' ubuntu already! 

ty for the help.

Regards,

Art

I like that you ask me if you have a doubt. And this is not strange that you have many doubts reading my instructions written in my bad English. :D

Yes, you are right. Xubuntu Live CD and the installation CD are the same. Select the option **Try Xubuntu without installing** at startup.

---

### Post by goodbye-windows(tm) on 2011-08-24
I noticed you were in Spain, my wife and I are ham radio operators and work stations in Spain from time to time. I can assure you that your English is many many times better than my Spanish is!

I'll post the results later, right now it's well past my bed time and I need my beauty rest.

Regards,

Art

---

### Post by lmarmisa on 2011-08-24
I hope that your resize operation will be successful.

Best regards,

Luis

---

### Post by dandnsmith on 2011-08-24
Since this an NTFS partition created under Windows, it would (I feel) be better manipulated under Windows.

I'd start Windows, Start|Run diskmgmt.msc, and see what is there.
With any good fortune the disk will be shown as unfilled, and you can use the tools there to expand the partition/filesystem to fill the HDD.

---

### Post by goodbye-windows(tm) on 2011-08-24
I tried to use windows for this operation, but there were to many unknowns for me. I probably could have figured it out after awhile, but I also needed become familiar with gparted too.

So, I did the operation in xubuntu.

I ended up creating an (additional) 26 GB partition, which I'll use for something else in the future.

The operation went smoothly, and there were no errors. I booted to windows, and all was well. Properties showed the new partition was 89 GB, just as it should be.

In ubuntu however, it appears there is a problem. When I right click on the file system icon and check properties, it only shows 30 GB. I'm not sure if this is an error or whether this is the correct way to check the size of the partition that holds xubuntu.

Here's the code:

```



art@ubuntu:~$ sudo fdisk -l
[sudo] password for art: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       11297    90698525+   7  HPFS/NTFS
/dev/sda3           11297       14594    26481664   83  Linux
art@ubuntu:~$ 


```Did I botch something?

Regards,

Art

---

### Post by JKyleOKC on 2011-08-24
> **goodbye-windoze said:**
> In ubuntu however, it appears there is a problem. When I right click on the file system icon and check properties, it only shows 30 GB. I'm not sure if this is an error or whether this is the correct way to check the size of the partition that holds xubuntu.Since you said in an earlier message that you installed Ubuntu within the XP partition, that almost certainly means that you did the installation with "wubi" since there's no other way to do that. The bad news is that this type of installation is limited to only 30 GB total, since it's actually all inside a Windows file.

The only way to get your Ubuntu system to use more than 30 GB will be to install it in its own, completely separate, partition. If you do that, you can make it as big as your drive can allow. I'm on a 500 GB drive here, and my home partition still has more than 150 GB free despite having more than half a dozen virtual machines, each with its own 20-GB virtual drive, installed.

Additionally, if you move Ubuntu to its own partition, the performance will be quite a bit better since it won't have to translate all disk actions into the Windows format for actual storage, and you won't be so likely to encounter update problems (which are known to affect some wubi installations with the latest system versions). You can do so by using clonezilla again to back up just the Ubuntu system, then doing a fresh install. However you should delete that new partition you added, and then during the install tell the program to use the unused space of the drive. That will create the necessary pair of partitions in the free space automatically for you.

---

### Post by Mark Phelps on 2011-08-24
You're running a Wubi-based install, meaning, that its using a large file INSIDE your Windows NTFS partition.  So, adding a new partition will not make the Ubuntu space larger; instead, it will have no effect on it.

You were told to resize your Windows NTFS partition to fill the drive.  You did not do that -- so as far as Ubuntu is concerned, it is still the same size.

---

### Post by goodbye-windows(tm) on 2011-08-24
TY to Mark and Jim.

Mark, When I go to windows and check the size of the C drive, it shows it as being around 90 GB-so I think I did create the larger partition.

Jim, yes, I did use wubi. I am painfully aware of the proper way to do the job...which is to create separate partitions for both operating systems. However, this is not possible, for technical reasons. In my case, I'm running a Dell Inspiron 1100, which has an issue with the transition to and from 2D and 3D modes-the screen goes black. The black screen is a common problem in some Dell systems. 

There is also a problem when the screen saver kicks in-sometimes the screen goes black and stays that way when the screensaver activates deactivates.

So, I MUST use windows and wubi in order to have xubuntu run. Having XP there is part of the work around I need in order to keep xubuntu running.

If you search the Dell forum using 'black screen', you can read about this issue.

At some point, I'm going to get a different laptop-but for now, I'm stuck with the windows/xubuntu/wubi combination.

When I installed xubuntu, I initially did so in a 6GB folder. Now that I have the bigger drive, I need to move the entire xubuntu into a 30 GB folder so that xubuntu can use more of the drive. Right now, I have only 1.5 GB available for xubuntu. So, the next issue will be how to move xubuntu into a larger folder within windows. Not sure it's possible, I spent a bunch of time searching hte forum last night and came up empty::>

Again, TY to you both.

Art

---

### Post by JKyleOKC on 2011-08-24
You should be able to use clonezilla to make a full backup of your Ubuntu installation to that new partition at /dev/sda3, then use Windows "add/remove programs" to remove the existing wubi installation, reinstall it but this time with a 30-GB disk size, then restore everything from the clonezilla backup. I'm not that familiar with clonezilla but you might have to do some tweaking to expand the Ubuntu installation's size after doing the restore. If you've not installed additional software, though, and with only a 1.5-GB installation I'm sure you can't have installed very much yet, you might only need to restore your home directory from the backup since the rest of the configuration should not see much change...

---

### Post by bcbc on 2011-08-24
[HOWTO: Resize the WUBI virtual disk]("http://ubuntuforums.org/showthread.php?t=1625371")

I'm a bit puzzled that you find wubi works different to a direct install. There should be no difference. Wubi uses a virtual disk and a bit of a windows bootmanager/grub4dos/grub2 hack to boot - but otherwise it's the same as a regular install.

---

### Post by lmarmisa on 2011-08-25
Sorry. This post was wrong, but I can not remove it.

---

### Post by goodbye-windows(tm) on 2011-08-25
I cloned the old 30 GB hard drive and moved the entire drive over to the new (and much larger 120 GB) drive. Clonezilla works like a champ. So, I am marking this thread as 'solved'.

The second part of the migration is to make the virtual drive (where xubuntu resides) larger, so ubuntu can use more of the new hard drive. The answer was to follow the procedure outlined above. It worked perfectly although wubi limits the virtual drive to 30 GB. But, the old size was only 7 GB, so there is lots of room for xubuntu to grow into.

My daughter will use the laptop for her school work this year. She's been watching me tune xubuntu and has been using the laptop quite a bit in the interim. For the last 2 years, she has had the use of a top of the line Mac. This year however, the school system can't supply computers. She says this xubuntu rivals the speed of her school supplied Mac and is just as easy to use. I should say the laptop is a low end 10 year old Dell Inspiron with an old Celeron processor. So, we're both overjoyed that xubuntu works so well.

Again, thanks to all who helped out with technical info and guidance.

Regards,

Art

---

### Post by JKyleOKC on 2011-08-25
I trust that you did see, in that HOW-TO thread, that it's possible to override the 30-GB limit of wubi and create a virtual drive up to at least 100 GB. However 30 GB may well be all your daughter needs.

It's good to know you got the problem solved, and I'm glad to have been directed to that how-to link even though I have only one wubi installation, and no room on the laptop drive to enlarge it.

---

### Post by bcbc on 2011-08-25
I recommend using Ubuntu One to synchronize your data for Wubi. You are also able to save other data e.g. larger multimedia on the windows /host partition (outside of the virtual disk). This is by far the safer option than storing personal data on the virtual disk which is a single file that could become corrupted e.g. due to [hard shutdowns]("https://wiki.ubuntu.com/WubiGuide#How_to_reboot_cleanly_even_when_the_keyboard.2BAC8-mouse_are_frozen") or power failure/running out of battery (laptop).

Wubi in general works great and I haven't personally lost any virtual disks, but I do see threads from people who have. That's why a direct install is safer (and as I said earlier, if Xubuntu works fine on your computer with Wubi it should work fine as a direct install).

---

