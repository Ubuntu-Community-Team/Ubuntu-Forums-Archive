---
title: "No partition available in LiveCD install.  Please help."
date: 2010-06-25
forum: General Help
---

### Post by daRPiniOn on 2010-06-25
I am attempting to install Ubuntu 10 from LiveCD and when it comes to the partition part there is nothing in the box.  I am running Windows 7 Pro with 2 partitions  (C and D), with more than 200GB free on each partition.

If this is a common issue and already another thread topic I couldn't find it.

Thanks for the help in advance.

---

### Post by leclerc65 on 2010-06-25
I would use [GPARTED]("http://gparted.sourceforge.net/download.php") to shrink D, to obtain an unallocated partition of about 15G to install Ubuntu on it.

---

### Post by dcstar on 2010-06-25
> **daRPiniOn said:**
> I am attempting to install Ubuntu 10 from LiveCD and when it comes to the partition part there is nothing in the box.  I am running Windows 7 Pro with 2 partitions  (C and D), with more than 200GB free on each partition.

If this is a common issue and already another thread topic I couldn't find it.

Thanks for the help in advance.

Is the Windows disk Dynamic or Basic?, I don't think the Linux partitioner can handle Dynamic.

---

### Post by daRPiniOn on 2010-06-25
> **leclerc65 said:**
> I would use [GPARTED]("http://gparted.sourceforge.net/download.php") to shrink D, to obtain an unallocated partition of about 15G to install Ubuntu on it.

But I already have a completely formatted unused partition.  The problem is that when I attempt to install Ubuntu it doesn't show any drives for me to select as an install path!  It doesn't show my C or D drive.  I used Easeus in Windows 7 to create/format a new partition simply for Ubuntu.  This may not be it, but it seems as if Ubuntu isn't recognizing any of my HDDs.

---

### Post by daRPiniOn on 2010-06-25
> **dcstar said:**
> Is the Windows disk Dynamic or Basic?, I don't think the Linux partitioner can handle Dynamic.

What do you mean by Windows disk?  - I'm using the .iso file I downloaded from Ubuntu's website and attemtping to install from DVD boot and I've attempted an install on Wubi.

---

### Post by daRPiniOn on 2010-06-25
Hey, sorry I need to pay  more attention to detail!  The drive that I created isn't unallocated - it's a designated NTFS - empty drive.  Unallocated and empty are two different things.  Thanks for your help!

---

### Post by daRPiniOn on 2010-06-25
> **daRPiniOn said:**
> Hey, sorry I need to pay  more attention to detail!  The drive that I created isn't unallocated - it's a designated NTFS - empty drive.  Unallocated and empty are two different things.  Thanks for your help!
Yep.  I still can't get it to work!  Not really sure why this thing isn't recognizing any of my HD partitions.

---

### Post by Dustin2128 on 2010-06-25
I think it would help if you partitioned your drive in windows; are your C & D partitions on the same drive or are they different drives? When I installed linux dual booting on my vista laptop, I had to use the vista partitioning tool to set aside about 85GB as free, unpartitioned space on the single 160GB hard drive. The ubuntu installer should automatically detect and install to the free space. I've only used 7 on public computers but I assume there's some partitioning tool there.

---

### Post by daRPiniOn on 2010-06-25
> **Dustin2128 said:**
> I think it would help if you partitioned your drive in windows; are your C & D partitions on the same drive or are they different drives? When I installed linux dual booting on my vista laptop, I had to use the vista partitioning tool to set aside about 85GB as free, unpartitioned space on the single 160GB hard drive. The ubuntu installer should automatically detect and install to the free space. I've only used 7 on public computers but I assume there's some partitioning tool there.

I am using one 1TB SATA 6GB/s HDD with two partitions.  The D partition is completely free (nothing on it whatsoever and formatted to NTFS).  The C drive has more than 200GB free space.  I'm getting an error when I run Wubi - after you install in Windows 7 you are required to reboot.  When I select Ubuntu on the dual boot menu in DOS it will show a startup screen (purple with ubuntu logo and five dots) and then immediately after this I'm getting a lengthy error message that says the .iso couldn't be found, that it might be from a system crash, or several other things...  Any avenue I take to try to install this thing is laden with errors.  I'm working off a brand new custom built PC -- specs:
Windows 7 Professional x64
Gigabyte X58A-UD3R Mobo
Intel i7 930 @ 2.8GHz (stock speed)
12GB DDR3 Triple Channel RAM @ 1333 MHz
1TB Caviar Black SATA 3.0 HDD
PNY GTX 480 GPU

Also -- I used Easeus Partition Manager (Incredibly good partitioning software)  Do you suspect that could be the problem?  I truly don't think it has anything to do with that.  It's not recognizing any of my partitions so?  I don't know what to say

---

### Post by Mark Phelps on 2010-06-25
Ubuntu can NOT install to an NTFS formatted partition.  So, as long as the partition is that format, the installer will not see it.

If you want Ubuntu to have its own partition, you have to UNFORMAT it, and as the previous poster said, install Ubuntu to FREE SPACE.

In contrast, a Wubi install REQUIRES an NTFS partition, but that is installing Ubuntu as an application inside Windows -- and is something I do not recommend.

---

### Post by daRPiniOn on 2010-06-25
> **Mark Phelps said:**
> Ubuntu can NOT install to an NTFS formatted partition.  So, as long as the partition is that format, the installer will not see it.

If you want Ubuntu to have its own partition, you have to UNFORMAT it, and as the previous poster said, install Ubuntu to FREE SPACE.

In contrast, a Wubi install REQUIRES an NTFS partition, but that is installing Ubuntu as an application inside Windows -- and is something I do not recommend.

Thanks for the clarity of the post.  I'm a Linux noob so I appreciate the comprehensive reply.  Thanks a lot Mark.

---

