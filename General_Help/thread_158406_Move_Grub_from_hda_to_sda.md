---
title: "Move Grub from hda to sda?"
date: 2006-04-11
forum: General Help
---

### Post by mozetti on 2006-04-11
Here's my setup:

Primary Master = hda
Primary Slave does not exist
Secondary Master = DVDRW
Secondary Slave = CDRW
Tertiary Master = sda
Tertiary Slave does not exist

First Boot Device is the Tertiary Master, sda, my 200GB SATA HDD

hda - PATA 100GB
1st Partition - 1GB WinNTFS SWAP (bootable)
2nd Partition - 1GB Linux SWAP
... I have 2 more partitions, but it's irrelevant

sda - SATA 200GB
1st Partition - 6GB WinNTFS XP OS (bootable)
2nd Partition - 14GB WinNTFS XP Programs
3rd Partition - 6GB /root
4th Partition - 15GB /home
... I have 3 more partitions, but it's irrelevant
---------------------------------------------
When I installed, I told it to put GRUB in the MBR since it picked up my XP installation. But every time I booted, I kept seeing the Windows boot.ini, even though I installed GRUB to the MBR. Well, I figured out why, I think. GRUB installs to to the Primary Master, hda, correct? So, apparently GRUB installed to the MBR of hda instead of the MBR of sda (the hard drive I installed Ubuntu on). The only problem is, in my BIOS, I don't boot from hda, I boot from sda.

My Tertiary Master, sda, is my first boot device and it had, and apparently still has, the windows boot.ini on it. The problem is, if I switch boot devices in the BIOS, making hda the first boot device, then Windows will rename my partitions, giving them different drive letters - I really don't want to go through this chore, since I install all my Windows programs to a different partition than the XP OS. Trust me, it'll be a mess.

Also, I'd rather not switch boot devices in the BIOS to dual-boot. I'd like to use GRUB to handle it. I can boot XP & Ubuntu now, but it's a major kludge that I lucked into. I won't get into details, but basically I have an entry in the Windows boot.ini for XP & one incorrectly set up for Ubuntu. When I choose Ubuntu, it gives an error because it's not pointing to the right place, and says press any key to continue. When I press a key, it goes to GRUB and I can choose my Linux kernels or my WinXP. I can also choose the XP item in GRUB and it works.

So, basically GRUB is installed and working properly on the MBR of hda. I just need it to be installed and working properly on sda. How do I copy the GRUB that is in the MBR of hda to the MBR of SDA?

---

### Post by WakkiTabakki on 2006-04-11
Try this:
[http://ubuntuforums.org/showthread.php?p=815810#post815810]("http://ubuntuforums.org/showthread.php?p=815810#post815810")

Good luck
/N

---

