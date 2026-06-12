---
title: "Partitioning causes &quot;mkfs.ext3: invalid blocks count&quot; error."
date: 2009-12-18
forum: General Help
---

### Post by SchneiderIS on 2009-12-18
First off, thanks for any help that ca be provided here.

Note that I am working from the command line since I am preparing the partitions prior to the installation in order to ensure that the Apple file system required for the first three partitions remains intact.

I have a AppleTV that I am trying to install MythBuntu (Ubuntu 9.10 OS) onto a separate partition.  The process is taking a 40Gb drive and breaking it into 6 separate partitions where the first three are already created.  The remaining three are created from the original 4th partition.  I am using "parted" as per the instructions from the atv-bootloader site (the site seems to have gone quite due to problems with spammers) where they talk about partitioning the dries but use a different sizing than what I am wanting to use.  Namely I am building the Media partition which will be sda4 and then sda5 will become the Ubunt installed partition with sda6 for swap.  

From the instruction set that is given it appears that a 4096 byte block count is requested for the Linux partition.  In the following commands that I execute I keep getting the error of "mkfs.ext3: invalid blocks count".

[FONT="Courier New"]# parted -s /dev/sda rm 4
# parted -s /dev/sda rm 5
# parted -s /dev/sda rm 6
# parted -s /dev/sda mkpart primary HFS 2732016s 68595695s
# parted -s /dev/sda mkpart primary ext3 68595696s 76984304s
# parted -s /dev/sda mkpart primary linux-swap 76984305s 78140126s
# partprobe /dev/sda
# mkfs.hfsplus -J -v Media /dev/sda4
Initialized /dev/sda4 as a 31 GB HFS Plus volume with a 8192k journal
# mkfs.ext3 B -b 4096 -L Linux /dev/sda5
[COLOR="Red"]mke2fs 1.40.8 (13-Mar-2008)
mkfs.ext3: invalid blocks count - /dev/sda5[/COLOR][/FONT]

So this makes me ask two questions.

1.) Does Ubuntu require a block size of 4096?

2.) If it does not what is the block size that it requires?

3.) Regardless, what is the solution that does get a proper block count using "parted" from the command line?

---

### Post by SchneiderIS on 2009-12-19
Is there no one that can help with this problem?

---

### Post by dcstar on 2009-12-19
> **SchneiderIS said:**
> 
........
# mkfs.ext3 **B** -b 4096 -L Linux /dev/sda5
[COLOR="Red"]mke2fs 1.40.8 (13-Mar-2008)
mkfs.ext3: invalid blocks count - /dev/sda5[/COLOR]
........

What is this "B" option?

---

### Post by SchneiderIS on 2009-12-19
You nailed it right on the head.

How very strange and thank you.  The "B" is not in my script that is created to generate the partitioning so when I cut and paste it into telnet I expected everything to be as in the script.  How very strange.

It works now.

Lesson learned for me is that mkfs error reporting is not complete or is very vague and misleading.

Thanks dcstar!

---

