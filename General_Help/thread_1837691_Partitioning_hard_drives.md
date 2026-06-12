---
title: "Partitioning hard drives"
date: 2011-09-02
forum: General Help
---

### Post by losgood on 2011-09-02
Hi all, new member here. I'm going to be doing a new build in a week or two, and I'd really like to give Ubuntu a go as a dual boot with Windows 7 64 bit. I'll be installing two hard drives, a 1TB to hold the Windows swap files and for data storage/ backup, and a 500 gig for the installation of Windows and Ubuntu. I've been trying to read about installing dual operating systems on a new install, but I'm a bit confused. I'm new to trying a dual boot system and I want to make sure I understand the process of partitioning the hard drives correctly. What is the best/easiest way to accomplish this? The way I understand it, I need to create a partition for Windows, one for Ubuntu, and another that is two times my RAM capacity for an Ubuntu swap file. Is this correct? Is it better to let Windows create the partitions or use the Ubuntu disc? Any info would be appreciated. Thanks!

---

### Post by raja.genupula on 2011-09-02
first install your windows by creating a partition only for it from your windows cd . 
then install your ubuntu by creating a partition for it and a swap partition . the swap partition ratio you've chosen is right . double of your RAM . 

for dual booting  this is the simple way .

all the best ,

---

### Post by jfed on 2011-09-02
As far as one drive goes, what I usually do when installing Ubuntu for my friends is just have Windows 7 installed first, using the entire disk, then toss in an Ubuntu disk, and during the install there is an option to "install Ubuntu side by side" with your other operating system, and it's literally just point-click and drag a small graph to allocate space, does the rest for you.

Although in your particular situation you seem to be doing a bit more of a complex job, you could install the OS's like that on one disk at least, haha.

If worst comes to worst you can always just wipe and start over no? lol

---

### Post by LowSky on 2011-09-02
Hi welcome to the forums.

First install Windows. If you are using Windows 7 or Vista you will need two partitions, as part of it's standard install. The first is a small boot partition and the other isyou normal C: drive partition. You can set all this up during the install very easily. Follow the instructions the installer gives you.

After you get Windows up and running install Ubuntu. use the option to use the free space and Ubuntu will do things on its own. Don't really worry about the SWAP thing it will handle everything on its own.

That the best advice I can give a new user. No need to get into a debate over how much SWAP or separate partitions for certain parts of the file system. Just do the standard install and things should be fine.

One thing I will say is Ubuntu doens't need as much space as Windows so don't give it half the hard drive unless you really expect to use it all.

Ubuntu can run fine using less than 20GB, but any more than 100GB is crazy unless you have HD video being stored.

---

### Post by oldfred on 2011-09-02
With two hard drives you can keep systems totally separate, one installed on each drive. This avoids issues of who controls the MBR and if you install some agreesive Windows virus checker that thinks grub is a virus or DRM software that writes into the same area as grub2's  core,img that is just after the MBR.

I also prefer to keep systems separate from data. You install a smaller Windows system and use more space for data. Many windows users suggest a separate d: partition, so when you have to reinstall windows you do not have to reinstall all your data. Backups still required.
You do not want to write into the Windows system partition from Ubuntu, you need a shared NTFS partition.

With Ubuntu you only need 10-20GB (I use 25 since I have space) for / (root) and have my data elsewhere. I also keep space for several 20 to 25GB roots so I can install the next version without interfering with my current version or test other installs.

Smaller system partitions are slightly more efficient as the files most often used are nearer each other.

If you have Ubuntu on a totally separate drive you can use gpt in place of MBR(msdos) partitioning. Somewhat improved and more reliable. Windows will only install to gpt if you are booting with UEFI (new boot system) not BIOS.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

