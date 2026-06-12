---
title: "partition problems"
date: 2009-09-08
forum: General Help
---

### Post by t0mmy9 on 2009-09-08
I decided I wanted XP and Ubuntu dual boot. XP was already installed, so I partitioned 50GB for ubuntu. The installation failed halfway through and I had to restart. I then noticed the partition has stayed but Ubuntu hasn't installed so I chose the minimum disk space for Ubuntu.

Now I have ubuntu already telling me the disk is full and the 50GB partition being labeled as "50GB media" on /dev/sda5.  I installed GParted to try to fix this problem, but the hardrive is being recognised as 50GB less than its original size, the partition not showing up. Is there any way to merge these partitions into one to allow 50GB for Ubuntu without touching the XP partition?

Thanks for any help.

---

### Post by lildigiman on 2009-09-08
make a LIVE CD gParted disk, boot from that, and you should be able to do everything there (because the LiveCD won't rely on running from the Harddrive its trying to work with).

---

### Post by -kg- on 2009-09-09
OK, not quite enough information.  You'll pardon me if I assume you know nothing, but I have to do it in case you don't.

You partitioned 50 GB for Ubuntu?  Did you just shrink your XP partition and leave 50 GB for your installation or did you actually format the partition?  If you formatted it, what file system did you partition it as?  ext3/4, or another?

What method did you select to install Ubuntu?  "Use Largest Contiguous Free Space"?  "Manual Partitioning"?  Were you looking to install Linux under Windows (i.e., WUBI)?

At what point in the installation did it fail the first time?  You said it indicated the disk was full.  Did it successfully install the second or was it the installer that told you the disk was full?

In any case, it sounds likely that you have no information in the 50 GB partition that was created, so you will want to delete that partition and start over.  While a GPartEd Live CD is a great tool for partitioning operations, both now and in the future, it's not absolutely necessary.  Your Ubuntu LiveCD has GPartEd that you can use.  It is used by the installer to create and manipulate the partitions and is accessible from the LiveCD desktop as well (under "System/Administration/Partition Editor").

My suggestion would be to boot to the LiveCD and use GPartEd from there to delete the 50 GB partition, leaving the free space as is for installation.  Then launch the installer from the icon on the desktop.  When you come to the installation method, check the "Largest Contiguous Free Space" radio button and the installer will install to the 50 GB free space that is there.

If you want control over the partitioning process, say, to make a separate /home partition or to use the ext4 file system (ext3 is default under Jaunty), then you will want to choose "Manual Partitioning."  You will need to know what you're doing with this method.

In each of these steps you will need to choose the format type.  You will first need to create a "Swap" partition (I suggest at the end of the free space) equal to around 1 1/2 X the amount of RAM you have installed.

If you are going to create a separate /home or other partitions, you will next need to create a "/" (called root) partition.  You will need approximately 10 GB for this partition, but if you don't anticipate creating any further partitions for the installation, you can use the remaining free space.

You will need to choose the file system at this point, which is where you would choose ext4 as the file system type, if you wish to use it.  As I said before, ext3 is the default for Jaunty.  You will also need to choose the mount point.  You will need to choose "/" for this partition, and there is a menu of other possible mount points to choose from for other partitions, should you wish to create them.

Once you have your partitions created, the file system formats, and the mount points selected, you can proceed with the installation.  It should install normally.  If you have forgotten any steps, the installer "usually" won't let you proceed.

If you were installing under Windows (i.e., WUBI), then you didn't need the 50 GB partition at all.  WUBI installs Ubuntu on the Windows partition.  You would want to delete the 50 GB partition and re-expand your Windows partition into the free space.  If you have scads of room in your XP partition, you could leave it as-is, but why waste space?  Besides, as you said, you had insufficient disk space, so if you're installing using WUBI, that would mean you don't have enough space on your Windows partition.

If you would like more information on partitioning operations in general, click on the link in my signature block.  Not only is there good information on this page, but I have included links to various tools, including the page for the GPartEd LiveCD, on the last page of the tutorial.

---

### Post by t0mmy9 on 2009-09-09
Wow, thanks for such a detailed reply. Yes I did just partition the free space of the XP part of the disk and thats when it crashed.

I downloaded gparted live and burned it onto disk, and after a lot of messing around changing partitions around ive managed to get the partition down to ~500Mb and transfer the rest to Ubuntu. I realise now it would have probably been easier to delete both and start again, but I will use the 500Mb for storage and accept this as solved. Thanks for the help.

---

