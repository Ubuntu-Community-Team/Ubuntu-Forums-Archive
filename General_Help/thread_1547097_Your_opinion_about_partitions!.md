---
title: "Your opinion about partitions!"
date: 2010-08-06
forum: General Help
---

### Post by saidbakr on 2010-08-06
Hi,
My computer's hard drive is 160 GB, I partitioned it for Ubuntu 10.04 in the following order and size:
++++++++++
/boot 50 MB
/         40 GB
/home 115,5 GB
/swap 4.5 GB
+++++++++++

What do you think about this partitions? Does it suitable to serve best performance and usability?

---

### Post by snowpine on 2010-08-06
I think 50mb is too small for /boot; it will fill up after a couple of kernel upgrades (unless you are super-vigilant about cleaning out old kernels).

I would shrink / a bit and increase /boot to 500mb or thereabouts. 40gb is not necessary for / unless you plan to install a lot of large applications (the base install is about 4gb).

---

### Post by saidbakr on 2010-08-06
I think that in the documentaton, I don't remembered where, it is enough for /boot to be 25 ~ 50 MB.

---

### Post by snowpine on 2010-08-06
> **saidbakr said:**
> I think that in the documentaton, I don't remembered where, it is enough for /boot to be 25 ~ 50 MB.

OK, good luck! :)

---

### Post by rhigmus on 2010-08-06
> **saidbakr said:**
> I think that in the documentaton, I don't remembered where, it is enough for /boot to be 25 ~ 50 MB.

[QUOTE=snowpine;9686916]OK, good luck! :)
[/QUOTE]

what he said. minimum specs are fine for one or two kernels, but you don't want the headache of trying to figure out why none of your kernel upgrades ever work. Happened to me on my desktop pc with 9.1 and a 70MB /boot partition. Don't be stingy, give it a Gig and you wont have to think about it afterward ;).

---

### Post by WorMzy on 2010-08-06
Why do you need a boot partition? You only have one OS. o.O

Other than that, looks fine. Depending on how much RAM you have, you could trim down your Swap. (Unless you intend to do lots of video/high-res image editing)

Oh, and the best way to use a boot partition is to just keep grub on it. You keep kernels on the OS' root partition, in /boot, and mount the boot partition's grub folder into /boot/grub so you can run update grub. (Or if you're using grub legacy, just manually edit menu.lst).

---

### Post by saidbakr on 2010-08-06
The discussion is very useful, but I'd like to ask about the meaning of two kernels? Does it means that my computers run, for example, Ubuntu 10.04 and WindowsXP or Suze Linux. i.e dual or multiple boot?!

Another question, does the order of partitions has any rule? I know that /boot should be found at the beginning of the hard drive sectors. However, do you think keeping /swap at the end of the hard drive is better or not?

---

### Post by snowpine on 2010-08-06
> **saidbakr said:**
> The discussion is very useful, but I'd like to ask about the meaning of two kernels? Does it means that my computers run, for example, Ubuntu 10.04 and WindowsXP or Suze Linux. i.e dual or multiple boot?!

Another question, does the order of partitions has any rule? I know that /boot should be found at the beginning of the hard drive sectors. However, do you think keeping /swap at the end of the hard drive is better or not?

I will answer your question in a moment :) but first let me ask you a question: Why not let Ubuntu partition the drive for you? The installer will automatically choose the correct partitioning scheme for 99% of users. You haven't really made a strong case for needing a custom partitioning scheme.

The Linux kernel is the most important part of Ubuntu that controls your hardware. Assuming you update your system periodically, you will get new versions of the kernel with bug fixes and security patches. 

[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

---

### Post by gsgleason on 2010-08-06
My /boot has three kernels and is 59M currently.  This is 10.04 i686.  100M is good.

What are the advantages of the segregation?

A separate /boot is nice if you're using a file system for the rest that is not supported by your boot loader.  Also, if you are compiling streamlined kernels for that machine, it's nice to keep a separate /boot that will survive reloads.

A separate /home is nice because you can reload the core and have users' directories in tact.  Just pay attention when reloading the rest of the disk.

Maybe a /boot partition at the beginning of the disk helps boot time?

---

### Post by Ginsu543 on 2010-08-06
Unless you're doing something arcane, for home desktop use I recommend three partitions:

1) / (20 GB)
2) /home (137 GB)
3) swap (3 GB)

