---
title: "Lost WIN 7 after installing Ubuntu 10.04"
date: 2010-10-02
forum: General Help
---

### Post by Majidjan on 2010-10-02
I have a harddisk which is partiotioned in C & D. I've installed WIN XP on C and WIN 7 on D. Then I installed Ubuntu 10.04 on D beside WIN 7. Now I can't access to WIN 7 and also to drive D in XIN XP and in Ubuntu.
What can I do to get back WIN 7 and drive D ?

---

### Post by Mark Phelps on 2010-10-02
First thing you need to do is confirm that your Win7 files are there.

Since you can boot into Ubuntu, do that, open an terminal, and run "sudo fdisk -lu" (that's a lowercase L, not a one).  This will list your partitions.  If it lists the Win7 partition(s) as well as the Ubuntu partitions, Win7 is still there.

For further confirmation, go to Places and click on the disk icon for Win7 (you may find two of them).  Open the partition and confirm that the files are still there.

If both of these worked OK, the good news is that all you have to do is add a GRUB entry for Win7.  Do that by opening a terminal in Ubuntu, and entering "sudo update-grub".  That will regenerate your GRUB menu and add an entry for Win7.

When you next reboot, you should get a GRUB menu with entries for Win7 and for Ubuntu.

---

### Post by Majidjan on 2010-10-02
Thanks your reply,
Output of sudo fdisk -lu is :

majid@majid-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x288a2889

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   102398309    51199123+   7  HPFS/NTFS
/dev/sda2       102398371   125929471    11765550+   f  W95 Ext'd (LBA)
/dev/sda5       102398373   121929622     9765625   83  Linux
/dev/sda6       121929728   125929471     1999872   82  Linux swap / Solaris

Going to Places shows nothing about WIN 7 just shows WIN XP ( which is installed on C).
Any idea ?
:confused:

---

### Post by raymondh on 2010-10-02
> **Majidjan said:**
> Thanks your reply,
Output of sudo fdisk -lu is :

majid@majid-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x288a2889

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   102398309    51199123+   7  HPFS/NTFS
/dev/sda2       102398371   125929471    11765550+   f  W95 Ext'd (LBA)
/dev/sda5       102398373   121929622     9765625   83  Linux
/dev/sda6       121929728   125929471     1999872   82  Linux swap / Solaris

Going to Places shows nothing about WIN 7 just shows WIN XP ( which is installed on C).
Any idea ?
:confused:

I don't see a win7.  

Look at the start of sda5 and the end of sda6.  They coincide with the start and end of sda2 (which is what you refer to as drive D ... in win speak).

Sorry ... but if I'm right, you installed linux OVER win7.

---

### Post by Majidjan on 2010-10-02
> **raymondh said:**
> I don't see a win7.  

Look at the start of sda5 and the end of sda6.  They coincide with the start and end of sda2 (which is what you refer to as drive D ... in win speak).

Sorry ... but if I'm right, you installed linux OVER win7.
You mean no chance to recover WIN 7 ?
If so , what should I do in order to :
1- access to drive D in both windows & Linux ?
2- how to erase Ubuntu to install a fresh Win XP - Win 7 & ubuntu ?
This time I'm goining to have 3 partition on my HDD.

---

### Post by raymondh on 2010-10-03
> **Majidjan said:**
> You mean no chance to recover WIN 7 ?
If so , what should I do in order to :
1- access to drive D in both windows & Linux ?
2- how to erase Ubuntu to install a fresh Win XP - Win 7 & ubuntu ?
This time I'm goining to have 3 partition on my HDD.

One more test/try.

As mark says, boot into ubuntu > places and see if win 7 is there... If it is, then follow his instructions on updating grub.  If not, you need to clarify ...... You want to 3-boot using a 1 hd set-up? You now have XP on the first partition, sda1.  Where do you want win7 and ubuntu..... Sda2 and possibly a sda 5-6 for ubuntu. From above, are you thinking of using the sda2 as a storage  partition alone?

Erasing is easy.  Just reinstall over it and then install ubuntu.  I prefer to set up the partitions before installing...

Post how you want to proceed and we'll try a tutorial for you.

In the meantime, back up your data elsewhere.

---

### Post by Majidjan on 2010-10-03
Hi.
I checked Places again, No WIN 7 exists.
I want to use 1 HDD to setup WIN XP , WIN 7 , UBUNTU on individual  partition let's say C, D , E. Any guide or tutorial ?
Thanks.

---

### Post by Mark Phelps on 2010-10-03
Linux (and Ubuntu) don't use the MS Windows "Drive Letters" scheme, so saying you want to install Ubuntu on "D" or "E" is confusing.

It looks like you might have wiped Win7 from "D" when you installed Ubuntu to it.  There's no second NTFS partition in the fdisk list (which is bad news) and you said you saw no volume for it in Places.

My recommendation (others may vary) for formatting a drive for what you want to do is the following:
1) Partition #1 - Primary, NTFS, WinXP
2) Partition #2 - Primary, NTFS, Win7
3) Partition #3 - Extended
4) Partition #4 (inside Partition #3) - Logical, Ext4, Ubuntu
5) Partition $5 (inside Partition #3) - Logical, Linux-Swap

You can do what you want by booting a GParted LiveCD, shrinking the current XP partition to make room for Win7, and then booting from the Win7 installation DVD and installing to the unallocated space.

If you don't gave a GParted LiveCD, go to distrowatch.com, download it from there and burn it to CD.

---

### Post by raymondh on 2010-10-03
> **Mark Phelps said:**
> Linux (and Ubuntu) don't use the MS Windows "Drive Letters" scheme, so saying you want to install Ubuntu on "D" or "E" is confusing.

It looks like you might have wiped Win7 from "D" when you installed Ubuntu to it.  There's no second NTFS partition in the fdisk list (which is bad news) and you said you saw no volume for it in Places.

My recommendation (others may vary) for formatting a drive for what you want to do is the following:
1) Partition #1 - Primary, NTFS, WinXP
2) Partition #2 - Primary, NTFS, Win7
3) Partition #3 - Extended
4) Partition #4 (inside Partition #3) - Logical, Ext4, Ubuntu
5) Partition $5 (inside Partition #3) - Logical, Linux-Swap

You can do what you want by booting a GParted LiveCD, shrinking the current XP partition to make room for Win7, and then booting from the Win7 installation DVD and installing to the unallocated space.

If you don't gave a GParted LiveCD, go to distrowatch.com, download it from there and burn it to CD.

If you're OK with with Mark's suggestion ....

Do you want to do a automated install or partitioning ... or do you want to set up the partitions for win7 and Ubuntu?

If you still need a step-by-step, help me visualize your HD ... sometimes pictures help a lot :)

