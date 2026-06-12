---
title: "Trouble triple booting Ubuntu, XP, and 7"
date: 2009-12-29
forum: General Help
---

### Post by blueshiftoverwatch on 2009-12-29
I'm trying to triple boot Ubuntu 9.10, Windows XP, and Windows 7. I installed 7 first, then XP, then Ubuntu last because Windows has the nasty habit of deleting GRUB and making it's self boot up by default.

When GRUB first comes up after turning on the computer all I see is Ubuntu and an option called "Windows 7 loader sda1", which for some reason actually boots Windows XP. As well as the Ubuntu standard safe mode and other stuff not worth mentioning.

Also, I installed the GRUB update from the Update Manager and am running a fake RAID0 system. It's configured from the motherboard so everything sees the array as just 1 HD, so I don't think that has anything to do with it.

I was going to try to figure it out myself but I'm too paranoid to mess around with GRUB because doing so could possibly result in bad things happening. I'm sure theirs a simple solution. Since a picture is worth a thousand words I'm going to post a picture of my GParted partition setup rather than describe it. In case your wondering, /virmac and /locmed are abbrebiations according to a naming scheme I have. They're only for storing random data.

---

### Post by oldfred on 2009-12-29
Windows combines its boot loaders into one, so you can boot but then cannot boot from either one separately except see below:

Vista/Win7 copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing]("http://members.iinet.net/%7Eherman546/p15.html#BOOTMGR_is_missing")
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

You also have the separate 100mb win7 partition since you installed it first. It is actually the boot partition for windows.

---

### Post by blueshiftoverwatch on 2009-12-30
Thanks for the links. The first one I'm going to bookmarks as it seems like useful information that might come in handy later on.

According to [this guy's post]("http://ubuntuforums.org/showpost.php?p=8357272&postcount=18") he got it to work. There are two minor things I'm not 100% clear on.

1. When he says "make 3 primary partitions" he means make 2 NTFS partitions, one for Windows XP and one for Windows 7, I get that. But than he said to make a third partition for "storage". What does he mean by that? Is the 3rd partition the 100MB Windows boot partition? Or is that the primary partition that I put Ubuntu on?

2. I could make the NTFS partitions from the Ubuntu live CD. But doesn't Windows 7 use a slightly different/updated form of the NTFS file system? If yes, wouldn't installing Windows 7 on the older/standard version that the Ubuntu live CD makes cause problems?

---

### Post by blueridgedog on 2009-12-30
The XP install overwrote the Windows7 boot loader.  I suspect it would work if you installed XP, then 7 then Ubuntu, but the path of placing each OS on primary partition and setting the boot flag should work as well.

---

### Post by oldfred on 2009-12-30
If you install win7 first as a clean install it puts in the 100mb boot partition. If the partition already exists then it just installs in that partition.

Storage is just the term he used for a shared data drive. When you dual boot win & ubuntu it is better to have another NTFS partition for data. It does not have to be primary. Originally we were mostly windows but to allow the same firefox and thunderbird info I put the profiles on a shared NTFS partition. Then most of the things we did we could do in either system with exactly the same data.

---

### Post by blueshiftoverwatch on 2009-12-30
But as long as I do the thing where I install one Windows OS, then put in the Ubuntu live CD to take the boot flag off of that partition before installing the second Windows OS, and than finally Ubuntu at the end. I'll be able to boot all 3 OS's and launch them from Grub, correct?

I'm not really interested in having a data partition to keep shared application info. Even if I was, couldn't I just keep all of the data on my Linux/Ext4 partition, install an application on Windows to give it the ability to read/write to Ext4, and keep my Firefox bookmarks and other settings synced across OS's that way?

---

### Post by oldfred on 2009-12-31
Windows cannot read ext4 and some say there are still issues with the windows drivers for ext3. You can read windows NTFS partitions but if you do too much inside windows boot partition it may complain. Even windows only users recommend a separate data partition so when :)windows goes bad they can still get to their data.

The moving of the boot flag keeps windows from seeing the other windows install and combining them. Of course from windows you will only be able to boot one of them but now grub can directly boot both.

---

### Post by blueridgedog on 2009-12-31
> **blueshiftoverwatch said:**
> But as long as I do the thing where I install one Windows OS, then put in the Ubuntu live CD to take the boot flag off of that partition before installing the second Windows OS, and than finally Ubuntu at the end. I'll be able to boot all 3 OS's and launch them from Grub, correct?


I think so, ie it matches my understanding of boot loader installation, but I have never tried it.  Give it a shot and let us know.

---

### Post by blueshiftoverwatch on 2009-12-31
I just:
1. Installed Windows XP
2. Removed the boot flag
3. Installed Windows 7

I'm on the manual partition phase of the Ubuntu 9.10 setup right now. But before I go any further I have one question that can be split into two parts. They're not so much important questions as I already know what to do as it is me being curious and trying to learn something. The guy in [this post]("http://ubuntuforums.org/showpost.php?p=8357272&postcount=18") said that after setting up Windows XP and 7 as primary partitions he put Ubuntu and everything else on an extended partition.

I noticed that if I go to make Ubuntu a primary partition the rest of the HD space becomes labeled "unusable", why? I also thought that HD's were able to support up to 4 primary partitions. Also, why would I want to put Ubuntu to be on an extended instead of a primary partition?

What would happen if I made my swap and two data partitions as logical partitions first and since  adding another primary partition makes the rest of the space unusable, tried to get around it by making Ubuntu's / partition primary, and last?

---

### Post by oldfred on 2009-12-31
You can have 4 primary or 3 primary and 1 extended that holds all the logical partitions. If you want the use the entire drive the 4 partitions in any combination must cover the entire drive. Some have trapped an extended between primary partitions and then could not expand the extended without major moving of partitions:
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)

---

### Post by blueshiftoverwatch on 2009-12-31
I got everything working from the links you posted originally. I'll check out those other links later.

---

