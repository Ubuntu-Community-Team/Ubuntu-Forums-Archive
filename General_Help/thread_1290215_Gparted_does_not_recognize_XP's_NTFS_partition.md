---
title: "Gparted does not recognize XP's NTFS partition"
date: 2009-10-13
forum: General Help
---

### Post by jwhendy on 2009-10-13
Hi,


I'm trying to resize an NTFS partition using an Ubuntu 8.04 i386 disk I had laying around. When I start up System->Administration->Partition Editor (GParted), I'm shown one partition with these listed attributes:

Partition: /dev/sda1 (with yellow triangle with a ! inside of it)
Filesystem: unknown
Size 74.53 GiB
Used: ---
Unused: ---
Flags: boot

Any thoughts on this? I found on other post here about GParted not being able to see an NTFS external drive and it suggested posting outputs from some other commands, so here are those as well:

```
~$ sudo fdisk -l
Device: /dev/sda1
Boot: *
Start: 1
End: 9729
Blocks: 78148161
ID: 7
System: HPFS/NTFS
```

```
~$ sudo sfdisk -d
/dev/sda1 start=63 size=156296322 Id=7, bootable
/dev/sda2-4 listed with 0's for the entries
```

```
~$ sudo parted /dev/sda1 print
Error: Unable to open /dev/sda1 - unrecognised disk label
Information: Don't forget to update /dev/fstab, if necessary.
```

Any thoughts? This is an HP Compaq 6910p... could it be that it's HPFS/NTFS and not just NTFS? Is this some sort of journaling or something??


Best regards,
John

---

### Post by justleen on 2009-10-13
Try install ntfs-3g on that live system? just a hunch...

Edit:
try parted /sda  instead of sda1

---

### Post by mike555 on 2009-10-13
Are you running Ubuntu from the Live CD ? Usually a person gets that sign when the partition is mounted .

---

### Post by az on 2009-10-13
Does the machine boot?

Parted is telling you that it doesn't recognize the disk label.  That means that the partition table on it is either of another type or is slightly corrupted.  If it's corrupted or nonstandard and the machine is still able to boot, then the BIOS is choosing to ignore the problem and let you access the drive.  If you were to partition the disk, there is no guarantee than you will be able to safely move your data around.

Fix the partition table.

If there is only one partition on the drive, then use Testdisk to try to detect and repair the partition table.  You may need to create a blank partition table before you do that.  Don't worry, erasing a partition table does not erase any data - it may make your computer unable to access the information, but if you have to ability to boot a live cd and fix the problem, then that's not such a big issue.

If there is more than one partition on the drive, then I would suggest you still go ahead, just make a mental note of where the partition should be before you erase the partition table, just in case you are presented with multiple possibilities.

---

### Post by brookie on 2009-10-13
> **justleen said:**
> Try install ntfs-3g on that live system? just a hunch...

+1...I had the same issue running gparted on Intrepid. After installing ntfs-3g through synaptic the yellow warning mark disappeared and gparted recognized my ntfs drives.

---

### Post by jwhendy on 2009-10-13
Wow these forums are amazing. I can't believe I have 3 responses in like 3min!

To reply to the posts...

- I'm booting from the 'try ubuntu without doing anything' option of a real install disk (not a live CD)

```
~$ which ntfs-3g
/bin/ntfs-3g
```

```
~$ suo parted /dev/sda print
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition table: msdos
Number:1
Start: 32.3kB
End: 80.0GB
Size: 80.0GB
Type: primary
File system: blank
Flags: boot
```

- The machine boots fine. Is there a way to look at the partition table from Win XP? I can try Testdisk but will have to wait until I'm at home to burn a CD.

- As far as I know, there's only one partition and it's a working Win XP Service Pack 2 installation.

Still think it's a bad partition table? Any other way to verify this?

More thoughts?


Thanks!
John

---

### Post by P4man on 2009-10-13
you need ntfsprogs for gparted to be able to read/resize ntfs partitions

```
sudo apt-get install ntfsprogs
```

I thought it was installed by default on live cds, but perhaps only on recent versions?

---

### Post by justleen on 2009-10-13
> **P4man said:**
> you need ntfsprogs for gparted to be able to read/resize ntfs partitions

```
sudo apt-get install ntfsprogs
```

I thought it was installed by default on live cds, but perhaps only on recent versions?

I think the ntfs support for (g)parted was added in 9.xx? Since then the installed could resize NTFS partition during the setup too, if im not mistaken..

Since he can get the partition details, i dont think its a bad partition.. you would get errors about the partition boundaries otherwise

---

### Post by jwhendy on 2009-10-13
Thanks for the continued replies. My reply:

- To restate... this is NOT a live CD. This is an install CD from which I am choosing the 'Try Ubuntu without doing anything' option at the boot up screen. It is the same CD I used to resize my wife's ntfs partition and the same CD I used to install ubuntu on her computer...

- From GParted: GParted menu-> show features brings up a window with file system types and either checks or stop signs in GParted ability categories. NFTS shows green checks all the way across (detect, read, create, grow, shrink, move, copy, check, read label).

```
~$ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree
Reading state information... Done
ntfsprogs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove, and 1 not upgraded.
```

More ideas?


Best regards,
John

---

### Post by justleen on 2009-10-13
> **jwhendy said:**
> Thanks for the continued replies. My reply:

- To restate... this is NOT a live CD. This is an install CD from which I am choosing the 'Try Ubuntu without doing anything' option at the boot up screen...


