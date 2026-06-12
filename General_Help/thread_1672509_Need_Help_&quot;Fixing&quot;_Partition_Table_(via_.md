---
title: "Need Help &quot;Fixing&quot; Partition Table (via sfdisk)"
date: 2011-01-21
forum: General Help
---

### Post by EarthBoundX5 on 2011-01-21
Ok, so I had a big screw up with my partition table a while back, fixed the issue, but still had problems, then followed some instructions to fix said problems using the command...

```
sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
```

This fixed the problem, but in doing so for some reason I added an empty sda3.

Here is my sudo fdisk -lu output
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x27ee8e40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   238237695   119117824    7  HPFS/NTFS
/dev/sda2       238237696   245473279     3617792    7  HPFS/NTFS
/dev/sda4       283224062   312580079    14678009    5  Extended
/dev/sda5       283224064   307859455    12317696   83  Linux
/dev/sda6       307861504   312580079     2359288   82  Linux swap / Solaris

```

and my sudo sfdisk -d /dev/sda output
```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=238235648, Id= 7, bootable
/dev/sda2 : start=238237696, size=  7235584, Id= 7
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=283224062, size= 29356018, Id= 5
/dev/sda5 : start=283224064, size= 24635392, Id=83
/dev/sda6 : start=307861504, size=  4718576, Id=82

```

I tried simply removing the line for sda3 and renaming the subsequent sdas accordingly, and that just gave me more problems...

The whole point of this is because I want to increase my extended partition to use my 18 GB of free space in front of it, and I think the existence of the unused sda3 is the problem.

---

### Post by srs5694 on 2011-01-21
You have no /dev/sda3 partition defined. The sfdisk output includes a line for it simply because it gives you information on all four of the fixed primary partition entries, whether or not they're in use. The start, size, and Id values for /dev/sda3 are all 0, however, indicating that the partition entry is not in use.

You should definitely *not* rename /dev/sda5 or subsequent partitions to be in the range of /dev/sda1 to /dev/sda4 -- at least, not unless you fully understand the MBR partitioning scheme and are doing this for a specific reason that you fully understand. If you've done this already, undo it while you've still got your original file; this change will cause nothing but grief. The reason is that, by definition, partitions 5 and up are logical partitions, which must reside inside an extended partition. If you rename a partition with a number of 5 or above to be in the range of 1 to 4, though, you're converting it into a primary partition. Unless you make appropriate changes to the extended partition, this will cause an illegal overlap between the renamed now-primary partition and the extended partition. Many tools will flake out when they see this sort of problem, which is confusing at best and highly dangerous at worst.

---

### Post by efflandt on 2011-01-21
You could use gparted on live/install CD or iso on USB to move the beginning of your extended partition down (which would probably automatically renumber it as sda3).  And then you could move the beginning of logical partition sda5 down to the beginning of sda3.

But you should familiarize yourself with restoring grub2 [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) because grub in the mbr is not going to know how to find the rest of itself if its files moved.  It is probably just a matter of following this [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Also note that moving the beginning of sda5 may take a long time (hours) and should not be interrupted, so do not do it when you need to shut your computer down or use it for something else.  An uninterruptible power supply (UPS) would also be a good idea if it is not a laptop with battery.

---

### Post by EarthBoundX5 on 2011-01-21
Thanks for the responses, and I'm sorry if I was not clear, so I'll respond as best I can...

> The  start, size, and Id values for /dev/sda3 are all 0, however, indicating  that the partition entry is not in use.

I specifically defined this for some reason in the "partition_table.txt"

> You should definitely *not* rename /dev/sda5 or subsequent  partitions to be in the range of /dev/sda1 to /dev/sda4 -- at least, not  unless you fully understand the MBR partitioning scheme and are doing  this for a specific reason that you fully understand. If you've done  this already, undo it while you've still got your original file

I already reversed doing this, I figured out it was a mistake pretty quick, haha.

> You could use gparted on live/install CD or iso on USB to move the  beginning of your extended partition down (which would probably  automatically renumber it as sda3).  And then you could move the  beginning of logical partition sda5 down to the beginning of sda3.

Already tried this, its actually the whole reason I made this thread.  I tried resizing it, but it would not let me at all; I just assumed it had to do with the fact that I predefined a 0ed sda3.

> Also note that moving the beginning of sda5 may take a long time (hours)  and should not be interrupted, so do not do it when you need to shut  your computer down or use it for something else.  An uninterruptible  power supply (UPS) would also be a good idea if it is not a laptop with  battery.

I've done ALOT of partitioning and resizing, I know how long it takes, haha.


ALSO, I figured I should attach my partition_table.txt, just to make things more clear, even though its basically already given above.

---

### Post by srs5694 on 2011-01-22
(re: resizing logical partition in GParted:)

> **EarthBoundX5 said:**
> Already tried this, its actually the whole reason I made this thread.  I tried resizing it, but it would not let me at all; I just assumed it had to do with the fact that I predefined a 0ed sda3.

You didn't say so in your first post. You'll need to be more specific about what sort of error message you're getting. There are a lot of possible causes for such problems, such as an in-use partition or a bug in libparted that causes it to refuse to resize partitions because of alignment issues. Without knowing what error message you're seeing, it's impossible to provide further advice, short of writing a book for you. You might also want to include a screen shot of your main GParted window; sometimes the icons in the main window provide useful clues.

---

### Post by EarthBoundX5 on 2011-01-23
> **srs5694 said:**
> (re: resizing logical partition in GParted
You didn't say so in your first post. You'll need to be more specific about what sort of error message you're getting.

I'm sorry, I thought I was clear enough with the last sentence in my post...

> The whole point of this is because I want to increase my extended partition to use my 18 GB of free space in front of it, and I think the existence of the unused sda3 is the problem.> **srs5694 said:**
> (re: resizing logical partition in GParted
You might also want to include a screen shot of your main GParted window; sometimes the icons in the main window provide useful clues.

Attached, but I only didn't before because I was pretty sure I was right about the issue, and figured it better to get to what I thought the point was, rather than waste time.

EDIT: Damn, didn't realize .htm files could not be uploaded.  Here is the details for gparted....

```

GParted 0.6.2
Libparted 2.3

**Move /dev/sda4 to the left and grow it from 14.00 GiB to 32.00 GiB**  00:00:01    ( ERROR )             
     calibrate /dev/sda4  00:00:01    ( SUCCESS )             [I]
         path: /dev/sda4
         start: 283224062
         end: 312580079
         size: 29356018 (14.00 GiB)[/I]          
    move partition to the left and grow it from 14.00 GiB to 32.00 GiB  00:00:00    ( ERROR )             [I]
         old start: 283224062
         old end: 312580079
         old size: 29356018 (14.00 GiB)[/I]          
    libparted messages    ( INFO )             *Unable to satisfy all constraints on the partition.*       [I]
         Can't have overlapping partitions.[/I]          

========================================
 
```

---

### Post by srs5694 on 2011-01-23
> **EarthBoundX5 said:**
> I'm sorry, I thought I was clear enough with the last sentence in my post...

You repeatedly referred to "the problem," but you never said what the actual problem was; you just stated (incorrectly) that "the unused sda3 is the problem." I'm not trying to be nit-picky here; I'm just trying to provide feedback so that you might better communicate technical problems in the future.

> Attached, but I only didn't before because I was pretty sure I was right about the issue, and figured it better to get to what I thought the point was, rather than waste time.

That's a common mistake. Always provide data, not conclusions, when posting problems to a technical forum like this.

> ```

GParted 0.6.2
Libparted 2.3

**Move /dev/sda4 to the left and grow it from 14.00 GiB to 32.00 GiB**  00:00:01    ( ERROR )             
     calibrate /dev/sda4  00:00:01    ( SUCCESS )             [I]
         path: /dev/sda4
         start: 283224062
         end: 312580079
         size: 29356018 (14.00 GiB)[/I]          
    move partition to the left and grow it from 14.00 GiB to 32.00 GiB  00:00:00    ( ERROR )             [I]
         old start: 283224062
         old end: 312580079
         old size: 29356018 (14.00 GiB)[/I]          
    libparted messages    ( INFO )             *Unable to satisfy all constraints on the partition.*       [I]
         Can't have overlapping partitions.[/I]          

========================================
 
```

The "unable to satisfy all constraints on the partition" message often occurs when resizing partitions in such a way that they come too close to one another. I haven't studied the issue in detail, but I hypothesize that libparted is modifying partition start and/or end points to satisfy alignment constraints (to align on cylinder of 1-MiB boundaries), and this causes the resized partition to overlap an existing partition. Rather than round the value the other way, it errors out like this. One possible solution is to change the alignment policy of the tool, which in the case of GParted can be done via a check box that's marked "rount to cylinders" or a selection box with three options (cylinder alignment, 1-MiB alignment, or no alignment), depending on the GParted version being used. Another option is to resize so that there's a small gap between the partitions.

---

### Post by EarthBoundX5 on 2011-01-25
> **srs5694 said:**
> you just stated (incorrectly) that "the unused sda3 is the problem."

Maybe the issue wasn't clear still.  That is A problem, but I agree it was not the problem relating to why I could not resize the partition.  It was just my assumption, and regardless I wanted to deal with that.  Its why I didn't title my thread "resize partition problem"; despite it being the main concern.  I still was hoping to find out how to fix the fact that sda3 is unused. 


> **srs5694 said:**
> The "unable to satisfy all constraints on the partition" message often occurs when resizing partitions in such a way that they come too close to one another. I haven't studied the issue in detail, but I hypothesize that libparted is modifying partition start and/or end points to satisfy alignment constraints (to align on cylinder of 1-MiB boundaries), and this causes the resized partition to overlap an existing partition. Rather than round the value the other way, it errors out like this. One possible solution is to change the alignment policy of the tool, which in the case of GParted can be done via a check box that's marked "rount to cylinders" or a selection box with three options (cylinder alignment, 1-MiB alignment, or no alignment), depending on the GParted version being used. Another option is to resize so that there's a small gap between the partitions.

This fixed the resizing issue.  The idea hadn't even crossed my mind, and such I feel kinda stupid. ](*,)

---

### Post by srs5694 on 2011-01-25
> **EarthBoundX5 said:**
> [quote=srs5694]you just stated (incorrectly) that "the unused sda3 is the problem."Maybe the issue wasn't clear still.  That is A problem, but I agree it was not the problem relating to why I could not resize the partition.[/QUOTE]

No, the unused /dev/sda3 is not a problem and never was a problem. Please review my earlier posts in this thread. If you're still confused, please tell me what's confusing you, or perhaps read [the Wikipedia article on MBR.](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by EarthBoundX5 on 2011-01-26
> **srs5694 said:**
> No, the unused /dev/sda3 is not a problem and never was a problem. Please review my earlier posts in this thread. If you're still confused, please tell me what's confusing you, or perhaps read [the Wikipedia article on MBR.]("http://en.wikipedia.org/wiki/Master_boot_record")

I'm sorry, the first time I read your first post, I didn't read it correctly, haha.  Anyways, I get it now why the sda3 is unused, more or less.  I didn't think once about the limit of 4 partitions relating to sda1-4.  Out of curiosity, what happens then when there is a extended partition with another primary after it?

Would it end up like this...
sda1
sda2
sda3
   --sda5
   --sda6
sda4

---

### Post by srs5694 on 2011-01-26
> **EarthBoundX5 said:**
> Out of curiosity, what happens then when there is a extended partition with another primary after it?

Would it end up like this...
sda1
sda2
sda3
   --sda5
   --sda6
sda4

Precisely. This is perfectly legal, although it's also a bit confusing to human brains. Also, some buggy partitioning programs can flake out with such configurations. (I once had OS X's Disk Utility delete /dev/sda4 when working on a disk like that.)

---

