---
title: "Have I lost all my data?"
date: 2011-09-06
forum: General Help
---

### Post by aviator1 on 2011-09-06
[I][SIZE=3]Here's the story........

I had a dual boot 320GB HD (Vista/10.04), which was getting full. I installed a new 2TB drive and eventually got 10.04 installed and working fine.

During the initial process, I tried to get all my original drive stuff on to the new drive by using the command "[/SIZE][/I][I][I][SIZE=3]dd if=/dev/sda of=/dev/sdb "

That pretty much screwed everything up, but I finally recovered to the point I am now.

However, when I look at my original 320gb drive, I do not see anything regarding any of my LInux stuff. Using "places\computer\320gb Drive", all I see is the Vista stuff.

Using gparted, I also see only a windows partition now on the original drive.

Any ideas from anyone?

Thanks for all responses.

Dave
[/SIZE][/I][/I]

---

### Post by JC Cheloven on 2011-09-06
Please, from a live session (you don't have a functional ubuntu installed right now, if I understood), with the discs connected, open a terminal and type ```
sudo fdisk -l
``` PLease post back the output so we can see what partitions you do actually have. Thank you.

Note.- no advantage/need to use big fonts (it's used for shouting).

---

### Post by aviator1 on 2011-09-06
> **JC Cheloven said:**
> Please, from a live session (you don't have a functional ubuntu installed right now, if I understood), with the discs connected, open a terminal and type ```
sudo fdisk -l
``` PLease post back the output so we can see what partitions you do actually have. Thank you.

Note.- no advantage/need to use big fonts (it's used for shouting).

Sorry about the big fonts. I meant to resize before I posted. Following is what I get using the command you listed.

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313       29552   226832380    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953514583+  ee  GPT

Disk /dev/sdc: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders
Units = cylinders of 6960 * 512 = 3563520 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00026844

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1126     3915752    c  W95 FAT32 (LBA)

---

### Post by YesWeCan on 2011-09-06
You've formatted your 2TB drive with a GUID partition table rather than the traditional MBR format. Is this what you wanted?

To see the GPT contents
sudo parted /dev/sdb print

---

### Post by aviator1 on 2011-09-06
> **YesWeCan said:**
> You've formatted your 2TB drive with a GUID partition table rather than the traditional MBR format. Is this what you wanted?

To see the GPT contents
sudo parted /dev/sdb print

Hello again. Thanks for your help over the weekend.

The setup on the 2 TB drive is what the Live cd did on its own. I do not know what a GUID partition table is, or a traditional MBR format.

All I know is that it boots up OK on the new drive, and I think during the previous work to get it running, all my data from the 320GB drive was lost.

If it's gone, then there is nothing I can do about it, but rebuild the stuff I lost.

Thanks for any help.

---

### Post by srs5694 on 2011-09-06
For future reference, it's easier to read the output of many text-mode commands if, when posting, you begin the text with a [noparse]```
[/noparse] tag and end it with a [noparse]
```[/noparse] tag. This preserves the columns and spacing, which get lost if you just cut-and-paste it the way you did. I'm adding the tags below, but sometimes the formatting gets lost in such quotes, so it might or might not be an improvement....

> **aviator1 said:**
> ```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313       29552   226832380    7  HPFS/NTFS
```

It seems that your your partitions cover cylinders 1 to 29552, but your disk goes up to cylinder 38913, so chances are your Linux partition(s) have been deleted from the partition table, but the filesystems they contain(ed) probably still exist on the disk. Your best bet at recovering this data is to use [TestDisk,](http://www.cgsecurity.org/wiki/TestDisk) which is included in various emergency disk systems such as [PartedMagic.](http://partedmagic.com/doku.php) You might be able to install it to an Ubuntu installation disk in the "try it now" mode by typing "sudo apt-get install testdisk" in a Terminal window, but I'm not 100% positive of that. In any event, TestDisk can usually recover partitions that are "lost" by searching for filesystem signatures and creating appropriate partition entries around them.

As to how this happened, I'm not sure. Nothing you described doing *should* have done this, so either you did something damaging that you didn't mention or you encountered a bug, a disk hardware failure, or some other unpredictable problem. At this point, your priority should probably be to use TestDisk to recover the partitions; however, you might want to run a SMART utility, such as smartctl or gsmartcontrol, once you've recovered your data to check the disk for hardware defects. (A case could be made for doing this first, but whatever the outcome, you want to recover your data, so you'd probably want to run TestDisk even if the disk is physically failing.) If you remember other commands you might have run, posting whatever details you can recall might let somebody who understands them point out an error, if it was a bad command that did the damage. That way you'd at least know to avoid making the same mistake in the future.

---

### Post by srs5694 on 2011-09-06
> **aviator1 said:**
> The setup on the 2 TB drive is what the Live cd did on its own. I do not know what a GUID partition table is, or a traditional MBR format.

All I know is that it boots up OK on the new drive, and I think during the previous work to get it running, all my data from the 320GB drive was lost.

Don't worry about it. If you're curious, you can read the Wikipedia pages on [Master Boot Record (MBR)](http://en.wikipedia.org/wiki/Master_boot_record) and [GUID Partition Table (GPT).](http://en.wikipedia.org/wiki/GUID_Partition_Table) In brief, MBR is the partitioning system that's been used for 30 years, and GPT is a new system that's seeing increasing use on new computers and on disks that are over 2 TiB in size.

> If it's gone, then there is nothing I can do about it, but rebuild the stuff I lost.

As I wrote in my previous post, I think the chances are good that you'll be able to recover your Linux data from the old disk. That's not certain, though; you'll just have to try TestDisk and see what it can find.

---

### Post by aviator1 on 2011-09-06
> **srs5694 said:**
> For future reference, it's easier to read the output of many text-mode commands if, when posting, you begin the text with a [noparse]```
[/noparse] tag and end it with a [noparse]
```[/noparse] tag. This preserves the columns and spacing, which get lost if you just cut-and-paste it the way you did. I'm adding the tags below, but sometimes the formatting gets lost in such quotes, so it might or might not be an improvement....



It seems that your your partitions cover cylinders 1 to 29552, but your disk goes up to cylinder 38913, so chances are your Linux partition(s) have been deleted from the partition table, but the filesystems they contain(ed) probably still exist on the disk. Your best bet at recovering this data is to use [TestDisk,]("http://www.cgsecurity.org/wiki/TestDisk") which is included in various emergency disk systems such as [PartedMagic.]("http://partedmagic.com/doku.php") You might be able to install it to an Ubuntu installation disk in the "try it now" mode by typing "sudo apt-get install testdisk" in a Terminal window, but I'm not 100% positive of that. In any event, TestDisk can usually recover partitions that are "lost" by searching for filesystem signatures and creating appropriate partition entries around them.

As to how this happened, I'm not sure. Nothing you described doing *should* have done this, so either you did something damaging that you didn't mention or you encountered a bug, a disk hardware failure, or some other unpredictable problem. At this point, your priority should probably be to use TestDisk to recover the partitions; however, you might want to run a SMART utility, such as smartctl or gsmartcontrol, once you've recovered your data to check the disk for hardware defects. (A case could be made for doing this first, but whatever the outcome, you want to recover your data, so you'd probably want to run TestDisk even if the disk is physically failing.) If you remember other commands you might have run, posting whatever details you can recall might let somebody who understands them point out an error, if it was a bad command that did the damage. That way you'd at least know to avoid making the same mistake in the future.

Thanks for the posting advice. I have not posted very often, so I appreciate the help.

I'm just an Ubuntu user, not a programmer type,  and while fairly "fluent" is working with the various Windows OS's, I am a novice when it comes to Linux. However, I sure like it better than MS.

I will give the TestDisk a shot and see what happens.

I didn't use any other commands than the "dd" I mentioned above.

When I was able to get a good LIVE CD and get booted up and installed on the the 2TB drive, it did lock up on shut down. I believe the next boot up was when I noticed the dual boot drive would not boot for either Vista or Ubuntu.

I'll post any results. Thanks very much.

---

### Post by srs5694 on 2011-09-06
> **aviator1 said:**
> When I was able to get a good LIVE CD and get booted up and installed on the the 2TB drive, it did lock up on shut down. I believe the next boot up was when I noticed the dual boot drive would not boot for either Vista or Ubuntu.

It's possible you ran into a bug or a random hardware fault that caused both a system crash and damage to the partition table. It's hard to diagnose such things, though, especially if they're just one-time events. I recommend running a SMART utility on your disks and keeping alert to a recurrence or other problems. Any number of hardware problems (failing RAM, underpowered or failing power supply, overheating CPU, etc.) could account for random system lockups, so if you see that symptom again, it could be you've got a hardware problem. If it locks up consistently at shutdown, though, that suggests a software problem that might be easier to diagnose. If the problem doesn't recur, I'd be inclined to write it off as a random event -- maybe caused by a momentary power blip or some extremely rare bug.

---

### Post by aviator1 on 2011-09-07
> **srs5694 said:**
> It's possible you ran into a bug or a random hardware fault that caused both a system crash and damage to the partition table. It's hard to diagnose such things, though, especially if they're just one-time events. I recommend running a SMART utility on your disks and keeping alert to a recurrence or other problems. Any number of hardware problems (failing RAM, underpowered or failing power supply, overheating CPU, etc.) could account for random system lockups, so if you see that symptom again, it could be you've got a hardware problem. If it locks up consistently at shutdown, though, that suggests a software problem that might be easier to diagnose. If the problem doesn't recur, I'd be inclined to write it off as a random event -- maybe caused by a momentary power blip or some extremely rare bug.


I have not noticed any recurring problems such as lock ups, etc. I think I will go with your one ti,me event scenario, also. Sometimes things just happen.

I think I will modify my configuration with Vista on the 320gb drive, as there are a few programs, which just will not function on Linux.

Could you give me some advice in 2 areas?

First, could you clarify, and identify a SMART utility for me? I was able to load TestDisk from the software center, but cannot fund it on a menu anywhere.

Second, how would I boot up with the primary HD with 10.04, and the secondary HD with Vista if I wanted to use Vista that day?

Thanks very much for your help.

Dave

---

### Post by YesWeCan on 2011-09-07
As you are not a geek yet, I recommend you reformat your drive to MBR. You have no need for GPT and it is not supported consistently by linux tools. For an easier life.

You probably started off with a blank drive and Ubuntu chose to make it GPT without telling you even tho it is smaller than the 2TiB limit. Which is very naughty.

---

### Post by westie457 on 2011-09-07
> **aviator1 said:**
> I have not noticed any recurring problems such as lock ups, etc. I think I will go with your one ti,me event scenario, also. Sometimes things just happen.

I think I will modify my configuration with Vista on the 320gb drive, as there are a few programs, which just will not function on Linux.

Could you give me some advice in 2 areas?

First, could you clarify, and identify a SMART utility for me? I was able to load TestDisk from the software center, but cannot fund it on a menu anywhere.

Second, how would I boot up with the primary HD with 10.04, and the secondary HD with Vista if I wanted to use Vista that day?

Thanks very much for your help.

Dave

a SMART utility is available to use in Disk Utility at the top right corner.

Testdisk is a CLI program - runs in a terminal ```
sudo testdisk
```


If the OSes are on different drives I believe you can choose which drive to boot in the BIOS. Not sure if a Grub menu is needed for that.

---

### Post by YesWeCan on 2011-09-07
+1 Disk Utility

This is how Grub works. It has to have special boot code put at the very start of your disk (unless you are using UEFI booting but this is another complex story and you aren't). This Grub code breaks the standard MBR boot code and this is what causes conflicts when Windows tries to be helpful by checking the integrity of the MBR code, and Windows will repair it. The MBR is a general boot system that is not Windows specific.


The upshot is you want standard MBR code on your 320GB Vista disk and Grub boot code on your 2TB disk. The Ubuntu installer is extremely unhelpful in this regard too because it defaults when you choose "use entire disk" to putting Grub on sda even if sda is not the same disk! And it doesn't give you any warning, unlike the SuSE and fedora installers. To avoid problems for newbies I suggest disconnecting the Windows drive while installing Ubuntu.


Once Ubuntu and Grub are installed to their own disk, you set your bios to boot that disk first. After it boots you run
[COLOR="DarkSlateBlue"]sudo update-grub[/COLOR]
to scan all your disks and add OSs to the Grub menu. Assuming you are using Grub2 and not Grub1 (aka Grub Legacy).

---

### Post by srs5694 on 2011-09-07
> **aviator1 said:**
> I think I will modify my configuration with Vista on the 320gb drive, as there are a few programs, which just will not function on Linux.

Could you give me some advice in 2 areas?

First, could you clarify, and identify a SMART utility for me?

The easiest to use are probably gsmartcontrol and the SMART functions in Palimpsest Disk Utility. The smartctl program is a text-mode tool that produces textual output. Unfortunately, the reports from all of these tools can be confusing. If you need help interpreting them, I recommend posting the details -- either the output from smartctl or a screen shot of gmsartcontrol or Palimpsest.

> Second, how would I boot up with the primary HD with 10.04, and the secondary HD with Vista if I wanted to use Vista that day?

Are you saying you want to install Vista on one disk and Linux on the other? If so, the easiest way is to just do the installation and let GRUB control the boot process by installing GRUB to the MBR of one disk and setting that disk as the defult boot disk in the BIOS. Other boot loaders can do the same, and there are ways to do this with the Windows boot loader, but you'll end up going through GRUB when you boot Linux in any event, so there's very little reason to favor other alternatives, at least unless you've got some specific needs or preferences you haven't mentioned.

> **YesWeCan]As you are not a geek yet, I recommend you reformat your drive to MBR.  You have no need for GPT and it is not supported consistently by linux  tools. For an easier life.[/quote]

I disagree with this advice, although there are advantages and disadvantages both ways. YesWeCan is correct that GPT is not needed on a 2 TB disk said:**
> GPT fdisk (gdisk and sgdisk)[/url] are GPT-enabled workalikes for these, so that's not a big deal. (You can install the GPT fdisk utilities by typing "sudo apt-get install gdisk" in an Ubuntu Terminal window.)

Ubuntu uses GRUB 2 as a boot loader, and GRUB 2 works fine with GPT disks. The main caveat is that if you install GRUB 2 to a GPT disk, that disk should have a [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) to store part of its code. (It *can be* installed without a BIOS Boot Partition, but its operation is likely to be less reliable that way.) Such a partition is easily created, as noted on the Wikipedia page to which I've linked. Creating this partition is the main drawback to GPT from a strictly Linux perspective.

Windows Vista and 7 can read GPT disks, but not boot from them except on UEFI-based computers. If aviator1 were using an older version of Windows and wanted to read the disk from Windows, MBR would have a strong advantage for being compatible with the older version of Windows.

The biggest drawback to MBR is that it uses 32-bit sector pointers, which imposes a limit of 2^32 sectors (2 TiB) on its disks. This limitation is irrelevant to aviator1's 2 TB (1.8 TiB) disk. Another big drawback to MBR is that it uses a hack to get around its limitation of having just four partition slots in its primary partition table: You need to make one of those primary partitions an extended partition and create logical partitions in it if you want more than four partitions total. This hack has created untold confusion over the years, as well as complicating certain operations even for advanced users.

In aviator1's case specifically, IMHO it's probably better to simply stick with how the disk is partitioned now than to change it. Changing from GPT to MBR is itself an extra task that could go wrong, and if Linux or other data are already on the disk, making the change without wiping out the data could be complicated, depending on how the partitions are set up. In other words, if it ain't broke, don't fix it. If the disk doesn't already contain a BIOS Boot Partition, it's worth creating one, but that task can be done more simply than converting from GPT to MBR.

[quote=YesWeCan]This is how Grub works. It has to have special boot code put at the very  start of your disk (unless you are using UEFI booting but this is  another complex story and you aren't). This Grub code breaks the  standard MBR boot code and this is what causes conflicts when Windows  tries to be helpful by checking the integrity of the MBR code, and  Windows will repair it. The MBR is a general boot system that is not  Windows specific.

Be aware that YesWeCan has very strong opinions about how the boot system should work, but they are his opinions. To the best of my knowledge, there's no standards document that says how any of this is supposed to work, so saying that GRUB "breaks the standard MBR boot code" is just his opinion. GRUB works *differently* than the way the Windows boot loader works, but that's very different from it being improper.

[quote=YesWeCan]The upshot is you want standard MBR code on your 320GB Vista disk and  Grub boot code on your 2TB disk. The Ubuntu installer is extremely  unhelpful in this regard too because it defaults when you choose "use  entire disk" to putting Grub on sda even if sda is not the same disk!  And it doesn't give you any warning, unlike the SuSE and fedora  installers. To avoid problems for newbies I suggest disconnecting the  Windows drive while installing Ubuntu.[/quote]

This practical advice I agree with.

---