That would be what "we" call a Live-cd :)

---

### Post by jwhendy on 2009-10-13
Re. 'live cd'... Ah :)

Thanks for the clarification!

Is anyone sure that it's not messing up due to it being HPFS/NTFS rather than 'straight' NTFS? That makes me wonder...


John

---

### Post by az on 2009-10-13
> **jwhendy said:**
> 

- The machine boots fine. Is there a way to look at the partition table from Win XP? I can try Testdisk but will have to wait until I'm at home to burn a CD.

You can use testdisk from the cd you already have.  Just install it in the live session.  The only problem would be if you aren't connected to the internet while you are running the live cd.



> **jwhendy said:**
> Still think it's a bad partition table? Any other way to verify this?

You already did that:
~$ sudo parted /dev/sda1 print
Error: Unable to open /dev/sda1 - unrecognised disk label



> **jwhendy said:**
> 

Is anyone sure that it's not messing up due to it being HPFS/NTFS rather than 'straight' NTFS? That makes me wonder...


John

NPFS/NTFS refers to the partition type, not the actual filesystem on the partition.  Don't worry about that.

---

### Post by jwhendy on 2009-10-13
Ok, here we go with testdisk:

```
~$ sudo testdisk
```
Screen comes up with:
```
Select a media:
Disk /dev/sda - 80GB/74GiB
```
I select 'Proceed'

Next screen:
```
Please select the partition table type:
```
I select 'Intel'

Next screen:
```
Disk /dev/sda - 80GB / 74 GiB - CHS 9729 255 63
```
and list of options. I select 'Analyse'

