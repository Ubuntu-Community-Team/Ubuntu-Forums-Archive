---
title: "gparted can't see ntfs partitions of new win7 install"
date: 2010-11-11
forum: General Help
---

### Post by fcuk112 on 2010-11-11
hi,

so i installed win7 ultimate on a 2TB HD and was hoping to dual-boot it with meerkat, i did a standard install and shrunk the partition using win7 disk management to leave 500GB for ubuntu.

problem is ubuntu can't detect the existing win7 install, when selecting advanced setup it just shows one big unallocated partition.

i went back into win7 and extended the partition again, then booted into ubuntu live cd to see if maybe gparted would do the trick.  gparted also cannot detect the existing win7 install and just displays unallocated 1.82TB.

in terminal if i do 'sudo parted /dev/sda print' i get this message:

Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? ^C   

wasn't sure what to write there so i just breaked out of it.

anyone experienced this before?

thanks.

---

### Post by Quackers on 2010-11-11
Is this on a MAC? It seems you have a GPT setup rather than the normal MBR. This is likely to be your problem with Gparted. 
I don't have a link I'm afraid, but if you do a search for GPT or GUID Partition Table you will surely come across posts by srs5694. He has helped several people in your situation. That's the best I can do for you, but somebody else may be more able than me to advise you.

---

### Post by fcuk112 on 2010-11-11
no, it's not on a mac.  it's a shuttle sp35p2 - does it have anything to do with bios settings?

i'll search for the links, thanks.

---

### Post by Quackers on 2010-11-11
I see. I don't think it is a bios problem.

---

### Post by dcstar on 2010-11-12
> **fcuk112 said:**
> no, it's not on a mac.  it's a shuttle sp35p2 - does it have anything to do with bios settings?

i'll search for the links, thanks.

Is the Windows disk a Basic disk or a Dynamic disk?

---

### Post by mister_playboy on 2010-11-12
Does your Windows 7 install boot correctly?

---

### Post by oldfred on 2010-11-12
Some links:
GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
The emergency disks that include GPT fdisk are:
    * SystemRescueCd
    * PartedMagic 
sudo parted /dev/sda unit s print
gdisk -l /dev/sda
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)

[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)

---

### Post by srs5694 on 2010-11-12
The problem is probably that the disk *used to* be a GUID Partition Table (GPT) disk, but it was incompletely converted to Master Boot Record (MBR) form, leaving most of the GPT data behind to confuse partitioning software. If this is the problem, it can be resolved as described  [in  this post of mine in another thread.](http://ubuntuforums.org/showpost.php?p=10022223&postcount=34)

---

### Post by fcuk112 on 2010-11-12
yes, thanks for your help all!  i started off by installing ubuntu and make space using gparted, when i then went to try and install win7 it complained about GPT partitions.  i then tried to do it the other way around and did a clean install of win7 which seems was done not so cleanly.

srs5694, i was able to resolve it by following your instructions from one of the links:

```

OK, then, it looks like you've got a new MBR with residual GPT data, which is confusing GParted. You'll have to wipe the GPT data. Here's how:

Boot your PartedMagic or System Rescue CD emergency disc.
For safety, back up your MBR by typing "dd if=/dev/sda of=sda-backup.mbr bs=512 count=1" and then copying the resulting file (sda-backup.mbr) to a USB flash drive, network share, or some other medium. Be sure to get the if= and of= parameters right, though!
Launch gdisk by typing "gdisk /dev/sda". When asked whether to use the MBR or GPT data, either will work.
Type "x" to enter the experts' menu. The command prompt should change.
Type "z" to "zap" (destroy) the GPT data. Tell it to proceed, but answer "N" to the question about blanking the MBR.

That's it. Windows should boot as it did before and you should now be able to continue your installation of Ubuntu; its installer should now see the same partitions as Windows.

```

gparted could recognise the partitions and ubuntu is now installing...

---

### Post by Dribbel on 2011-05-11
[RIGHT]*Just to let you know your solution worked for me.. Thx!*[/RIGHT]
Hey guys, I pretty much had the same problem:

- I created a few partitions with Ubuntu 11.04 Livediscs GPartEd (on my 1TB disc)
- tried to install Win7 but it complained about GPT Partitions
  so: I deleted all partitions and installed Win7
- booted up in 11.04 Livedisc again: GParted shows me just 'unallocated space'
  then I tried to install Ubuntu anyways coz the installer said it would put it next to Windows. It did, except it saw the other windows install I had (different HDD) and just put it straight over my fresh installed one..

Then I found this thread;
- Installed Win7 again
- ran PartEdMagic Livedisc and deleted GPT
- GPartEd on my Ubuntu 11.04 Livedisc could now see my fresh windows install and I am now running dual-boot Win7/Natty.

Thx :)

> Edit: fuck112's post above me was my solution too

---

### Post by izal on 2012-01-24
i have the same problem and it worked for me. Thank you so much srs5694 and you too fcuk112 for posting the solution:).

---

### Post by schru on 2012-11-01
thanks for solution fcuk112, solved same problem for me also

---

### Post by xovertheyearsx on 2012-12-29
followed the directions and it worked! so i wanted to say thank you!

on a side note, i noticed that the "--zap" option destroys the GPT and leaves the MBR in tact. 

i was hoping to stick with GPT completely and saw that Gparted supports GPT since I was hoping to install multiple operating systems on my machine.  e.g. Windows 7, Windows 8, Ubuntu, Snow Leopard, and Arch.

I'm new to the whole UEFI and GPT standards and it's all been throwing me for a loop since I'm so accustomed to using EFI and MBR standards.

i found a few posts, including the FAQ on the Gparted Website and on SourceForge, that gParted supports GPT. 

My question is that if I wanted to switch back to GPT, should I format the drive completely and start from scratch using Gparted? or should I just continue as is? or should I use another Partition Editor like "gdisk"?

I also read up on the Wiki's, but they all seem to be vague on this one detail.

I'd appreciate any feed back ):P

---

### Post by SilverDrake11 on 2013-01-10
Hello, I had the same problem and was able to solve it by following the gdisk instructions above. Thanks!

Details are as follows: I purchased a new laptop containing Windows 8. I wiped it clean and installed Windows 7. Gparted would not recognize the Windows 7 partition until I wiped the GMT with gdisk.

---

### Post by oldfred on 2013-01-10
Closing thread as it is old. 
But a update for those who keep finding this thread.

While instructions are still ok, as with everything computers there is a newer better way. The author of gdisk, srs5694 created a application just to remove old gpt data, as gdisk is a bit more complex as it is more for complete gpt partition creation & maintenance.

       To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

    

Any other issues should be a new thread.

---

