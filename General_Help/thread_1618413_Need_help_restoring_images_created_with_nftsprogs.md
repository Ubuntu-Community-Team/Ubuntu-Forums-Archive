---
title: "Need help restoring images created with nftsprogs"
date: 2010-11-10
forum: General Help
---

### Post by mahershi on 2010-11-10
Hello!


Prelude:
A few weeks back I got myself a little netbook. It came with Windoze-XP and other stuff loaded in to three partitions:
Partition - 1: The recovery partition that came installed at the factory
Partition - 2: The Windows XP partition that got installed after I started the netbook for the first time. This was the "work/play" partition.
Partition - 3: I was forced to create this at the time "Partition - 2" was created.

In all reality, I bought this netbook hoping to give it to mom someday soon, but, then, .... greed took over so I started contemplating installing Ubuntu on this netbook  and use it as a sort of really portable notepad. 

Giving into the temptation of keeping the netbook for myself I decided to:
-> forget gifting it to mom (I am going to buy her another netbook or the iPad)
-> wipe out all the partitions and install just plain ubuntu 10.10 on it (all of my other systems run some mods of 10.04)

Realizing that there was no way for me to recover the installed drivers, etc, I decided to use NTFS-progs to clone the hard-drive just in case I ever needed to restore Windoze. So, roughly, here are the steps I performed:

* I boot the netbook from an external HDD that had Ubuntu 10.04 installed on it.
* I made a copy of the MBR using the following command:
# dd if=/dev/sda of=./mbr count=1 bs=512
* I captured the original partition table in two ways:
# fdisk -l /dev/sda > fdisk-l
# sfdisk -d /dev/sda > partition-table
* The following command was used to make a copy of the Recovery Partition (Partition - 1, as mentioned above):
# dd if=/dev/sda1 of=./dev-sda1-recovery-partition conv=sync,noerror bs=64K
* NTFS-Clone was used to make a copy of the main windows XP partition (Partition - 2, as mentioned above). The following command was run:
# ntfsclone --save-image --output ./dev-sda2-windows-xp-partition /dev/sda2

The output of that command was as follows:
  ntfsclone v2.0.0 (libntfs 10:0:0)
  NTFS volume version: 3.1
  Cluster size       : 4096 bytes
  Current volume size: 73155395584 bytes (73156 MB)
  Current device size: 73155398656 bytes (73156 MB)
  Scanning volume ...
  100.00 percent completed
  Accounting clusters ...
  Space in use       : 12982 MB (17.7%)   
  Saving NTFS to image ...
  100.00 percent completed
  Syncing ...

----

So far so good! Just to make sure, I understood how to restore that cloned partition, I decided to try out the steps in reverse.

I deleted all the three partitions from the HDD. Then I created a single NTFS partition spanning the entire HDD. Then I used "ntfsclone --restore-image ..." to restore the  Windows-XP partition image (partition - 2, as stated above) onto the entire HDD. Then, I used "ntfsresize -s 160039M /dev/sda1" to resize the restored partition. Realizing that the earlier Windows XP partition was partition # 2 and now it was partition # 1, I made the appropriate changes in the Windows boot.ini file. Then, I restarted the system ... and nothing happened! The BIOS went through fine (obviously!) and then, there was a blank screen with blinking cursor!!!! :(

Hunting through the forums I found thread 610680 and performed the magic incantations as specified in it (though I have no clue what those incantations do):
# echo 1 | awk '{printf("%c%c%c%c",$1%256,$1/256,$1/65536,$1/16777216)}' | dd bs=1 count=4 seek=28 of=/dev/sda1
(NOTE that the "echo 1" was done with the presumption that I needed to put partition # 1 into some table on the disk.)

After all that goofing around, I was unable to get Windows-XP to boot on that system. And therefore I ask: how do I "restore" ONLY the Windows-XP partition (partition - 2, as stated above) using NTFS-progs so that the restored partition occupies the ENTIRE DISK?

Thanks in advance for all your help.

---

### Post by dcstar on 2010-11-10
> **mahershi said:**
> 
..........
After all that goofing around, I was unable to get Windows-XP to boot on that system. And therefore I ask: how do I "restore" ONLY the Windows-XP partition (partition - 2, as stated above) using NTFS-progs so that the restored partition occupies the ENTIRE DISK?

Thanks in advance for all your help.

You don't. The boot loader is preset to use the recovery partition before going to the windows partition.

If you only want windows, then download whatever windows tools available that fix bootloaders for windows systems.

---

