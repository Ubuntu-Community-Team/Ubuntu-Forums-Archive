---
title: "i need to ask something basic about partitions for ubuntu"
date: 2010-03-19
forum: General Help
---

### Post by aviramof on 2010-03-19
when i create partitions manually i create one ext4 with / and one swap and i made bote of them primery on this HD is it ok or am i doing something wrong?
 
because when i looked now after letting ubuntu install it automaticly last time on the biggest amount of free space i discoverd that it created an extended partition.
 
thanks in advance.

---

### Post by sidewalkcynic on 2010-03-19
Sounds like you did not properly partition your installation correctly - try it again.

/ 
swap  
/home

---

### Post by audiomick on 2010-03-19
> **aviramof said:**
> when i create partitions manually i create one ext4 with / and one swap and i made bote of them primery on this HD is it ok or am i doing something wrong?
 
because when i looked now after letting ubuntu install it automaticly last time on the biggest amount of free space i discoverd that it created an extended partition.
 
thanks in advance.
If you let the installer run automatically, it overwrites the drive an installs what you describe. To retain an existing partition structure, you have to choose the "manual" option when the installer gets to the partitioning stage.

It is not "incorrect" to install as is currently the case on your computer. However there are advantages to a partition setup as sidewalkcynic suggests. If you have a separate /home partition, you can, in the event of a future re-install, re-mount the existing /home partition and thereby retain all your documents and user settings.

---

### Post by aviramof on 2010-03-19
ok so how should i set it i have 25.75 GB assign to ubuntu at the moment i can't assign more because i have windows server 2008 on the same HD and i can increase the partition so what should i do?how much to give to swap home and boot(/)?
 
thanks in advance.

---

### Post by psusi on 2010-03-19
You did nothing wrong.  If you want a separate /home, that can be handy if you reinstall since your personal files are separate, though you get much the same just reinstalling without formatting the partition.  You need at least 2-4 gigs for the root, and at least as much swap as physical ram so you can hibernate.  The rest can be /home.

---

### Post by jskandhari on 2010-03-19
Usually Even When you try to make a Manual Partition Try making the Ext4 & swap both in one extended partition...

---

### Post by aviramof on 2010-03-19
ok let me understand i need to create two ext4 partitions one for root one for home and a swap partition and try to make one of the ext4 partitions extended for the swap 
 
the sizes should be 4GB for the root just in case 2 gb for the swap because i only have 2gb and the rest for home.
 
sound simple enaf except the extended partition part i'm not sure ubiquity have this option in manual partitioning option.

---

### Post by jskandhari on 2010-03-19
Here is what i usually do
I create two partitions in windows Disk managment or AMnually in ubuntu live CD

Windows Procedure
1) NTFS format partition.. size what i want my ubuntu OS partition to have.
2) NTFS partition which i want the SWAP to have 2xRAM.
#Both the partition to be consective Linux will automatically configure it to Extended and then create Logical Partitions of the Same size...

Then when i enter the setup in manually selecting the partitions i Select the 1st partition and give it root flag and select the ext3/4 filesystem. and select the 2nd partition and give it the swap flag..

##This was usually done before the Live Cd's kicked in ( for almost all PC/lappy's )

Linux Live Cd Method
1) Create a Extended Partition Size=OS partition + Swap
2) Create a Logical Partition for OS in ext4/3 filesystem in the Extended
3) Create a Swap Partition ( logical i.e. inside the extended itself )

Simply select them and provide the respective flag and you are done :)

hope it helps...

---

### Post by srs5694 on 2010-03-19
First, I think you should understand the primary/extended/logical distinction. The Master Boot Record (MBR) partitioning system used on most x86 and x86-64 systems has a limitation of four basic partitions. These are called *primary partitions*. Because four is a small number of partitions, years ago a hackish workaround was implemented: One of the four basic partitions becomes a placeholder for additional partitions. The placeholder partition is then known as an *extended partition,* and the partitions it contains are called *logical partitions.* Used in this way, you can have up to three primary partitions, one extended partition (which you don't use directly), and an arbitrary number of logical partitions. Because the number of primary partitions is so limited, most people familiar with this system try to use as few of them as possible. Windows must boot from a primary partition, and some other OSes also require primaries. New computers sold in the last few years usually have two or three primary partitions devoted to Windows (the Windows C: drive itself, a sort of "helper" partition, and often one partition with recovery tools.) Linux, by contrast, is happy to reside entirely on logical partitions. Thus, the usual advice when multi-booting is to leave the Windows partitions as they are (aside from shrinking one of them to make room for Linux), create an extended partition, and create as many logical partitions as you like for Linux.

If the computer is to be used only for Linux, or for Linux and certain other OSes (Mac OS X, FreeBSD, maybe a few others), you might want to consider using the GUID Partition Table (GPT) instead of MBR. GPT does away with the primary/extended/logical distinction, it handles bigger disks (MBR tops out at 2TiB), and it stores two copies of all data for improved reliability. Unfortunately, Windows can't boot from GPT disks on BIOS-based computers. To use GPT, you must create a GPT disklabel. It's been a while since I used the Ubuntu installer, so I don't recall if you can do it directly in the installer, but certainly GNU Parted, GParted, and GPT fdisk (but not regular fdisk) can do it from many Linux emergency discs.

Another point: Although it's often advised to shrink the Windows C: partition using Windows tools, you'll probably use Linux tools to create the Linux partitions. These tools will either assign primary/logical status automatically or will enable you to explicitly create extended and logical partitions -- usually the latter. (Fedora's installer is the only tool that comes to mind that does the assignment automatically.)

As for sizes, it depends on how you partition the disk. An Ubuntu installation can take anywhere from a couple gigabytes to ten gigabytes or more. If you put everything in one partition or split off /home but nothing else, all of that will need to go in the Ubuntu root (/) partition. It is possible, though, to create more partitions, which can change the optimum sizes. For instance, you could split /usr off from the root (/) partition. Since /usr is where most program files reside, it's the one that grows the most when you add programs. If you use separate root (/) and /usr partitions, you might devote 2GB to root (/) and 8GB to /usr; but if you don't split these two up, you might want 10GB in root (/). Most new Ubuntu users find it hard to guess how much to devote to different partitions, so they just create one big partition, or maybe split off /home (which is where you'll store your user data files such as your word processing documents, music files, etc.).

---

### Post by aviramof on 2010-03-20
thanks for the information it was most intresting but all i want to do is to create three partition one for root one for home and one for swap and i have no problem that they all will be primary with there own seperate index because i am not about to create hugh amount of partitions i don't need more then four on any of my hd's and that it what i would try to do or maybe i want create home partition now because i don't have a lot 
of space and i don't want my root to be limited to new software will see how it goes..

---

