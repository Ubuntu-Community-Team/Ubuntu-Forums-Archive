---
title: "Recovering partition table"
date: 2012-07-12
forum: General Help
---

### Post by Daneel.Olivaw on 2012-07-12
So.. I had a dual boot and wanted to install Windows. The problem is that I accidentally deleted my /home partition. Apparently when you tell the Windows installer to delete the / partition, it seems to just delete everything. I didn't know that, so f* me :S.

Anyway, now when I turn on my laptop, Grub goes to recovery mode (of course). I booted up from a Live USB and couldn't see any partition so y used TestDisk to recover the partition table. Grub still goes to recovery mode. 
If I boot from a Live USB now I can mount every partition and read files so I have the option of using an external HDD to make a complete back up to wipe everything clean and start over, but I'd rather avoid that nuclear option. 
For some reason, GParted sees the whole disk as unallocated. I was planing on re-installing Ubuntu on the / partition but the installer also thinks it's completely unallocated. 

It seems it's the same problem shrimpboi13 had [on this thread]("http://ubuntuforums.org/showthread.php?t=1638750") that has no solution :(

Is there any way of recovering my partition structure?

Thanks in advance for the help and apologizes if my English is not perfect. :)

---

### Post by oldfred on 2012-07-13
Did testdisk recover a valid partition table? Often that just works. But sometimes partitions get renumbered, but UUIDs should be the same and then it works.

Just to see what we can see run the BootInfo report and post link.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.
Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary - uses standard bootinfoscript but adds some extra info
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Daneel.Olivaw on 2012-07-13
> **oldfred said:**
> Did testdisk recover a valid partition table? Often that just works. But sometimes partitions get renumbered, but UUIDs should be the same and then it works.

Just to see what we can see run the BootInfo report and post link.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.
Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary - uses standard bootinfoscript but adds some extra info
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Thanks!
I ran Boot-Info and clicked on recommended repair (BTW, this is the link it created [http://paste.ubuntu.com/1089238](http://paste.ubuntu.com/1089238)). Now it can boot from grub and lets me select which OS I want to start. So this is awesome. Thanks a lot!!

However, while Windows can show the partitions just fine and reed data, and so can the Windows installation wizard, GParted and Ubuntu installation still shows the whole disk as unallocated.

---

### Post by oldfred on 2012-07-13
When you have partition table issues gparted stops working.

Script shows this problem:
> /dev/sda4 ends after the last sector of /dev/sda

drive is total [COLOR=Red]976773168[/COLOR] sectors
But last sector of the extended ls too large:
/dev/sda4         964,879,965   [COLOR=Black][COLOR=Red]9[/COLOR][COLOR=Red]76,784,129 [/COLOR][/COLOR][COLOR=Red] [/COLOR]  11,904,165   f W95 Extended (LBA)[COLOR=Black]

I think this is the easiest way to fix that issue:

[/COLOR][COLOR=Black]First backup partition table.
sudo sfdisk -d /dev/sda > parts_sda.txt
[/COLOR]
[COLOR=Black]Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt



[/COLOR]

---

