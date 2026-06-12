---
title: "Dual Boot Advice: choose NTFS or EXT3 for the common partition?"
date: 2010-05-20
forum: General Help
---

### Post by gaussian on 2010-05-20
Background: unlike most posters (I assume) I have been Linux exclusive now for six years. There has been some points during those years that I have been forced to use OS X and some brief experiences with Windows (e.g. when fixing neighbor's wireless connections). I have a Windows XP on Virtualbox on one of my computers for stuff I need it for (occasional complex Office document, GPS and Itunes sync etc). My total Windows Vista/7 experience so far is probably less than two hours.

I have bought a new laptop and I am planning to make it dual boot. It comes with Windows 7. While this almost feels like a betrayal, my kids need Windows for all their gadgets and school (e.g. Powerpoint -OpenOffice Impress conversions are too much of a hassle). And while I could write a long rant about teaching children to use Powerpoint (or Impress for that matter), this is besides the point.


So my question now is as follows: what is the current wisdom about the format of the shared/data partition between Windows and Linux? Should I go ext3? Or NTFS? Why? Any thoughts appreciated. You can assume that I am pretty tech savvy: e.g. I can compile a kernel but I cannot really code too much.

---

### Post by jbrown96 on 2010-05-20
NTFS on Linux is far better than ext3 on Windows, so go with NTFS. I wouldn't even make a dedicated partition to share data; just make your Win7 partition large enough to hold the OS and data, then mount the Win7 partition in Ubuntu. You end up with less wasted disk space, unless you know your disk usage precisely beforehand. 

On a side note, if Office is the main reason for running Windows, then take a look at wine. I installed the wine1.2 packages about three months ago and Office 2007 runs perfect in it.

---

### Post by bumanie on 2010-05-20
As linux has stable read/write to ntfs (and has done for a few years), there is no reason why a shared data partition cannot be ntfs - you will be able to access it from both linux and windows. If you made the shared partition ext3/4, you would have to install a reader in windows for it to be able to read the ext3/4 partition. A superfluous step imo.
That's my opinion, others may think differently. You could use FAT32, which of course, both linux and windows can read/write to, but ntfs is a better filesystem - journaled, can accept larger files etc.
I don't even have a shared partition, I just drag things out of windows if I need them and open office, or media players etc. have no trouble reading/modifying them.

---

### Post by gaussian on 2010-05-20
> **jbrown96 said:**
> NTFS on Linux is far better than ext3 on Windows, so go with NTFS. I wouldn't even make a dedicated partition to share data; just make your Win7 partition large enough to hold the OS and data, then mount the Win7 partition in Ubuntu. You end up with less wasted disk space, unless you know your disk usage precisely beforehand. 

On a side note, if Office is the main reason for running Windows, then take a look at wine. I installed the wine1.2 packages about three months ago and Office 2007 runs perfect in it.

Thanks, this is what I suspected. And the advice for making just two (actually three, counting linux swap) partitions makes sense. 

I will have to take a look at Wine again. Over the years I have used it several times and it has been consistently getting better.

---

### Post by gaussian on 2010-05-20
> **bumanie said:**
> As linux has stable read/write to ntfs (and has done for a few years), there is no reason why a shared data partition cannot be ntfs - you will be able to access it from both linux and windows. If you made the shared partition ext3/4, you would have to install a reader in windows for it to be able to read the ext3/4 partition. A superfluous step imo.
That's my opinion, others may think differently. You could use FAT32, which of course, both linux and windows can read/write to, but ntfs is a better filesystem - journaled, can accept larger files etc.
I don't even have a shared partition, I just drag things out of windows if I need them and open office, or media players etc. have no trouble reading/modifying them.


Thanks. I know I don't want to go FAT32 route for the reasons you state.

---

### Post by jbrown96 on 2010-05-20
Swap isn't necessary unless you want to hibernate (suspend to disk), which is different from sleep (suspend to ram) and doesn't require swap. 

Your computer came with Win7, so it definitely has 1GB+ ram and that's more than enough. 
Here's your basic layout:
1) Maybe have a factory installed recovery partition
2) Windows boot partition (~100MB that's automatically created on Vista and 7)
3) Win7 C:\
3) Linux /
5) Shared NTFS partition (if you don't merge it with #3)

The above would force you into logical partitions, which isn't bad per se, but I find once you need to carve your partitions into logical ones, then you have disk space problems. You run into situations where you need a few more GBs for Win7 or Linux, and it's difficult (not impossible) to fix. 
I also recommend putting /home on a separate parition because it makes reinstalls easier. Again, that puts you at a large number of partitions. 

I had to give a presentation a few months ago, and Impress did not live up to its name. I went with PowerPoint, and was very nervous about the projector, but it worked fine. 
Another option is to virtualize Windows with Virtualbox or Vmware. I don't know whether you've considered that, but it is an option.

---

### Post by gaussian on 2010-05-20
> **jbrown96 said:**
> Swap isn't necessary unless you want to hibernate (suspend to disk), which is different from sleep (suspend to ram) and doesn't require swap. 

Your computer came with Win7, so it definitely has 1GB+ ram and that's more than enough. 
Here's your basic layout:
1) Maybe have a factory installed recovery partition
2) Windows boot partition (~100MB that's automatically created on Vista and 7)
3) Win7 C:\
3) Linux /
5) Shared NTFS partition (if you don't merge it with #3)

The above would force you into logical partitions, which isn't bad per se, but I find once you need to carve your partitions into logical ones, then you have disk space problems. You run into situations where you need a few more GBs for Win7 or Linux, and it's difficult (not impossible) to fix. 
I also recommend putting /home on a separate parition because it makes reinstalls easier. Again, that puts you at a large number of partitions. 

I had to give a presentation a few months ago, and Impress did not live up to its name. I went with PowerPoint, and was very nervous about the projector, but it worked fine. 
Another option is to virtualize Windows with Virtualbox or Vmware. I don't know whether you've considered that, but it is an option.

Thanks. Never had any problems with logical partitions, but I understand the point you are referring to. I don't think I will have to be moving partitions around anytime soon (after installing Ubuntu), the laptop has a 320GB drive.

---

### Post by theozzlives on 2010-05-20
I'd be more concerned about creating a separate /home partition, then you can modify my my "How To" to suite 7 and your needs (like the "home" in Windows is no longer called Documents and Settings, but simply Users).

[http://ubuntuforums.org/showthread.php?t=1244185]("http://ubuntuforums.org/showthread.php?t=1244185")

---

### Post by jarviser on 2010-05-20
Just to throw another option in the thread, like you I have a laptop with Win7 and I only use Win7 for my Canon scanner and nothing else, certainly not for surfing the web.

 I use a standard and large /home partition in ext3 for all my data, which incidentally Windows cannot recognize. If I needed to use Win7 for any other reason like a particularly badly behaved .ppt presentation I will write the files into NTFS C: drive "My Documents" first then reboot into Win7. Doesn't happen often! 

I also use Office 2007 in Wine 1.2 with little problem except you need to add a library riched20 in the wine config panel libraries tab. I have the same Office licence on both Ubuntu and Win7 partitions.

The advantage in having /home as the main (not shared) partition is that all the tools including Office in Wine, Rhythmbox, Bluefish, Filezilla etc have the /home partition as the default and it saves a lot of reconfiguration.

---

### Post by srs5694 on 2010-05-20
> **jbrown96 said:**
> NTFS on Linux is far better than ext3 on Windows, so go with NTFS.

This is the way most people go, and I can't really say I disagree; however, there is one down side: Linux lacks good NTFS maintenance tools, so if you suffer a power loss or other system crash and then boot straight into Linux, the NTFS partition is likely to be unavailable, and will remain unavailable until you boot into Windows to fix the problem. This could be an inconvenience, depending on your use pattern. If you use ext3fs, or even FAT, you won't have this problem. IMHO, this is mostly a concern if you make heavy use of the shared-data partition in Linux and use Linux most of the time -- say, if you store digital photos or MP3 files on that partition and seldom boot Windows. Booting Windows after a system crash might then be an unwelcome annoyance.

> **jbrown96]I wouldn't even make a dedicated partition to share data said:**
> 

I disagree with this advice. The issue is that Linux knows nothing about Windows' security features, and will not honor them. Thus, it becomes easy to accidentally trash a Windows installation from Linux. If you use separate Windows boot and shared-data partitions, OTOH, you need never mount the Windows boot partition in Linux, making accidental damage to that partition much less likely.

[quote=jbrown96]Swap isn't necessary unless you want to hibernate (suspend to disk),  which is different from sleep (suspend to ram) and doesn't require swap.

Although swap isn't necessary, having it as a reserve makes sense -- if a program (or set of programs) creates a short-term spike in memory use, swap will serve as a buffer. Also, the kernel can move seldom-used sections of memory out to swap, freeing up RAM for use in buffers and caches, which can improve performance. 2-8GB of swap space (typical values for today's systems) is very minor compared to modern hard disk sizes (250GB to 2TB). IMHO, it's worth having swap space.

