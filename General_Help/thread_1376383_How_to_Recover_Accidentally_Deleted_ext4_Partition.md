---
title: "How to Recover Accidentally Deleted ext4 Partition?"
date: 2010-01-09
forum: General Help
---

### Post by Jamie Jackson on 2010-01-09
I created a virtual machine to play around with some things, and in a moment of disorientation, I deleted my *host* system's EXT4 partition in gparted. This is the crucial partition on my host system, as it's got *everything* but /boot on it.

I'm still in the same session right now, and everything is running normally, and all the files are still available, as far as I can tell, but I know I'm going to be hosed if I shutdown.

How do I recover the partition? It's just deleted, I haven't overwritten it.

I'd start a massive backup right now, but I don't have any external drives big enough to handle the backup.

I'm hoping there's some easy way to get this partition back.

Please let me know what I can do, or if I need to provide more info.

Thanks,
Jamie

---

### Post by ibuclaw on 2010-01-09
See here for reference: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Can you open a terminal, and post the output of the following command in ```
 tags:
[CODE]sudo fdisk -lu
```

And I'll guide you through the next steps.

Regards
Iain

---

### Post by Jamie Jackson on 2010-01-09
Thanks for the reply. Will start reading the reference while I wait.

```
jamie@mercury:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3072f6f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *          63      224909      112423+  83  Linux

```

---

### Post by ibuclaw on 2010-01-09
> **Jamie Jackson said:**
> Thanks for the reply. Will start reading the reference while I wait.

```
jamie@mercury:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total **[COLOR="Blue"]625142448[/COLOR]** sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3072f6f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *          63      **[COLOR="Blue"]224909[/COLOR]**      112423+  83  Linux

```

OK, looking at this (have highlighted the interesting bits in bold) we can determine that your missing partition is between sector 224909 and 625142448

First, will see if parted is capable of recovering it, you will need to turn off swap.
```
sudo swapoff -a
```
Then load parted
```
sudo parted /dev/sda
```
You will be brought to a new "(parted) " prompt. Paste in the following to run a rescue on the affected area.
```
rescue 224909 625142448
```
And if it can find it - it will prompt you for recovery.

Regards
Iain

---

### Post by Jamie Jackson on 2010-01-09
While I was reading the link you sent, I read about testdisk, BTW.

It seems to have found my missing partition(s). I want to show you what it displays, in case having a partition of LVM partitions complicates matters:

```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

  TestDisk is free software, and
comes with ABSOLUTELY NO WARRANTY.

Select a media (use Arrow keys, then press Enter):
Disk /dev/sda - 320 GB / 298 GiB - ATA WDC WD3200BEKT-0
Disk /dev/mapper/lvmvolume-home - 161 GB / 150 GiB - WDC WD3200BEKT-00F3T0
Disk /dev/mapper/lvmvolume-root - 53 GB / 50 GiB - WDC WD3200BEKT-00F3T0
Disk /dev/mapper/lvmvolume-swap - 8589 MB / 8192 MiB - WDC WD3200BEKT-00F3T0

[Proceed ]  [  Quit  ]

Note: Disk capacity must be correctly detected for a successful recovery.
If a disk listed above has incorrect size, check HD jumper settings, BIOS
detection, and install the latest OS patches and disk drivers.

```

That looks pretty promising. With this in mind, should I still pursue your "recover" command, or might this be a better tack? Just checking.

Thanks again,
Jamie

---

### Post by Jamie Jackson on 2010-01-09
Oh, and FWIW, it was sda3 that I deleted in gparted. (That's the partition that held these logical volumes.)

---

### Post by ibuclaw on 2010-01-09
> **Jamie Jackson said:**
> 
While I was reading the link you sent, I read about testdisk, BTW.

Hmm... an LVM may complicate things. (Lookup LVM recovery, and you'll see why).

Testdisk would have been my first tool to try out, but given it's extensive features, I'd thought I'd experiment with other simpler tools first. ;)

You can try the parted way first by all means - it won't do any damage if it can't find anything.

Regards
Iain

---

### Post by Jamie Jackson on 2010-01-09
> You can try the parted way first by all means - it won't do any damage if it can't find anything.

[s]You meant "testdisk" instead of "parted," right?[/s] Never mind, sorry. I re-read, and you meant exactly what you wrote.

BTW, testdisk is looking pretty good so far:

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
     Partition               Start        End    Size in sectors
* Linux                    0   1  1    13 254 63     224847
P Linux LVM               14   0  1 38912 254 63  624912435

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, 
     Enter: to continue
LVM2, 319 GB / 297 GiB

```

---

### Post by ibuclaw on 2010-01-09
> **Jamie Jackson said:**
> You meant "testdisk" instead of "parted," right?

I actually meant parted. Although as stated - testdisk is a pretty (awesome) comprehensive tool, and if you are halfway through figuring out recovery now, you might as well continue using testdisk.

> **Jamie Jackson said:**
> 
BTW, testdisk is looking pretty good so far:


Excellent. Let me know how it goes. =)

If you aren't aware - once you have all partitions listed, you can use the **Left** and **Right** arrow keys to change the partition status. ([COLOR="SeaGreen"]Green[/COLOR] = Recover)
If you are unsure whether or not the partition is the correct one, you can use **P** to list all files and directories.
Once you are happy with the listings, you can select **Write** to save the partition table.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by Jamie Jackson on 2010-01-09
Thanks for all the help so far.

parted's recover didn't seem to do anything, BTW:
```
jamie@mercury:~$ sudo parted /dev/sda
GNU Parted 1.8.8.1.159-1e0e
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) rescue 224909 625142448                                          
(parted) rescue 224847 625142448                                      
(parted)           
```

I've chosen to write what testdisk found, and it wants me to reboot, so I'm about to do so with my fingers crossed...

---

### Post by Jamie Jackson on 2010-01-09
No dice. I got a grub error 17 on reboot. :(

I went out and bought a big external HD, so now I've got to figure out how to back up the internal and try again to restore the partition.

Update: I'm back up and running. :)

The scoop: When I recovered the partition with testdisk, it showed up as sda2, whereas it used to exist as sda3. This must have confused GRUB2. I reinstalled GRUB2 from a live cd session, and now I'm all set.

---

