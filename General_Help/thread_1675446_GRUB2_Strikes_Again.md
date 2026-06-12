---
title: "GRUB2 Strikes Again"
date: 2011-01-25
forum: General Help
---

### Post by aajax on 2011-01-25
This posting is a follow-on to some past experiences that are discussed in a couple of other posts that can found at [http://ubuntuforums.org/showthread.php?t=1574076]("http://ubuntuforums.org/showthread.php?t=1574076") and at [http://ubuntuforums.org/showthread.php?t=1576624]("http://ubuntuforums.org/showthread.php?t=1576624").

GRUB2 violates a cardinal rule of system design.  In my opinion the updating of a system should not result in changes being made to other systems.  While it is possibly that my recent experience is not entirely attributable to the poor design of GRUB2 I think it is entirely attributable to the theory of the design.

The experience to which I refer can be summarized as the somewhat innocent act of allowing maintenance updates to be applied to the packages installed on my system that ended up not only breaking the system to which they were applied but in fact damaged other systems on the same computer.  In this case the damage being referred to is to render 2 different systems unbootable that both worked great prior to the maintenance update.

The scenario plays out like this.  I have a computer with multiple operating systems installed.  Two of them reside on the boot device and are based on Ubuntu Server 10.04 (Lucid).  They are installed in such a manner that each system is ENTIRELY contained within their respective partitions.  In that, GRUB2 is confined to the respective boot sector of each partition.  These boot sectors are booted using what GRUB refers to as chain-loading.  In this case, there is a small (30MB) primary partition that is marked active.  It is FAT16 and happens to have DOS5 installed but of course the presence of a DOS system is irrelevant to GRUB.  GRUB would work just as well with no OS installed on that partition.  Then my 2 Ubuntu Server systems reside on partition 1 and 3 (sda2 & sda4 from a Linux perspective).  When I updated the system on sda4, GRUB was updated and the update process seems to have updated the boot sector on sda2 and not sda4.  The consequence of this is that chain-load to sda4 hangs just after the Starting message that begins the loading process.  This is the behavior that would be expected if the boot sector on sda4 was not updated.  While the update of the boot sector on sda2 caused the system on sda2 to become unbootable it did permit the system on sda4 to be booted.  Of course the only reason I know this is because of past suspicions developed from prior experience with bad outcomes caused by the use of GRUB2.  A user lacking this experience would easily be led to believe that booting the boot sector of sda2 must mean that the system on sda2 is the one that is running.  In this case the 2 systems are similar enough that there are no obvious signs of what is different.

The evidence used to make the above assertions is as follows:

- The menu that is presented when I boot (chain-load) sda2 is the one defined in the grub.cfg file on sda4.
- The menu defined by grub.cfg on sda2 doesn't appear anywhere.
- The modification dates for the files in /boot/grub on the sda4 partition reveal the recent update. Note the update occurred quite a bit prior to discovery of the boot problem because I try to keep this computer running constantly.  Reboot only occurs when the power fails.

My opinion is that this scenario represents a cardinal sin being committed as a result of poor design.  Installing maintenance on one system should never result in changes being made to another system.

I suspect that there is nothing that will be done about this problem but thought that the community of users should know about the kind of problems they can expect as a result of dependence on a very ungrand boot loader.

---

