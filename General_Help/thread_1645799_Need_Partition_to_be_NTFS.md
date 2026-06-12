---
title: "Need Partition to be NTFS"
date: 2010-12-15
forum: General Help
---

### Post by Serson_Person on 2010-12-15
I love my Ubuntu NetBook 10.04 Remix.

However, I installed Ubuntu 10.10 on my Desktop Computer alongside Windows Vista.

Here's the problem:  Ubuntu notices the Windows partition, but Windows doesn't see the Ubuntu partition.  It's a 500GB Hard Drive split between the two.

Now I'm frantically trying to find out how to re-format my computer and re-install Vista by itself.  However, if I knew how to convert my Ubuntu partitions to NTFS then I wouldn't need to bother.

Ugh..  for once everything in my computer life was about to go smooth but I decided to install Ubuntu.  It's not Ubuntu's fault, it's my fault for doing something so unnecessary at the time.

any advice, possible solutions or anything, let me know.  Thanks.

---

### Post by afrodeity on 2010-12-15
Try installing EXT4 for Windows, there are utilities which make Windows able to see the ext partition.

---

### Post by Verbeck on 2010-12-15
try using Ext2fsd
[http://www.acc.umu.se/~bosse/]("http://www.acc.umu.se/%7Ebosse/")

but the better option would be to shrink your linux filesystem and create a shared separate ntfs partition to keep the files on

---

### Post by Serson_Person on 2010-12-15
Um, I've been searching about it and I'm a bit confused.

I forgot to mention I'm also a dummy at this kind of stuff.

---

### Post by sikander3786 on 2010-12-15
Please explain a bit. You just need to get rid of Ubuntu from your desktop? Or you also need to extract some data from Ubuntu partition?

If that is not the case, you can easily delete Ubuntu partition by going to My Computer > Manage > Disk Management. It would show your Ubuntu partition there and can be deleted/formatted.

But, if you've got Grub installed (most likely), you'll need to fix startup for Vista using a Vista installation/repair disc.

---

### Post by Serson_Person on 2010-12-15
In my perfect vision, I had Vista hogging everything of the 500GB except for Ubuntu owning the share it needs to run itself, plus maybe twenty-five GB for downloads and what not.

Yet when I was first installing Ubuntu, it looked like to split the partitions the way I wanted to, the whole hard drive would have to be erased.

So as it stands, Partition 1 (Vista) has about 310GB, while Partition 2 is split into two [Estimated from memory, it's like ... 149GB ; 7.9GB].

I'd like to have them both, because I love Ubuntu and Linux in general, it's just messed up right now because of the way the partitions are spliced and formatted.

So in panic mode, I just want to re-do everything and make it like i never installed ubuntu.
In patient mode, i'd like to still have both, but with vista either owning most of the drive space, or being able to see the linux partition.

I'm not very good at explaining things, or asking questions right.  I guess that's why searching google doesn't help me.  sorry

---

### Post by Verbeck on 2010-12-15
> **Serson_Person said:**
> 
So in panic mode, I just want to re-do everything and make it like i never installed ubuntu.
from ubuntu, backup your files in the home folder, delete the partition from windows partition manager, and then use a windows recovery disk to 
fix the boot loader. then, expand the cdrive or create a new partition from the unallocated space
> **Serson_Person said:**
> 
In patient mode, i'd like to still have both, but with vista either owning most of the drive space, 
boot into a live cd/usb, open system>administration>gparted, right click the ubuntu partition and resize (click the check mark to apply the changes). then from windows, expand the c drive (right click my computer>manage>disk management)
> **Serson_Person said:**
> or being able to see the linux partition. see my previous post or use the program ext2read

take your pick and ask any additional questions you may have

---

### Post by sikander3786 on 2010-12-15
You want to take back some of disk space from Ubuntu's partition and add it to your Vista partition?

---

### Post by Serson_Person on 2010-12-15
Thanks guys so far,

I never thought of running Gparted from USB linux.

Okay... so I'm in G-Parted, and here's what I'm trying to do...

I'm trying to trim the "fat" off of each partition.  [Not Fat format, just the extra space]...  but then I end up with two unallocated spaces, and I'm unsure what I can do from here.  I'd like to combine them and make an extra partition that I can put all neutral files in, like music, video and such but I can't seem to do that.

I'll do "Resize/Move", and then with the allocated space if I right-click only "New" and "Information" are available options.  I tried to create new NTFS in both of them and name them the same to see if they'd merge, but no luck.

Any suggestions?

---

### Post by Serson_Person on 2010-12-15
> **sikander3786 said:**
> You want to take back some of disk space from Ubuntu's partition and add it to your Vista partition?

I'd prefer to have three partitions, if that's possible.  a partition for neutral files, then just two partitions for the OS's.

---

### Post by sikander3786 on 2010-12-15
> **Serson_Person said:**
> I'd prefer to have three partitions, if that's possible.  a partition for neutral files, then just two partitions for the OS's.
You'll need a total of 4 partitions then because having a Swap partition is recommended even if you've got huge amount of RAM. So you need 2 partitions for your OS, 1 for Swap and 1 for data sharing. When you boot an Ubuntu Live CD, in order to let us know about your current setup, post the output of this command.

```
sudo fdisk -lu
```

---