[quote=jbrown96]The above would force you into logical partitions, which isn't bad per  se, but I find once you need to carve your partitions into logical ones,  then you have disk space problems. You run into situations where you  need a few more GBs for Win7 or Linux, and it's difficult (not  impossible) to fix.[/quote]

It's not *that* hard. You've got to boot from a recovery CD/DVD for most partition resizing operations in the first place. Once there, you can resize the extended partition (in which all logical partitions reside) pretty easily. That said, extended/logical partitions can cause problems such as incorrect partition sizes that make all the partitions invisible to parted or GParted.

Also, under no circumstances should you create more than three primary partitions. If you create four primary partitions, and then find you want to resize partitions and add another, you'll have to convert at least one primary into a logical partition, and that operation *is* tricky. Unfortunately, many new PCs these days come with three or even four primary partitions already, so you may have no choice but to use logical partitions for Linux -- and maybe delete or modify at least one of the pre-made partitions.

Overall, I wouldn't hesitate to create extended/logical partitions, and I certainly wouldn't compromise on anything else -- such as a desire to keep separate root (/) and /home partitions -- to avoid doing so.

Before too long, I expect PC makers to start switching to the GUID Partition Table (GPT) system, which doesn't have the primary/extended/logical distinction that's been hanging around our necks like a rotting albatross for these past 25 or 30 years. You can use GPT today for a Linux-only system, but Windows can't boot from GPT on BIOS-based computers. (There is a workaround known as a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) but it's ugly and dangerous.)

> I also recommend putting /home on a separate parition because it makes  reinstalls easier. Again, that puts you at a large number of partitions.  

This I agree with. The Ubuntu installer doesn't do it this way by default, so you'll need to use the "advanced" or "manual" partitioning option. (I don't recall which term is used.)

---

