---
title: "Instalation &gt; Partitioning"
date: 2011-02-08
forum: General Help
---

### Post by nemacx on 2011-02-08
Hi everyone.

I'm in a middle of instalation of Ubuntu 10.10, so I have a couple of questions before i continue.

I have 3 partitions, all NTFS filesystems, I want to keep them, but change the filesystems on all 3 of them to Ext4.

So if i choose "Erase and use all" will I be able to partition later ? I'm thinking more about doing like this, but I'm not sure :

EDIT : First partition as my main, system partition, is this correct ?

[IMG]http://img109.imageshack.us/img109/9116/screenshot1gi.png[/IMG]

---

### Post by DanneStrat on 2011-02-08
Hi!

> I want to keep them, but change the filesystems on all 3 of them to Ext4.

You mean to keep the partition sizes and structure or the data

on the partitions? If you format the partitions all your data

will be gone.

> So if i choose "Erase and use all" will I be able to partition later ? 


Yes you will be able to partition afterwards. But at

the same time I would recommend you do a manual partitioning.

> I'm thinking more about doing like this, but I'm not sure :

EDIT : First partition as my main, system partition, is this correct ?

You can mount whatever partition you want as /. When you specify

/ as mountpoint, linux will use it as root partition.


If you have any more questions, feel free to ask.

---

### Post by nemacx on 2011-02-08
> **DanneStrat said:**
> Hi!



You mean to keep the partition sizes and structure or the data

on the partitions? If you format the partitions all your data

will be gone.



Yes you will be able to partition afterwards. But at

the same time I would recommend you do a manual partitioning.



You can mount whatever partition you want as /. When you specify

/ as mountpoint, linux will use it as root partition.


If you have any more questions, feel free to ask.

I know it'll all be gone, ok.

But i need to change the filesystems to Ext4, so the Erase all option falls out.

Well this is the problem, i've set up as on the picture, i want sda1 to be my root partition, but : 

[IMG]http://img225.imageshack.us/img225/5339/screenshotlzi.png[/IMG]

---

### Post by DanneStrat on 2011-02-08
>  know it'll all be gone, ok.

But i need to change the filesystems to Ext4, so the Erase all option falls out.

Well this is the problem, i've set up as on the picture, i want sda1 to be my root partition, but :

Did you tick the box to format "sda5" and "sda6" or was

it greyed out?

Mark those partitions one by one and select "change..." and see if you can tick the format box.

Then try to proceed with the installation.

---

### Post by nemacx on 2011-02-08
> **DanneStrat said:**
> Did you tick the box to format "sda5" and "sda6" or was

it greyed out?

Yep, i solved the problem by adding /media/D and /media/E to them.

Thank you for your help and patience 

EDIT : Yeah i ticked the format on all partitions, changed them to Ext4, to the first one i added "/" and to the second one and third i added as described above. :)

---

### Post by DanneStrat on 2011-02-08
> **nemacx said:**
> Yep, i solved the problem by adding /media/D and /media/E to them.

Thank you for your help and patience 

EDIT : Yeah i ticked the format on all partitions, changed them to Ext4, to the first one i added "/" and to the second one and third i added as described above. :)

Yes. It's important to select mountpoints or else

the operating system won't know what to use the partitions

for and they will be unused.

Good luck with ubuntu!;)

---

### Post by srs5694 on 2011-02-08
If you're erasing the partitions, it makes little sense to preserve the partition sizes from Windows, unless those sizes happen to correspond to useful sizes in Linux. My usual recommendation for Linux partitioning for new users is:


[list]
[*]**root (/)** -- 5-20 GiB, depending on how complete an installation you want and how much disk space you have available. Linux and all its programs reside here.
[*]**swap** -- 1-2 time your system's RAM; so if you have 2 GiB of RAM, you'd want 2-4 GiB of swap space. Swap space is used as an adjunct to RAM.
[*]**/home** -- Whatever's left over, unless it's very small, in which case keeping /home on the root (/) partition makes sense. All your user files (word processing documents, MP3s, etc.) reside in /home.
[/list]


There's little or no point in creating ext4fs /media/D and /media/E partitions for Linux; those aren't standard mount points in Linux, so creating them just complicates matters in a non-standard way. (You might use such partitions for exchanging data with a dual-booted OS, such as Windows, but you haven't mentioned such an OS; and you'd want to use FAT or NTFS for such an exchange partition.) Although your current /dev/sda1 is a good size for a Linux root (/) partition (roughly 20 GiB), your remaining partitions (both about 30 GiB) don't map well onto the swap and /home partitions I've described (unless perhaps you've got ridiculous amounts of RAM). Between these factors, it makes the most sense to me to delete those two partitions and create new ones of different sizes in their place.

---