In ubuntu, access gparted.  Take a screenshot of what gparted outputs and post back.

While doing that, decide and post back how much space you want to allocate for XP, win 7, Ubuntu and SWAP.

[Some reading if you wan]("http://ubuntuforums.org/showthread.php?t=282018")t.

If you no longer need assistance, kindly mark your thread closed.

Welcome to the forums.

---

### Post by Majidjan on 2010-10-04
> **raymondh said:**
> If you're OK with with Mark's suggestion ....

Do you want to do a automated install or partitioning ... or do you want to set up the partitions for win7 and Ubuntu?

If you still need a step-by-step, help me visualize your HD ... sometimes pictures help a lot :)

In ubuntu, access gparted.  Take a screenshot of what gparted outputs and post back.

While doing that, decide and post back how much space you want to allocate for XP, win 7, Ubuntu and SWAP.

[Some reading if you wan]("http://ubuntuforums.org/showthread.php?t=282018")t.

If you no longer need assistance, kindly mark your thread closed.

Welcome to the forums.
This is a report by Gparted :

[http://s2.kimag.es/view/46729591.png](http://s2.kimag.es/view/46729591.png)

[IMG]http://s2.kimag.es/view/46729591.png[/IMG]
I want to reinstall 3 OS in 3 individual partition , Partition #1 - #2 - #3.
As I have a 250 GB HDD , I will divide it to 100 , 50 & 100 GB for each OS( WinXP, Win7 & Ubuntu)
Thanks.
[IMG]http://s2.kimag.es/view/46729591.png[/IMG]

---

### Post by Mark Phelps on 2010-10-04
> **Majidjan said:**
> I want to reinstall 3 OS in 3 individual partition , Partition #1 - #2 - #3.
As I have a 250 GB HDD , I will divide it to 100 , 50 & 100 GB for each OS( WinXP, Win7 & Ubuntu)

I would do it differently ...

Instead of 100GB for Ubuntu (which is a HUGE amount), I would only allocate 30GB for Ubuntu and create a fourth partition for sharing data -- and format it NTFS.

Also, I would make Partition #3 an Extended partition, and then either (1) manually create root and swap partitions inside that, or (2) let the Ubuntu installer create and format the partitions inside it.

---

### Post by Majidjan on 2010-10-07
> **Mark Phelps said:**
> I would do it differently ...

Instead of 100GB for Ubuntu (which is a HUGE amount), I would only allocate 30GB for Ubuntu and create a fourth partition for sharing data -- and format it NTFS.

Also, I would make Partition #3 an Extended partition, and then either (1) manually create root and swap partitions inside that, or (2) let the Ubuntu installer create and format the partitions inside it.
Hello again.
I have an extra HDD for sharing data .
I don't know how to create swap partition manually. Is it important ? I have 2 GB RAM on my PC. If ubuntu can make it by itself and no problem , let's do that.
what about 4 partition to install 4 OS ? any conflict or problem ?
Thanks.

---

### Post by soldier1st on 2010-10-07
when you installed Ubuntu it took the place of the Windows 7 install so besicaly you overwrote your Windows 7 install with Ubuntu. when you install another os you need to partition the drive(s) properly or issues like this can happen.

---

### Post by Majidjan on 2010-10-07
> **soldier1st said:**
> when you installed Ubuntu it took the place of the Windows 7 install so besicaly you overwrote your Windows 7 install with Ubuntu. when you install another os you need to partition the drive(s) properly or issues like this can happen.
That's right.
But please refer to post 10 & 12 and give me any guide or suggestion .
Thanks.

---

