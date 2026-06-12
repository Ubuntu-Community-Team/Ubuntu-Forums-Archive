---
title: "Dual boot (win 7 + Ubuntu)"
date: 2011-01-05
forum: General Help
---

### Post by asana on 2011-01-05
Hi fellow Ubuntu-users,

I searched google about this topic but couldn't find a recent topic (win7 + ubuntu).

Currently my set-up is as follow:

**HDD 1 (SATA) with 3 partitions:**
- Windows 
- Files
- Games

**External HDD:**
- Ubuntu
- Swap

I want to boot from Ubuntu but I can't select the Operating System. I know it has to do something with the MBR, but I don't have that much knowledge about Dual booting from two different HDDs.

I tried to create a parition next to mine partitions on HDD 1, but with 4 partitions it changes into a Dynamic Drive which doesn't support multiboot (I have to install Ubuntu and everything will be erased).

I hope someone can help me with this problem and can come with a good tutorial about this problem.

THanks in advance,

Tristan

---

### Post by gekken on 2011-01-05
> **asana said:**
> Hi fellow Ubuntu-users,

I searched google about this topic but couldn't find a recent topic (win7 + ubuntu).

Currently my set-up is as follow:

**HDD 1 (SATA) with 3 partitions:**
- Windows 
- Files
- Games

**External HDD:**
- Ubuntu
- Swap

I want to boot from Ubuntu but I can't select the Operating System. I know it has to do something with the MBR, but I don't have that much knowledge about Dual booting from two different HDDs.

I tried to create a parition next to mine partitions on HDD 1, but with 4 partitions it changes into a Dynamic Drive which doesn't support multiboot (I have to install Ubuntu and everything will be erased).

I hope someone can help me with this problem and can come with a good tutorial about this problem.

THanks in advance,

Tristan

Hi Tristan - Without rooting around in your machine, it appears that when you did the install, GRUB2 was installed on the external HDD. Really common issue.

It can be fixed! read this: [http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html) GREAT tutorial for beginners!

---

### Post by garvinrick4 on 2011-01-05
# If Ubuntu is on an external USB drive you have to select it to boot in front of internal drive in BIOS. Usually it is F10 or F2 or esc key. Once you boot into Ubuntu. Open a terminal and you can add Windows internal drive to your boot menu by:
```
sudo update-grub
```
# When you boot internal drive first you will always boot straight into Windows
# When you boot external USB drive you will now always get option of Ubuntu or Windows.

---

### Post by oldfred on 2011-01-05
I hope you did not accept the windows dynamic partitions. Once changed to SFS you cannot change back and it will not work with any thing else.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Some info on partitioning and partitioning tools:
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by asana on 2011-01-06
Thanks for your answers!

I actually reinstalled Ubuntu using the whole partition.
However, something was wrong with my password (I think i made a typo), again a reinstall.

This time my MBR is corrupt, after the BIOS-screen I get: Grub>.
I found this solution and I'm going to try this one ASAP: [Link]("http://ubuntuforums.org/showthread.php?t=1509922")

Greetings.

---

### Post by oldfred on 2011-01-06
More links on repairs:

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by asana on 2011-01-06
Thanks for your reply.

How I restored my MBR so I could get into Windows:
- boot LiveCD
- Open a Terminal Window
- sudo apt-get ms-sys
- sudo fdisk -l
- sudo ms-sys -m /dev/sda

After that Windows booted.

I found a 120 gigabyte harddisk which I'm going to build-in in my computer. What is the best way to install Ubuntu on it without messing up my MBR.

---

### Post by oldfred on 2011-01-06
Some suggest and it is the safest way, is to unplug the windows drive. Ubuntu will think it is the first drive but still works as it also searches to find the partition by unique UUID. Just be sure to keep windows as the first drive as it does not like changes.

The other alternative is to manually partition and then it gives you a combo box on where to install grub. It is not always sdb, but usually. Some systems promote IDE drives or seem to change boot order so drive letter is not always the same. 

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

---

### Post by murtyvonna on 2011-01-06
I have upgraded Ubuntu 10.04 to 10.10 through update manager. At start up grub lists kernels which are shown as Un-installed as per Synaptic package manager, but  they are previous kernels left over after upgrading. I want want to clean them. What is the way.

Thanks in advance.

---

### Post by garvinrick4 on 2011-01-07
# murtyvonna you can start a new thread:
```
sudo update-grub
```will get rid of kernels already uninstalled 
that show in grub menuentry.
# open up synaptics and in upper right type in offending kernel
2.6.37-11 for example use the one you want to get rid of.
right click on generic kernel that comes up and mark for removel then hit
the apply check mark and remove.
Can see your kernels by running this code:
```
 
grep menuentry /boot/grub/grub.cfg

```

---