Next screen (yes, it's listed twice as shown here):
```
Current partition structure:
Partition Start End Size in sectors
Invalid NTFS boot
1 * HPFS - NTFS 0 1 1 9728 254 63 156296322
1 * HPFS - NTFS 0 1 1 9728 254 63 156296322
```

I select Proceed.

```
Should TestDisk search for a partition created under Vista?
```
I answered 'N'... then went back and said yes again.

Both times, the output of TestDisk after going through all the cylinders was:
```
Structure: Ok
```

I'm checking through this link right now: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step).

Will post back with results. So far, it matches that tutorial to a tee (duplicate partitions listed).


Best regards,
John

---

### Post by jwhendy on 2009-10-14
bump... everyone was being so helpful and I think it's so close to being able to figure out the issue! Then the posts stopped...

What should I do now that testdisk cannot find any partitions?


John

---

### Post by jwhendy on 2009-10-14
Whoops... somehow a post of mine didn't actually get posted!

Following my previous post that the testdisk results were mimicking the tutorial... that wasn't actually the case.

Following the search, all that was listed on my screen was 'Structuer:Ok' with no partitions, and no options other than [Back] or something like that. I did a 'Deeper search' and had it look for Vista partitions (even though it's XP) and still got nothing.

After selecting [Analyse], I have this screen: [http://www.cgsecurity.org/wiki/File:Analyse.gif](http://www.cgsecurity.org/wiki/File:Analyse.gif)

Except, testdisk only shows the duplicate first partitions, not any others. I also only have a [Search] option, not [Quick search]. After the search, I get the Structure:OK message, but nothing else.

I'm stuck!



John

---

### Post by mechro on 2009-10-14
> **jwhendy said:**
> 

What should I do now that testdisk cannot find any partitions?



Are you saying that because it said "structure OK"?

Or are you saying that because you followed the TestDisk step by step instructions (Search, Deeper Search, etc.) and it couldn't find any partitions?

**Edit: Please ignore. Post posted after you posted but before I read what you posted while I was posting my post.**

---

### Post by jwhendy on 2009-10-14
No problem - indeed, no partitions found after search, deeper search, with and without trying to detect vista partitions...

I watched it several times scan all cylinders and not find anything...


John

---

### Post by az on 2009-10-14
> **jwhendy said:**
> No problem - indeed, no partitions found after search, deeper search, with and without trying to detect vista partitions...

I watched it several times scan all cylinders and not find anything...


John

I'm not really clear on what you are describing.  Did you clear your partition table before running testdisk?

Once it detects a partition that is not already in the partition table, it will prompt you to ask if you want it added to the partition table.

---

### Post by jwhendy on 2009-10-14
Ok, here's the play by play again. I'll use screenshots from this site where possible ([http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)).

- boot up from 8.04 disk and choose 'Try ubuntu without doing anything' (or whatever it is)
- use synaptic to install testdisk
- run 'sudo testdisk' from terminal
- brought here: [http://www.cgsecurity.org/wiki/File:Create_log.gif](http://www.cgsecurity.org/wiki/File:Create_log.gif)
- choose [Create]
- brought here: [http://www.cgsecurity.org/wiki/File:Select_disk_update.gif](http://www.cgsecurity.org/wiki/File:Select_disk_update.gif)

- except, I only have one listing
--- Disk /dev/sda - 80GB / 74 GiB

- choose [Proceed]
- brought here: [http://www.cgsecurity.org/wiki/File:Partition_table_type.gif](http://www.cgsecurity.org/wiki/File:Partition_table_type.gif)
- choose [Intel]
- brought here: [http://www.cgsecurity.org/wiki/File:Menus.gif](http://www.cgsecurity.org/wiki/File:Menus.gif)
- choose [Analyse]
- brought here: [http://www.cgsecurity.org/wiki/File:Analyse.gif](http://www.cgsecurity.org/wiki/File:Analyse.gif)

- except, I only have two listings (both identical)
--- Invalid NTFS boot
--- 1 * HPFS - NTFS 0 1 1 9728 254 63 156296322
--- 1 * HPFS - NTFS 0 1 1 9728 254 63 156296322

- also, my only options are [Proceed] and [Backup], not [Quick search] and [Backup]
- choose [Proceed]
- brought here: [http://www.cgsecurity.org/wiki/File:Vista_check.gif](http://www.cgsecurity.org/wiki/File:Vista_check.gif)
- say 'y' to search for Vista partitions even though this is XP
- brought here: [http://www.cgsecurity.org/wiki/File:Quick_search.gif](http://www.cgsecurity.org/wiki/File:Quick_search.gif)
- after done, brought here: [http://www.cgsecurity.org/wiki/File:First_results.gif](http://www.cgsecurity.org/wiki/File:First_results.gif)

- except, there are no partitions shown. My screen looks like:
--- TestDisk 6.8, Data Recovery Utility, August 2007
--- Christophe GRENIER <email>
--- [http://www.website.org](http://www.website.org)
--- Disk /dev/sda - 80 GB / 74 GiB - CHS 9730 255 63
--- Partition Start End Size in sectors
---bunch of blank lines
---Structure:OK
---Keys A: add partition, L: load backup, Enter: to continue
---NOTHING else is shown; none of that stuff shown in the picture is on my screen

- press [Enter] to proceed

- brought to a new screen, everything is the same up to the line:
--- Partition Start End Size in sectors as listed above, then:
--- No partition found or selected for recovery
--- [Quit] [Search!]
--- when highlighting [Search!] there is text under it that says 'Search deeper, try to find more partitions'

- choose [Search!]
- brought here again: [http://www.cgsecurity.org/wiki/File:Quick_search.gif](http://www.cgsecurity.org/wiki/File:Quick_search.gif)
- when search done, I'm brought back to the screen described as above
--- no partitions listed
--- just says Structure:Ok and add partition, load backup, or enter to proceed

- press [Enter] and it says the same thing as after the 'Quick search'
--- No partition found or selected for recovery
--- only one option: [Quit]

So, I guess my question is what to do from here? I'm pretty much taking suggestions on what to do and was pointed to the direction of testdisk... I don't know what to do with it.

My objective: shrink my NTFS partition about 12GB so I can add a 10GB Linux partition and 2GB swap partition. How might I accomplish this? Why did everyone recommend testdisk?


Best regards,
John

---

### Post by mechro on 2009-10-14
Is there no point in the procedure where you can select one of these and press P?...

```
Current partition structure:
Partition Start End Size in sectors
Invalid NTFS boot
1 * HPFS - NTFS 0 1 1 9728 254 63 156296322
1 * HPFS - NTFS 0 1 1 9728 254 63 156296322
```

---

### Post by jwhendy on 2009-10-14
Nope... I never have the chance to select anything. At the screen you referenced, the only options are to [Proceed] (Try to locate partition) or [Backup].

When it's done searching, since none are listed, there's nothing to select.

If from the main screen, I choose [Advanced], my screen is like this:

- Disk /dev/sda - 80GB / 74 GiB - CHS 9730 255 63
- Partition Start End Size in Sectors
- 1 * HPFS - NTFS 0 1 1 9728 254 63 156296322

And my options are:
- [Type]: Change type, this setting will not be saved on disk
- [Boot]: Boot sector recovery
- [Quit]

The [Geometry] and [Options] choices from the main menu take me to screens to change geometry (have no desire to do this) or do nothing (there are no options listed from the [Options] menu choice except to go back).

I don't know what the [MBR Code] will do... and am not sure that I want to 'Write TestDisk MBR code to first sector'.

Thoughts?


Best regards,
John

---

### Post by mechro on 2009-10-14
> **mechro said:**
> Is there no point in the procedure where you can select one of these and press P?...

```
Current partition structure:
Partition Start End Size in sectors
Invalid NTFS boot
1 * HPFS - NTFS 0 1 1 9728 254 63 156296322
1 * HPFS - NTFS 0 1 1 9728 254 63 156296322
```

If the answer's no then follow az's advice and select [Delete] here...

[http://www.cgsecurity.org/wiki/File:Menus.gif](http://www.cgsecurity.org/wiki/File:Menus.gif)

then Analyse and Search etc again. You are trying to identify which of the HPFS-NTFS entries is valid for your Windows installation. When you know which one it is, you'd mark it as Primary bootable and mark the other one as Deleted and then Write.


**Edit: This posted before your last reply but still relevant, I think.**

---

### Post by az on 2009-10-14
Yes.  The current partition table is invalid.  Erase it and start over.

---

### Post by jwhendy on 2009-10-14
Ok... I'm willing to try that, but am a little worried about the risk!

This is a work computer. What's my chance of really blowing this?? Will choosing delete have any possibility of preventing the currently functioning windows partition from booting properly?


Best regards,
John

---

### Post by mechro on 2009-10-14
Well yes there is a risk but it will be fixable with help and support.

If it was me, work - no, at home - yes. You could  do a repair/recovery install using a Windows disk and hope that would repair the Partition table.

---

### Post by mechro on 2009-10-14
You could sit back, relax, have a coffee and have a rethink why you're doing this. Why are you doing it? :D

---

### Post by jwhendy on 2009-10-14
True, true. I just want to use Linux at work. I've done this all before, so I thought it would be a snap to just resize the partition with GParted and setup a dual boot option for myself. Turns out this one is not that easy!

I've been using VirtualBox for now, but it's just slow and I think the CPU/RAM limits it imposes on the guest OS have been causing me crashes. I wanted to give a full install a shot and see if I noticed a difference.

Maybe it's just not worth it. I've liked my buggy VirtualBox experience enough over XP that I wanted to persist a bit and see if there was any way possible to go through with it.

Is there a way to make a backup table, try the delete/rewrite, and resort to the backup if needed with little/no risk or would I be looking at the chance of turning my comp into a brick?


John

---

### Post by az on 2009-10-14
> **jwhendy said:**
> 
Is there a way to make a backup table, try the delete/rewrite, and resort to the backup if needed with little/no risk or would I be looking at the chance of turning my comp into a brick?


John

You can make a backup using testdisk.  Once you analyse the drive, you get the option of making a backup.  You won't need it since the partition is clearly there and hard to miss.  You will be able to add it back to the block partition table.

---

### Post by jwhendy on 2009-10-14
I'm willing to try it, but would prefer to have the exact steps.

I just went to the [Delete] option but was only asked if I wanted to rewrite the current table with 0s, not anything about a backup.

At the [Analyse] menu, I can either do [Proceed] to search or [Backup] to write the list of current partitions to disk... is this what I should do to create a backup in the event I need to restore this?

I've also got the numbers written down, so I suppose I could manually reenter start/stop and sizes if I had to.

So... where would I make a backup? and how do I add in the 'correct' partition afterward?

I don't see these instructions on the TestDisk site.

I tried [Rebuild BS] to rebuild the bad NTFS boot, and it plugged through cylinders for a long time and then told me that a valid NTFS boot sector must be present to access any data; even if the partition is not bootable.

I tried [Repair MFT] but that didn't work either - needs a valid NTFS boot.

Anyway, steps?
- [Delete] from main menu
- then what?


John

---

### Post by az on 2009-10-15
If I were at home, I would do it and tell you the exact steps.  I will not do it from memory, since that could lead you to following the wrong sequence. 

However, it is straightforward.  I have no doubt that once you delete your partition table, testdisk will be able to recover the partition and write it to the partition table.  That new partition table will be fine.

---

### Post by jwhendy on 2009-10-15
Alright - I'll give it a whirl and post back about it.


John

---

### Post by mechro on 2009-10-15
I'm probably a bit late but have you tried fixing the mbr from XP (you need an XP disc to get the recovery console)?...

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

---

### Post by speed32219 on 2009-10-16
not to hijack this thread, but I have a very similar problem, and maybe a few of you could give me a little guidance before I trash it completely.

ubuntu@ubuntu:~$ **sudo sfdisk -d**
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start= 63, size=312560577, Id= 7, bootable
/dev/sdb2 : start= 0, size= 0, Id= 0
/dev/sdb3 : start= 0, size= 0, Id= 0
/dev/sdb4 : start= 0, size= 0, Id= 0

ubuntu@ubuntu:~$ **sudo parted /dev/sdb1 print**
Model: Unknown (unknown)
Disk /dev/sdb1: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number Start End Size File system Flags
1 0.00B 160GB 160GB ntfs

I had Windows and Ubuntu installed to one sdb1 as a dual boot, and a single NTFS partition on a second HDD sdb0. GRUB was my bootloader, installed to the MBR of the first sdb2.

I was installing Ubuntu ussng a live CD to a USB drive with a copy of GRUB also and I configured it to boot from the USB drive, GRUB works and the system boots fine from the new USB flash drive **BUT** when re-configured to boot from the HDD (the previous configuration), GRUB craps out, I just get the word GRUB on the screen during boot. Also, the partitions on the sdb2 are borked. I should have an NTFS partition and an ext3 partition (and presumably a swap partition), but I only show a NTFS partition that is somehow corrupted; it will not mount and spits errors when I tries to look at it with gParted. 

I also tried to run chkdsk on it from the XP disk but the message is spites out immediately is too many errors on drive.

**TestDisk 6.9, Data Recovery Utility, February 2008**
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdb - 160 GB / 149 GiB - CHS 19457 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 19455 254 63  312560577
[B]D HPFS - NTFS              0   1  2 19456 254 63  312576641
[/B]
Structure: Ok.  Use Up/Down Arrow keys to select partition.
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
**NTFS found using backup sector!, 160 GB / 149 GiB**

But if I select P to list files it tells me "Can't open filesystem. Filesystem seems damaged."

Need assistance in what to do next to get drive back, or least get some of the files off that I neglected to backup in the last 3-5 months.

---

### Post by alphaniner on 2009-10-16
One thing a lot of people don't realize is that modifying the partition table *absolutely does not affect the data on the disk*.  **At all**.  If you create a partition encompassing half of the disk, for example, this doesn't cause anything to be written to the 'middle' of the disk to designate the end of the partition.  Rather, all that is modified is a 64 byte block of the [[COLOR="Red"]MBR[/COLOR]]("http://en.wikipedia.org/wiki/Master_boot_record").

I recently wiped the partition table on my active system disk (containing /, swap and a 'data' partition, all mounted and in use) by accident in fdisk.  I created a new empty partition table, then created one partition encompassing the whole disk.  Luckily, fdisk spat an error (though it did write the changes) so I quickly realized what I had done.  I rebuilt the table 'by hand' from the output of
**fdisk -l** and reinstalled GRUB as a precaution and that was that.

The point is, don't be afraid to use tools that modify the table.  And if you want to be extra cautious, you can make a backup of the MBR using```
dd if=/dev/sd_ of=/path/to/image bs=512 count=1
```
and restore it using```
dd if=/path/to/image of=/dev/sd_ bs=512 count=1
```

Actually you don't need the **bs** or **count** flags in the second command, but it doesn't hurt.  And it will save your butt if you accidentally choose the wrong input file.

---

### Post by jwhendy on 2009-10-16
Interesting development...

I used my wife's XP Home Service Pack 2 disk to boot into the recovery console... and was told 'Windows cannot find any hard drives attached. Make sure any hard drive devices are plugged in and powered on now' or something like that. It said it could not continue further and would reboot.

Weird.

I guess testdisk is my only real option?

Any last suggestions before I go for the delete/add through testdisk? I can try the dd option to make a backup of the current table just in case. It's at least working now, so for whatever reason that is, I don't want to botch it.

Last question - is there any kind of 'mass output' method of installing OSs that could be the cause of this weirdness? I just keep wondering if it's something my company (30,000 employees or so in the US) does... how it installs disk images or this thing called safe boot?


John

---

### Post by alphaniner on 2009-10-16
> **jwhendy said:**
> Interesting development...

I used my wife's XP Home Service Pack 2 disk to boot into the recovery console... and was told 'Windows cannot find any hard drives attached. Make sure any hard drive devices are plugged in and powered on now' or something like that. It said it could not continue further and would reboot.

Most likely the HDD is SATA and Windows does not include drivers for the controller.  I don't know how common it is, but it's not evidence of a hardware problem or anything.  If you have a driver disk you are prompted to hit F6 at the very beginning of the install process to load the necessary drivers.

> Last question - is there any kind of 'mass output' method of installing OSs that could be the cause of this weirdness? I just keep wondering if it's something my company (30,000 employees or so in the US) does... how it installs disk images or this thing called safe boot?

Yes, there are numerous methods of mass installation.  My company uses 'Image for DOS' and 'Image for Windows' for some of our products.  It's kind of like a DIY version of the restore process with PCs from Dell, HP, etc.  Safe boot could be something to do with this; there's also Windows Safe Mode but that's something else entirely.

---

### Post by jwhendy on 2009-10-16
Just deleted the partition table via testdisk...

It's still not finding anything when I do the [Analyse] option. I'm stuck now as how I might do the add thing... how do I write the correct partition table to disk now?


John

---

### Post by jwhendy on 2009-10-16
Ok... I just used fdisk to recreate a partition after deleting via testdisk.

Here's my remaining question before I try a reboot: In my first researchings, I did an fdisk -l and an fdisk -d.

~$ sudo fdisk -l
Device: /dev/sda1
Boot: *
Start: 1
End: 9729
Blocks: 78148161
ID: 7

and

~$ sudo sfdisk -d
/dev/sda1 start=63 size=156296322 Id=7, bootable

What should my new partition table say? Start at 1 or 63? I'm leaning toward 63 since I figure the MBR is 0-63?

Also, now sudo sfdisk -d returns:
/dev/sda1 start=996030, size 15530055, ID=7, bootable

Any input on how to get this guy set straight again?


John

---

### Post by jwhendy on 2009-10-16
Any suggestions?

I just need a little help re-writing the partition table with something that doesn't tell me it's an invalid NTFS boot. Testdisk still doesn't find anything. Was deleting the old table supposed to help it find something new via [Analyse]? The results are the same so I'm not seeing how I go about adding a new table via testdisk.

testdisk?
fdisk?

Anything?


john

---

### Post by mechro on 2009-10-16
> **jwhendy said:**
> Just deleted the partition table via testdisk...

It's still not finding anything when I do the [Analyse] option. I'm stuck now as how I might do the add thing... how do I write the correct partition table to disk now?


John

Are you saying that Testdisk is still not giving you a search option?

---

### Post by jwhendy on 2009-10-16
If by search, you mean [Analyse] from main menu, then [Intel] as partition type, then yes I can search.

After the search, I get the options to [Backup] or [Proceed] and after [Proceed] I get 'no bootable partitions found' and an option to [Quit] or do a deeper search, which also returns no partitions.

I'm not getting any options like this: [http://www.cgsecurity.org/wiki/File:First_results.gif](http://www.cgsecurity.org/wiki/File:First_results.gif)

After my search, I've got nothing.

az said there would be some way to add a partition back to the table, but the [Analyse] option isn't doing it for me. I'm wondering if I'm supposed to do something else?


John

---

### Post by mechro on 2009-10-16
> **jwhendy said:**
> 

Last question - is there any kind of 'mass output' method of installing OSs that could be the cause of this weirdness? I just keep wondering if it's something my company (30,000 employees or so in the US) does... how it installs disk images or this thing called safe boot?


John

I don't know, but if I was a large company I'd be quite happy for the IT department to bork Partition tables so employees couldn't fiddle about with the company's kit. :-D

---

### Post by mechro on 2009-10-16
> **jwhendy said:**
> 
After the search, I get the options to [Backup] or [Proceed] and after [Proceed] I get 'no bootable partitions found' and an option to [Quit] or do a deeper search, which also returns no partitions.


It might say "no bootable partititions" but is it giving you a list of anything?

---

### Post by jwhendy on 2009-10-16
And I think if I can get my work done more enjoyably and with higher productivity using an OS I like better that's not susceptible to viruses and doesn't need to get continually slower on me due to gobs of company patches and updates that zap my CPU during the work day... why should they really care? ;)

They might not see it that way, though, so point taken maybe they goofed with the table to make it unreadable. Is that possible/likely?


John

---

### Post by mechro on 2009-10-16
> **mechro said:**
> It might say "no bootable partititions" but is it giving you a list of anything?

Also, at any time do you get a list which has any of the letters P,E,L,*,D down the left hand side?

---

### Post by jwhendy on 2009-10-16
Hmmm, not exactly.

I get this screen: [http://www.cgsecurity.org/wiki/File:Analyse.gif](http://www.cgsecurity.org/wiki/File:Analyse.gif)

But picture only the first two lines, like this:

```

Disk /dev/sda - 80GB / 74GiB - CHS 9729 255 63
Current Partition Structure:
Partition Start End Size in sectors

Invalid NTFS boot
1 * HPFS-NTFS 62 0 1 9728 254 63 155300355
1 * HPFS-NTFS 62 0 1 9728 254 63 155300355

*=Primary bootable, P=Primary, L=Logical, E=Extended, D=Deleted
[Quick search] [Backup]

```

That's what I've got. I can't select either of those partitions or do anything other than the [Quick search] or [Backup] options. In the testdisk tutorial, they do the quick search and from there it seems possible to do things with the found partitions.

I'm doing a quick search right now to see one more time if it finds them. Not sure how it lists two partitions but then doesn't find them through the searches.

---

### Post by jwhendy on 2009-10-16
Search still doesn't produce anything.

After the search where it says 'No bootable partitions found' I can choose A=Add partition, then write the partition table and it says a reboot will be necessary for changes to take effect... but when when going to Analyse, I still see the same duplicate partitions listed and it says 'Invalid NTFS boot'.

Do I need to reboot for testdisk to actually see the changed table it just wrote? I'd like to have some confidence that this is all set before I actually reboot.

Is it bad to see what appears to be 'duplicate' partitions? Or is that just how testdisk lists them? What would a 'normal' teskdisk output look like?


John

---

### Post by mechro on 2009-10-16
On my system after [Quick Search] I get this...

[http://i36.tinypic.com/2yx2pgy.png](http://i36.tinypic.com/2yx2pgy.png)

... which I ignore, [Continue] gets this...

[http://i33.tinypic.com/icrdy0.png](http://i33.tinypic.com/icrdy0.png)

... which is what we're looking for on your system even if it's not highlighted in green.

---

### Post by mechro on 2009-10-16
> **jwhendy said:**
> Search still doesn't produce anything.

After the search where it says 'No bootable partitions found' I can choose A=Add partition


John

Is there no option to use Left/Right arrow keys?

---

### Post by jwhendy on 2009-10-16
Yikes. I've not seen anything like that at all. I get absolutely nothing after my searches. Perhaps I'll just replace the mbr with the backup I made using dd and just forget about it unless there are any more groundbreaking suggestions?

The only other possibility I could see would be to try a reboot and see if testdisk comes up with anything else?

Or, if someone could let me know what the mbr should be, maybe I could re-write it with fdisk?

What I'm not understanding is why after tinkering around testdisk doesn't seem to show anything different. For example, I deleted the mbr via testdisk, then added one via fdisk, and went back into testdisk and it still listed the duplicate first partitions and said invalid NTFS boot?


John

---

### Post by mechro on 2009-10-16
Sorry but I'm stuck now. If you let Testdisk create a log file then maybe that might give us some clues. The log file should be in Home (until you reboot) - it's testdisk.log and you'll have to "show hidden files" if browsing for it from nautilus.

---

### Post by jwhendy on 2009-10-16
Here's the log: [http://jw.hendy.googlepages.com/testdisk.log](http://jw.hendy.googlepages.com/testdisk.log)

Shouldn't I be able to do what testdisk can with fdisk since I already know the size the partition should be from previous fdisk/sfdisks?

Or does testdisk provide something additional?


John

---

### Post by az on 2009-10-16
> **jwhendy said:**
> Here's the log: [http://jw.hendy.googlepages.com/testdisk.log](http://jw.hendy.googlepages.com/testdisk.log)

Shouldn't I be able to do what testdisk can with fdisk since I already know the size the partition should be from previous fdisk/sfdisks?

Or does testdisk provide something additional?


John
I looked at the log you provided.

Once you delete the partition table, you need to reboot so that the kernel can see the new partition table properly.  

Does tesdisk do anything special?  Well, if the partition was at all non-standard, then it will add the new partition as it is on disk.  Parted also offers the same functionality.  It's called the rescue option.

Once you have deleted your partition, you run parted

sudo parted /dev/sda
print
(it will list no partitions since you cleared it) (It may say there is no label, which means there is no partition table.  Use mklabel to make it.  Take the default msdos table)
rescue
(it will as you for a place to start - the default is the beginning of the drive.  Likewise the end is the end of the drive. Take the default and it will search.  It will ask you if you want to add the found partition(s) to the partition table.  Say yes.

Testdisk is just easier to do.

I'm sorry this is not as straightforward as I said it would be.  I guess I didn't think I needed to mention that you need to reboot after you clear the partition table.

---

### Post by jwhendy on 2009-10-16
I don't think this is an issue of which is more straightforward. I still think there's something wrong.
```

sudo parted /dev/sda
Gnu Parted 1.8.9
Welcome...
(parted) print
Model: ATA Fujitsu MHW2080B (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition table: msdos

Number Start End Size Type File system Flags

(parted) rescue
Start? 0
End? 1000000000
(parted)

```
That's it... no options to add anything, nothing found... just nothing.

Let me know if I missed a step.

John

---

### Post by mechro on 2009-10-16
> **jwhendy said:**
> Here's the log: [http://jw.hendy.googlepages.com/testdisk.log](http://jw.hendy.googlepages.com/testdisk.log)

Shouldn't I be able to do what testdisk can with fdisk since I already know the size the partition should be from previous fdisk/sfdisks?

Or does testdisk provide something additional?


John

I presume testdisk makes full use of the fdisk command. I guess the additional something is the combination of recovery tools it offers.

I'm sorry and embarrassed I can't offer you any more help. My solution on my own kit would be to back-up, wipe my drives, re-partition and re-install.

You could achieve your goal of using Ubuntu at work via a USB flashdrive installation or a boot floppy combined with a nice slimline mobile external drive.

---

### Post by jwhendy on 2009-10-16
Also, there were no defaults for Start? and End?. If I just pressed Enter for those, it just kept printing out 'Start?' prompts. I had to say something so I went with '1' once and '0' another time.


John

---

### Post by jwhendy on 2009-10-16
@Mechro
Yes, the flash drive might have to be my way to go. I thought of that, too. Afterall, I can get one with plenty of space to hold a minimal install for pretty cheap. I just bought an 8GB for like $20-30 or something a bit back. I could do the same and have a good solution to all of this.

Don't be embarrassed :) Who knows what the heck is going on. I'm guessing this is a super odd situation that's pretty fringe compared to most partition problems.


John

---

### Post by mechro on 2009-10-16
> **az said:**
> 
I'm sorry this is not as straightforward as I said it would be.  I guess I didn't think I needed to mention that you need to reboot after you clear the partition table.

Reboot into Windows:!:

---

### Post by az on 2009-10-17
> **jwhendy said:**
> I don't think this is an issue of which is more straightforward. I still think there's something wrong.
```

sudo parted /dev/sda
Gnu Parted 1.8.9
Welcome...
(parted) print
Model: ATA Fujitsu MHW2080B (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition table: msdos

Number Start End Size Type File system Flags

(parted) rescue
Start? 0
End? 1000000000
(parted)

```
That's it... no options to add anything, nothing found... just nothing.

Let me know if I missed a step.

John

That's so weird! No, you didn't miss a step.

From the information you posted previously, your partition is exactly where it should be.  I can't figure out why neither Testdisk nor Parted can find it.  What happens when you do this:

sudo losetup -r -o 32256 /dev/loop2 /dev/sda

That attaches /dev/sda to loop device number 2, with an offset of 32256 which is 63 blocks of 512 bytes.  That's where your partition is, according to your first post.

Next, try mounting it.

mkdir sda1
sudo mount /dev/loop2 sda1

That creates a folder called "sda1" and mounts the loop device there.  Does it mount properly?  It it was uncleanly shut down, it may refuse, but the message it spits out will tell if you found the partition or not.

If that works, then just create an ntfs partition (without creating the filesystem) staring at the beginning of the drive (63 blocks in by default) and using the entire drive.  You will then be able to access your filesystem.  

If this doesn't work, I have no idea.


> **mechro said:**
> Reboot into Windows:!:

No, reboot again into the live cd.  Here, the kernel gets information about the drives from the BIOS.  You need to reboot to have the BIOS refresh what it sees after you change the partition table.

---

### Post by mechro on 2009-10-17
> **az said:**
> 
No, reboot again into the live cd.  Here, the kernel gets information about the drives from the BIOS.  You need to reboot to have the BIOS refresh what it sees after you change the partition table.

Ah! Thanks. Testdisk is pretty clear in asking to reboot after deleting the table so I wasn't sure if you meant it had to be an attempt at booting a drive.

---

### Post by jwhendy on 2009-10-17
Thanks, az. I'll do that right away.

One question - how can I create a partition? Fdisk? or testdisk?

Also, what should the end of it be? The same as the original output of fdisk/sfdisk (posted before)? I'm not familiar with fdisk on linux much. I've used it a lot of OS X, and while I figure they should be the same, they're not quit the same. I was asked for the ending of the drive but it was the ending cylinder (I think), not the ending in whatever-it-is-that-OS-X-asks-for.

For example, fdisk seems to be wanting the beginning as in 1, whereas I would normally have said (as you said) 63. It asked for the end and wanted 9729 or something where as I would have said 156296322.

For reference, here was what fdisk and sfdisk reported originally. Should I recreate a partition to match these findings?

```

~$ sudo fdisk -l
Device: /dev/sda1
Boot: *
Start: 1
End: 9729
Blocks: 78148161
ID: 7
System: HPFS/NTFS

~$ sudo sfdisk -d
/dev/sda1 start=63 size=156296322 Id=7, bootable

```


Thanks!
John

---

### Post by az on 2009-10-17
> **jwhendy said:**
> Thanks, az. I'll do that right away.

One question - how can I create a partition? Fdisk? or testdisk?

Also, what should the end of it be? The same as the original output of fdisk/sfdisk (posted before)? I'm not familiar with fdisk on linux much. I've used it a lot of OS X, and while I figure they should be the same, they're not quit the same. I was asked for the ending of the drive but it was the ending cylinder (I think), not the ending in whatever-it-is-that-OS-X-asks-for.

For example, fdisk seems to be wanting the beginning as in 1, whereas I would normally have said (as you said) 63. It asked for the end and wanted 9729 or something where as I would have said 156296322.

For reference, here was what fdisk and sfdisk reported originally. Should I recreate a partition to match these findings?

```

~$ sudo fdisk -l
Device: /dev/sda1
Boot: *
Start: 1
End: 9729
Blocks: 78148161
ID: 7
System: HPFS/NTFS

~$ sudo sfdisk -d
/dev/sda1 start=63 size=156296322 Id=7, bootable

```


Thanks!
John
I would just use parted

sudo parted /dev/sda
mkpart
Partition type?  primary/extended? primary                                
File system type?  [ext2]? ntfs                                           
Start? 0                                                                  
End? 80GB   

print

quit

---

### Post by jwhendy on 2009-10-18
Everything went fine up until the 'mount' command.

```
~$ sudo mount /dev/loop2 sda1
mount: block device /dev/loop2 is write-protected, mounting read-only
mount: you must specify the filesystem type

```

Fine.
```
~$ sudo mount -t ntfs /dev/loop2 sda1
NTFS signature is missing.
Failed to munt '/dev/loop2': Invalid argument
The device '/dev/loop2' doesnt' have a valid NTFS
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)?
Or the other way around?

```

So, maybe it's hpfs? No dice:
```
~$ sudo mount -t hpfs /dev/loop2 sda1
mount: block device /dev/loop2 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/loop2, 
missing codepage or helper program or other error.
In some cases useful info is found in syslog - try dmesg | tail or so.

```

```
~$ dmesg|tail
HPFS: Bad magic... probably not HPFS
```
But nothing when attempting to mount NTFS.

Something's not clicking with the filesystem type. Not sure what to do from here!


John

---

### Post by az on 2009-10-18
What does this show:
sudo hd -n 50000 /dev/sda|grep NTFS

That does a hex dump of /dev/sda and then searches for the string "NTFS".  The first six characters of an NTFS filesystem contain that string.

---

### Post by jwhendy on 2009-10-18
No dice. I get nothing.

Althouh, bumping it down to 10000... I almost want to say I knew it. I can see this in the margin on the right of the hex characters:

..#SafeBoot ....
random crap
then the bad part...
SafeB
oo.ha.bee.corrup
te....SafeBoo.ha
r.dis.erro.(erro
.00h..........

Not liking that.

So, could it be safeboot afterall? I don't know what it is (not safe mode as someone alluded to earlier) but it's definitely part of the company as I seem to recall having to restart and then wait for them to push through a patch or upgrade to it... Where exactly should NTFS be? The very first thing or just in that 50000 characters somewhere? Safeboot is literally the very first thing.


John

---

### Post by jwhendy on 2009-10-19
Ha! How about this?!

I googled 'SafeBoot' and found out that it's actually device encryption software, recently acquired by McAfee. It's now called Endpoint Encryption or something. From this [SITE]("http://www.mcafee.com/us/enterprise/products/data_protection/data_encryption/endpoint_encryption.html"):

> 'McAfee Endpoint Encryption for Mobile
Secure mobile devices by preventing unauthorized use or access to data on the devices; encrypt standard applications: contacts, calendar, tasks, emails, etc.'

This would explain a lot. It might be pointless to try to proceed, as I think it makes sense that SafeBoot would want to protect data from being explored from means other than the primary OS, right? I mean, if someone stole my work computer and could just pop in a linux CD and look at everything, it would kind if defeat the purpose of things being safe, right?

If people seem to concur that this product could be making it impossible to read this partition or work with it, I'm giving up, getting an 8GB flash drive, and having linux on that.


John

---

### Post by mechro on 2009-10-19
Does your company have an IT policy? If they're encrypting drives, wouldn't they tell employees not to mess with installations?

Perhaps they know what you're up to and are setting you up for early retirement? Just joking! :wink:

This is quite interesting...

[http://www.dslreports.com/forum/remark,15920502](http://www.dslreports.com/forum/remark,15920502)

---

### Post by mechro on 2009-10-19
> **jwhendy said:**
> 
This would explain a lot. It might be pointless to try to proceed, as I think it makes sense that SafeBoot would want to protect data from being explored from means other than the primary OS, right? I mean, if someone stole my work computer and could just pop in a linux CD and look at everything, it would kind if defeat the purpose of things being safe, right?


So perhaps the initial question to you should have been "Can you browse your Windows files using the LiveCD?"

Can you? \\:D/

---

### Post by jwhendy on 2009-10-20
Nope! No browsing. Posted this a bit back

> ~$ sudo mount -t ntfs /dev/loop2 sda1
NTFS signature is missing.
Failed to munt '/dev/loop2': Invalid argument
The device '/dev/loop2' doesnt' have a valid NTFS
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)?
Or the other way around?

Az showed me how to basically make a clone of /dev/sda1 on /dev/loop2 and then when trying to mount loop2 (just like trying to mount sda1), I got the 'Invalid NTFS' error.

Safeboot is probably the reason... I guess it does it's job!

I wonder if the usb linux idea will even work, then... if someone could boot another OS from a flash drive, could they get to my stuff? I might be able to do it, I guess. I can vpn from linux on my Macbook into my work network and then offer it a password for my network drives in fstab, so maybe I can do something similar if/when I get a usb stick working.


John

---

### Post by mechro on 2009-10-21
If there's a Windows network share, Ubuntu should pick it up.

You might be able to test it from the LiveCD. Go to Places > Network.

[https://help.ubuntu.com/community/SettingUpSamba#Browsing SMB shares](https://help.ubuntu.com/community/SettingUpSamba#Browsing SMB shares) > Browsing SMB shares

---

