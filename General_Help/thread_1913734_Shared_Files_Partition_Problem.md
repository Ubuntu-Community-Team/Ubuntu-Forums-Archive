---
title: "Shared Files Partition Problem"
date: 2012-01-23
forum: General Help
---

### Post by ryanmichaelmcclure on 2012-01-23
I have a dual boot system, Ubuntu and Windows 7. (I only have the Windows for music notation software, and I can't stand to use it). However, I wanted to create a shared folder for documents and media, so I can listen to a song and notate it on Windows but still have it it a neutral location for Ubuntu access.

Here is my partition status:
GPT

1MB-Boot
140GB-Shared
25GB-Ubuntu
70GB-Windows 7

Here's the problem. I created the shared partition with GParted using a FAT32 format, which I knew both could access. Ubuntu can access it perfectly, but Windows calls it "Allocated Space". What do I do?

Also...a tiny problem that bugs me...Ubuntu calls this partition "140GB Filesystem" and I would like it to call it "Shared". Also, disk utility won't allow me to nake it that; rather it names it "SHARED". 

Help on either issue would be greatly appreciated.

---

### Post by Basher101 on 2012-01-23
if you still have nothing stored on your partition, you can reformat it to NTFS (to store files larger than 4 GB) i use a 1 TB shared partition without any issues...

To partition it in windows click start, then right click on "computer" and choose "manage". Wait until a windows pops up and choose "Disk management" which is at the bottom on the left. Now you should be able to see all your partitions (note that all your ubuntu partitions will have **[COLOR="Red"]no names[/COLOR]**, just don't touch them. I will attach a screenshot to show you what they look like). Now click on your 140 GB partition and delete it. Make a new volume with the NTFS filesystem. Once you are done, exit the window. Now click start again, then computer. Now you should see your C: drive and your 140 GB partition. Rightclick on your 140 GB partition and _**rename**_ it to whatever you want. Now it will also show the name in ubuntu.

you are done :popcorn:


regards


edit: note that i have no SWAP partition, i have 8 GB of ram so i did not need one..the red encircled partition with no name is my ext4 partition

---

### Post by ryanmichaelmcclure on 2012-01-23
I actually have my data already on the new partition :( if I were to split that partition on Ubuntu, would I be able to create a ntfs partition and then transfer the files over?

---

### Post by oldfred on 2012-01-23
If you have not used a lot of the 140GB partition you may be able to split it. When you say gpt are you booting with UEFI as Windows64 bit only boots from gpt with UEFI. With gpt all partitions are primary so there are no issues. But if MBR you may have the 4 primary partition limit.

Post this:
sudo parted /dev/sda unit s print

New code for NTFS gpt partition
[http://ubuntuforums.org/showthread.php?t=1822452](http://ubuntuforums.org/showthread.php?t=1822452)

Beside Ubuntu auto mounting a shared partition by label you can create a mount point, call it anything you want and mount it under that. If a permanent partition that you are using you can add an entry to fstab and have it mounted when you boot.


Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Shared NTFS partition - You can also use links
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

I vaguely remember that FAT only allowed capitals in labels.

---