As mentioned above, there really is no reason to have a separate /boot partition unless you'll be installing many different OSes, and even then it would be better to have a separate GRUB2 partition and keep each kernel in its respective OS partition's /boot directory.

If you intend to install a lot of programs, you might want to consider expanding the / partition to 30 or 40 GB. For me personally, I've always found 25 GB to be plenty for the / partition

---

### Post by saidbakr on 2010-08-06
> **snowpine said:**
> I will answer your question in a moment :) but first let me ask you a question: Why not let Ubuntu partition the drive for you? ...
[]("http://en.wikipedia.org/wiki/Linux_kernel")

I think that our friend **gsgleason **answered your question. However, I would like to know something about this point. Suppose that I ,currently, run Ubuntu 10.04 on my computer and my user name is "bakr" so we have /home/bakr, and after sometime I'd like to install fresh installation of Ubuntu 10.04, 10.10  or even Fedora and then in this installtion I choosed my user name to be "admin". i.e there is no "bakr" user!

My question is: What's the situation for documents presented in /home/bakr with the new installation? Could I able to move or edit them with the "admin" user or I should need to get them by SUDO?!

---

### Post by Nick_Jinn on 2010-08-06
Just forget about /boot. It will go automatically into root.

Its nice having a seperate /data partition though. I use NTFS, or Fat32 if you work with other linux operating systems without NTFS support.

---

### Post by worksofcraft on 2010-08-06
Need for separate boot partition has something to do with it having to reside on disk sectors that can be addressed by the BIOS on older machines that just weren't designed for modern disk drives. However whenever I had nothing but problems making separate boot partition.

I read somewhere that it is best to have swap partition 3x the size of your computer physical memory. That way virtual memory system can work optimally.

Don't skimp too much on your / partition: Besides programs you may want to store large shared files there (video and audio) and also apache and mysql store their data off /var I think and many apps use /tmp e.g. internet cache.

---

### Post by bodhi.zazen on 2010-08-06
Unless you have a good reason, why not go with the defaults ?

There are many reasons to make various partitions, why are you doing so ? With antyhing resembling a modern computer you are not going to see much, if any, performance boost.

In terms of swap, IMO, I advise you use swap = RAM X2 , max 1 Gb, unless you use suspend, in which case swap = RAM. If you have more then 1 Gb RAM you are unlikely to use swap at all.

In terms of /boot , you need to have a separate /boot partition with LVM and/or LUKS (full system encryption).

If you are booting multiple OS you want a grub partition, not a boot partition. If you share /boot across OS, each install will format and overwrite /boot , so you would loose the kernel(s) for the old OS. You then mount your grub partition at /boot/grub.

---

### Post by ezsit on 2010-08-06
I always use a separate /boot partition out of habit from the days of old bios limitations and now use them for keeping the boot files in ext3 while able to experiment with other filesystems. It has never caused any problems whatsoever for me.

I like:

swap   ==  2GB
/boot  ==  1GB
/      ==  40GB
/home  ==  remainder of the drive

I do not run Windows at home and so I have no need for a shared data partition, but if you want one, leave enough space then create and format that partition from within Windows.

---

### Post by Nick_Jinn on 2010-08-07
I use massive amounts of swap when I use live disks. If I want to convert a DVD image from one type to another, I need more than 3x the size of the file.......the original file, the file in its middle state during conversion process, the output file. These all exist at once. If the file is 3gb, I need at least 9gb if I am going to first convert the image and then burn it with my second optical drive. I could use a /data partition for some of it, but for some reason a lot of these files end up as 'shared documents' and still eat up your ram even if you save them to a data partition.....at least that is what it seems like to me. I use rather huge swap partitions and use it kind of like a temporary data folder for live CD/DVD sessions.

I have 4TBs of space to work with though. On a small hdd I would use no less than 1gb of swap and up to 2x your ram.

---

### Post by bodhi.zazen on 2010-08-07
IMO a data partition makes a lot of sense, I like to keep my data separate from the OS, makes reinstalling the OS and backups much easier. 

Nick_Jinn's example of needing a large swap file is valid, but that is not a typical scenario. converting uses /tmp and on a live CD , /tmp is ram and thus one needs a large swap. On an installation this would not be the case. You would still use hard drive space in /tmp but not a large swap file.

---

