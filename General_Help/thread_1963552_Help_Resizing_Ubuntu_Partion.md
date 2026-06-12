---
title: "Help Resizing Ubuntu Partion"
date: 2012-04-22
forum: General Help
---

### Post by c152flying on 2012-04-22
I have recently installed Ubuntu 11.10 on my laptop, dual booted with Windows7. During the install, I wasnt given the option of resizing my windows partition, it installed over an old recovery partition, which is far too small. I have reduced the size of the windows partition within windows to free up some unallocated space.
I also have a cpy of GParted live cd, but have not a clue how to go on from here.

Attached is a copy of my hard drive partitions. Any help would be great.

---

### Post by sffvba[e0rt on 2012-04-22
*Thread moved to **General Help**.*


404

---

### Post by oldfred on 2012-04-22
Because of where partitions are on drive it is not so easy to move things around to combine. It could be done but moving is higher risk as any power failure or system shutdown in the middle corrupts everything. Besure to back up everything before making any changes.

I often suggest 10 to 25GB as / (root) if you have separate /home or data partitions. And with Windows you should really only read from the Windows system partition, so if you need to share data another NTFS data partition may be a consideration.

Rather than move partitions you could just use the unallocated as sda4 an make it /home. My / with lots of programs only uses about 7GB of my 25GB partition. But I am agressive in moving data to other data partitions and only have system in system partitions.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by c152flying on 2012-04-22
As I have only just installed Ubuntu, would it be more simple for me to reinstall having first deleted the partition it is in at present? Would the installer then give me the option of using the unallocated space?

---

### Post by oldfred on 2012-04-22
If you also want a shared NTFS data partition you may want to shrink Windows a bit more. Otherwise the unallocated would probably be better for a new install. Which version of Windows, and do you have good backups.

I always partition in advance with gparted and then use the manual installer to choose which partition it /, swap, /home if desired. The auto installer sometimes has issues if you do not have one primary partition available to make the extended partition or enough space. 

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by c152flying on 2012-04-22
Thanks for the info, I will probably do a clean install after re partitioning. I have backed up before the previous install and running windows 7.

---

