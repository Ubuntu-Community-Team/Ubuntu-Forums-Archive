---
title: "Uninstall UBUNTU 11.10 and format HDD"
date: 2011-12-31
forum: General Help
---

### Post by raghavender.s on 2011-12-31
Hey,

I have tried hunting for a solution but could not find any that worked so asking afresh.
I have just 1 HDD with no partitions on it except the one that ubuntu created byitself when installing.

My HDD has no data on it so I dont mind formatting it clean. I want to Clean the HDD Up, install Windows and then Get the laptop to dual boot windows and Ubuntu.

I understand we cant create a Dual Boot once we have Ubuntu Installed. It has to be windows first.

When I try to Boot the laptop off the Windows DVD and try to  install Windows the HDD is shown but the file format is EXT4 something that Windows does not read.

How to I move on from here please?

---

### Post by VanR on 2011-12-31
So Windows won't install because it doesn't recognize the ext4 partition?
I would put a Ubuntu CD in and run it live and open GParted and format the entire drive to NTFS in that case.

---

### Post by 73ckn797 on 2011-12-31
The Windows CD should suggest deleting the partition(s) the formatting and installing Windows. 

You could boot from the Ubuntu CD and run gparted and repartition and setup up several partitions. One for Windows, formatted as NTFS. Another for Ubuntu, formatted as ext3 or 4. Then install Windows to the NTFS partition.

When you have instralled Windows and run the UBuntu install it will ask whether you want to install alongside WIndows and it will handle everything. I would recommend creating a separate /home partition for Ubuntu which will make life much more easier later.

Look here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by vpharry on 2012-01-01
Format it full... install windows on full and then repartition it and install linux on how much space you want
You can install ubuntu first theres no problem in that... Install ubuntu on the amount of space you desire... partition the remaining space to windows format(ntfs). Then you have to boot into ubuntu livecd and reinstall grub. Then boot into ubuntu from your hdd and update grub.

---

