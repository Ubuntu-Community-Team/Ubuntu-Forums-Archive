---
title: "Moving from virtual to physical machine with 11.04 = reboot loop. WHY?"
date: 2011-05-01
forum: General Help
---

### Post by Smokin Whale on 2011-05-01
Hey guys,

I've been a happy Ubuntu user for quite some time, and have to say this community rocks. I may not have many posts but i've been lurking for a while, and can always seem to find the solution.

Anyway, I am building a number of cheap PCs for friends and family and in the past with Ubuntu 10.04 and 10.10 I have simply set up a virtual machine in VMware workstation 7.1 and then used Acronis True Image home 2011 to transfer it to a physical machine. Works flawelessly, and takes about 10 minutes to get a complete OS onto a PC.

However, with the upgrade of 10.10 to 11.04, everything works fine in the virtual machine, but the moment I transfer it to the physical machine, the PC will enter a reboot loop the moment it tries to load Ubuntu. Holding shift doesn't help, but it does say "grub loading" for a split second before rebooting again. :(

I've tried a clean installation of Ubuntu 11.04 and it does the same thing.

Suggestions? Thanks in advance! :)

---

### Post by Smokin Whale on 2011-05-01
In hindsight this might be better in the installations and upgrades forum, could a mod please move this for me?

---

### Post by Smokin Whale on 2011-05-02
Okay well I think I may have found the problem. It lies with Acronis True Image Home 2011. I just tried clonezilla, and it boots up, no problem. Only problem that my virtual machine disk is 20gb, so my 40gb drive has a 20gb partition. I should be able to resize the partition using Gparted which is included in partition magic on the Ultimate Boot CD (google all of those if you're unfamiliar).

I've also updated Acronis and created a new bootable media, I'll keep this updated if it works. I imagine imaging sector-by-sector should work, its just a partition problem I think.

---

### Post by Smokin Whale on 2011-05-02
The newest version of Acronis warns me that I have to re-install Grub for it to boot, which explains why it wasn't working. Is there an easy way to do this or should I stick to Clonezilla + partition resize? I used Gparted and it worked a treat. Looking for the easiest way to do this really, I'll be doing quite a few.

PS: thanks for all the help guys. lol.

---

### Post by wilee-nilee on 2011-05-02
> **Smokin Whale said:**
> The newest version of Acronis warns me that I have to re-install Grub for it to boot, which explains why it wasn't working. Is there an easy way to do this or should I stick to Clonezilla + partition resize? I used Gparted and it worked a treat. Looking for the easiest way to do this really, I'll be doing quite a few.

PS: thanks for all the help guys. lol.

Clonezilla saves the mbr it is what I use, reinstalling grub2 is easy though.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Smokin Whale on 2011-07-20
Thought i'd update the thread for archival sake. I've been cloning ubuntu onto disks for some time now with great success.

It has something to do with the disk size being changed - using acronis to move to an identical sized disk yeilds no issues. However, even moving to a larger or smaller disk it will go into a reboot loop, but its easy to sort out - simply run the Boot Repair Gui tool from the Ubuntu Secured live CD. - repair Grub, and away you go.

Link to tool:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Otherwise, repairing Grub via the command line in a live CD works too.

Thanks for the help :D

---

