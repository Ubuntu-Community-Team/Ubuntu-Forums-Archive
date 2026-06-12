---
title: "Increase Partition size"
date: 2010-05-03
forum: General Help
---

### Post by akssps011 on 2010-05-03
Hi

I m using a dual boot system (kubuntu + WinXP) on an 80GB HDD.
I gave 10 GB space to Kubuntu and rest to Win XP.

I am now left with only 1 GB space. How can I increase the size without affecting the data stored on my Kubuntu drive. (I have around 15GB free space in XP Partition)

---

### Post by srs5694 on 2010-05-03
You have three choices (you can do two or all three, of course):


[list]
[*]Shrink your Windows partition and increase the size of the Linux partition to fill that space. You can use GParted to do this, although using the Windows partitioner to shrink Windows is safer.
[*]Buy new bigger-than-80GB hard disk, using Clonezilla or some other tool to copy both Windows and Linux to the new disk (increasing partition sizes as you see fit), and replace the existing drive with the new one.
[*]Buy a new disk of any size, partition it, and use the extra space for Windows and/or Linux. For Linux purposes, I recommend using the new space as /home. Google "Linux moving /home" for guides on how to do this; quite a few exist. If you're running out of space because you're installing lots of software, you could move the entire Linux installation or move just /usr to the new disk instead of or in addition to moving /home there.
[/list]


Post again if you need more specific advice.

---

### Post by agnes on 2010-05-03
Boot from a live cd that has GParted. There are many such Live CD's but Puppy Linux will do (maybe also (K)Ubuntu but don't recall if (K)Ubuntu has GParted by default).
So, launch GParted from Live CD
Right click XP partition -> Resize/Move and shrink it
Right click Kubuntu partition -> Resize/Move and expand it
Could take a long time. But should work ok. I did it in opposite direction when making room for XP.

---

### Post by akssps011 on 2010-05-03
> **agnes said:**
> Boot from a live cd that has GParted. There are many such Live CD's but Puppy Linux will do (maybe also (K)Ubuntu but don't recall if (K)Ubuntu has GParted by default).
So, launch GParted from Live CD
Right click XP partition -> Resize/Move and shrink it
Right click Kubuntu partition -> Resize/Move and expand it
Could take a long time. But should work ok. I did it in opposite direction when making room for XP.

would using Gparted live cd directly from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) would do ?
Would resizing this way leave my data intact. I don't want to loose data.

---

### Post by hangfire on 2010-05-03
> **akssps011 said:**
> Hi

I m using a dual boot system (kubuntu + WinXP) on an 80GB HDD.
I gave 10 GB space to Kubuntu and rest to Win XP.

I am now left with only 1 GB space. How can I increase the size without affecting the data stored on my Kubuntu drive. (I have around 15GB free space in XP Partition)

You have other options that are easier and safer than resizing existing partitions.

For example, you could add another hard disk, create a /home and a /var on it, and move those directory's contents to the new disk. Your 10GB partition should be sufficient to run Kubuntu if well maintained.

Another option is to delete your swap partition (assuming you have one) and create a /home or /var partition in its place. If you find you do need more swap, you can create a smaller swap file in the / (root), /home, or /var filesystem.

---

### Post by Monotoko on 2010-05-03
> would using Gparted live cd directly from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) would do ?
Would resizing this way leave my data intact. I don't want to loose data. 

I have never had a problem resizing partitions, and in 99.9% of cases it will be fine if your sensible (accidently deleting partitions is usually a bad plan of action)

But theres always the 0.01% chance that it could currupt the partition, so make sure you have a backup if its really important data :)

---

