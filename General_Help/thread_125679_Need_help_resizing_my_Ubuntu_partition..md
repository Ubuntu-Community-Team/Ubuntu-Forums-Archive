---
title: "Need help resizing my Ubuntu partition."
date: 2006-02-04
forum: General Help
---

### Post by brjoon1021 on 2006-02-04
I have a 160 GB hard disk.

there is a 40 GB windows XP partition, NTFS at the front of the drive. The rest WAS unformatted so that I could install Ubuntu. 

I just installed Ubuntu and formatted a 41 GB Linux partition as a Primary partition where I installed Ubuntu. GRUB went into the MBR. I selected Reiser FS but Partition Magic (My windows Partition Manager) shows it as ext 2 for some reason...

Anyway, I now have a Primary parition with Windows,a second Primary partition that has Ubuntu and  about 70 GB or so left over as unformatted.
The problem is: I want more Linux distributions to try out. 

So, can I resize the Ubuntu, primary partition safely ? Or, Partition Magic may allow me to convert it to Logical. Is that safe ? Remember , my goal is to have several, 7 or more, Linux distros on this disk. I just do. The limit is 4 Primary partitions per disk. So I need to start making Logical partitions. Given what is already done, how can I backtrack, make Ubuntu take less space and get more partitions made, safely ? It was kind of a waste to make such a large primary partition for Ubuntu. I want to try out several Linux and give them 5-8 GB each. I pretty much want to put as many partitions as this disk will hold because I want to install Kanotix, PCLinuxOS, Mandriva, Linspire, Xandros, Vector, Suse, and probably more.

Can you help me with the primary problem: getting Ubuntu to take up a lot less real estate. I want it on a 5-8 GB partion instead of the 40 or so that it resides on now.

Thanks,

B.

---

### Post by dcstar on 2006-02-04
[QUOTE=brjoon1021]
.......
Can you help me with the primary problem: getting Ubuntu to take up a lot less real estate. I want it on a 5-8 GB partion instead of the 40 or so that it resides on now.
[/QUOTE]
Probably the best bet would be to boot up off the Install/Live CD, and resize the (unmounted) partition with the appropriate tool available on the CD.

Of course you would back up any important data first in case things went wrong.....

---

### Post by Major_Stitch on 2006-08-22
It isn't a problem.
When in Ubuntu install the gparted package and than it will be easy just choose the partition you want (in gparted) and than resize.

---

### Post by !nvincible on 2007-02-27
You can do it easily :) 
just issue follw command ...
1.**parted**
2.**p**
in my case it is ...
Number  Start   End     Size    Type      File system  Flags
1       32kB    5240MB  5239MB  primary   ntfs         boot
2       5240MB  40GB    35GB    extended               lba
5       5240MB  10GB    5239MB  logical   fat32
6       10GB    16GB    5239MB  logical   fat32
7       16GB    17GB    1053MB  logical   linux-swap
8       17GB    27GB    10GB    logical   fat32
9       27GB    39GB    12GB    logical   ext3
10      39GB    40GB    1020MB  logical   ext3


[COLOR="Blue"]this will display a partion table to you .
then just select a partition you want to decrease...[/COLOR]
3.**resize 9  27GB 33GB**

This command will resize your partion ...

I hope this helps...

---

### Post by shellhrs on 2007-02-28
I've had good experience using GParted LiveCD. I found it much better than using Partition Magic or Acronis Disk Manager in Windows.

When I tried to use GParted directly from Ubuntu (when running Ubuntu), it can't resize the partition I wanted (the Ubuntu root partition) because it's active, unlike PM in Windows. That's where GParted LiveCD came. It booted from the CD, and therefore the HD is not active -- you can modify the HD.

But I don't know if you can move a primary partition to a logical partition using GParted LiveCD. AFAIK, you need to create one large logical partition in which you can create multiple partitions (for your Linux distros) later. Maybe PM can, but I haven't tried it myself.

---

