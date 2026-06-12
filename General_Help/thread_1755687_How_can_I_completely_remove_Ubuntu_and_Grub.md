---
title: "How can I completely remove Ubuntu and Grub?"
date: 2011-05-11
forum: General Help
---

### Post by aisajib on 2011-05-11
Hi all! I need a quick but important help. Imagine I installed Ubuntu in a separate partition along with a Windows operating system. Now, for some reason I want to completely uninstall Ubuntu. The best way, as I find myself, is to format the partition that contains Linux. But what do I do if I want to remove the grub bootloader as well?

This happened a couple of times when I installed Ubuntu on my friend's computer. If for whatever reason they want to remove Ubuntu, they can't get rid of Grub.

So, I'd like to know what is the best way to completely remove Ubuntu from a separate partition as well as Grub and recover Master Boot Record for windows?

---

### Post by coffeecat on 2011-05-11
As far as the mbr is concerned, there are two ways:

With a Windows installation disc, from the repair console or command line. With Windows XP, run 'fixmbr'. With Vista or Windows 7, run 'bootrec /FixMbr'.

If you don't have a Windows installation disc, you can use an Ubuntu live CD. See this post for three alternatives:

[http://ubuntuforums.org/showpost.php?p=8950739&postcount=7](http://ubuntuforums.org/showpost.php?p=8950739&postcount=7)

Most people find the first method with lilo to be quite reliable. That all assumes you have a working Windows partition with the boot flag set.

My way of going about this would be to repair the Windows mbr with any of the above methods and then boot into a live Ubuntu CD to remove the Ubuntu partition(s) and create whatever partitions for Windows in the freed space as are needed.

---

### Post by Quackers on 2011-05-11
You will need to restore the Windows bootloader to the mbr of the drive with a Windows repair disc/installation disc.

---

### Post by seawolf167 on 2011-05-11
Windows 7 Recovery Disks can be found [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/"). After running the previously posted commands, simply boot up into Windows and use the Windows partition editor to delete the Ubuntu partition and then resize that now unallocated space into your existing Windows partition.

---

### Post by aisajib on 2011-05-11
> **coffeecat said:**
> As far as the mbr is concerned, there are two ways:

With a Windows installation disc, from the repair console or command line. With Windows XP, run 'fixmbr'. With Vista or Windows 7, run 'bootrec /FixMbr'.

If you don't have a Windows installation disc, you can use an Ubuntu live CD. See this post for three alternatives:

[http://ubuntuforums.org/showpost.php?p=8950739&postcount=7](http://ubuntuforums.org/showpost.php?p=8950739&postcount=7)

Most people find the first method with lilo to be quite reliable. That all assumes you have a working Windows partition with the boot flag set.

My way of going about this would be to repair the Windows mbr with any of the above methods and then boot into a live Ubuntu CD to remove the Ubuntu partition(s) and create whatever partitions for Windows in the freed space as are needed.


Thanks for your reply. Which one do you personally think is better? The bootrec /FixMbr or the code:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
??

---

### Post by oldfred on 2011-05-11
They both work. 

It may depend more if you have a windows repair disk or a Linux repair disk.

Both windows & Lilo in the MBR just look for a partition with the boot flag and jump to that partition for more boot code.

Generally you should have a repair/live Cd/USB with the current version for every system you have installed whether Window, Ubuntu or anything else.

---

### Post by aisajib on 2011-05-11
> **oldfred said:**
> They both work. 

It may depend more if you have a windows repair disk or a Linux repair disk.

Both windows & Lilo in the MBR just look for a partition with the boot flag and jump to that partition for more boot code.

Generally you should have a repair/live Cd/USB with the current version for every system you have installed whether Window, Ubuntu or anything else.


Thanks for the help. :)

---

