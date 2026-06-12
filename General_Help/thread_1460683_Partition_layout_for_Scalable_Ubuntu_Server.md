---
title: "Partition layout for Scalable Ubuntu Server"
date: 2010-04-23
forum: General Help
---

### Post by KaiserBachfeld on 2010-04-23
I am new to Lenix (as an administrator I have only been a very light user mostly with live CDs) and as a home network administrator.  I have searched the forums and tried many things but nothing seems to be successful so I will write here what I am looking for.  I keep getting stuck at partition disk page.  I have tried many things but nothing seems to work.


**I need to know what the best partition layout is for Ubuntu Server 9.1 with RAID software.  Also, I need to know which drives should be logical or primary and what file system is the best to use and if I should should change the mount behavior, reserved blocks, flag the partition to be bootable, etc.  Thanks for your help.**


Below is for further information of what I like to use my server as.

Goals for my server:

- Scalable.  As one trying to teach himself network and server administration I would like to add and remove things to try out new things.  This I will probably do with virtual machines and if I like the new application and what it can add to my network I will then add it to the main operating system.
- File Server with security (encrypted hard drives just encase the   machine is stolen).  This is my primary purpose and if I could get  everything to run backups to server I would be very satisfied.
- Security (Firewall, possibly a proxy for my network, I would like to   see all of my traffic pass through the server before it leaves for the   world. I have also recently starting to learn about tor and setting up a   tor rely so this is a possibility too.  It would be important to have   my traffic be more anonymous and if my IP address could be something   from an English speaking country even better so my downloads come in   something that I can read).
- Virtual machines (I would like to have a place to setup virtual   desktops/servers where I can teach myself more).

Current Hardware:
- 8 GB RAM/4-sticks dual channel/800 Mhz
- Core 2 Quad 2.83 GHz/12 MB cache
- Two 1TB 7200 RPM/64 MB/SATA II
- shared monitor with desktop via KVM switch

Current Network components:
- Modem (WiMax)
- wireless router
- 5-port switch
- Access Point
- Desktop Vista 64-bit Ultimate
- Netbook Windows XP Home (would like to change to ubuntu remix or GoS)
- Laptop Windows 7 Home Premium (my roommates computer)

I would like to add in the future:
- possibly an iPad or some kind of book reader that would have access to   the wi-fi
- Some kind of laptop probably with Windows 7 so I can take the work I   do in Adobe CS4 on my desktop with me with when I travel.

---

### Post by KaiserBachfeld on 2010-04-29
Is there a limit how many partitions Ubuntu 9.1 server can I have?

No matter the order or the size for some reason after I make four partitions the rest of the drive is inaccessible.

For example I am trying to make something like the following partitions.

/10% or 10 GB ext4
/boot 250MB or 5 GB
/home 20 GB ext4
/usr 20 GB
/swap 12 GB

I have two 1 TB drives.  I would like RAID 1 these drives and use the extra space for network storage to point automatic updates to but I can't seem to get past what the best partitioning layout should be.

---

### Post by srs5694 on 2010-04-29
For maximum flexibility, consider a [Logical Volume Management (LVM)](http://tldp.org/HOWTO/LVM-HOWTO/) configuration. (See also [this site,](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem) or [this one,](http://www.ubuntux.org/a-beginners-guide-to-lvm) or Google to find more.) LVM enables you to easily add, delete, and resize filesystems without worrying about which ones come where on the disk, or moving them so as to consolidate free space that might exist between different partitions. This will enable you to easily add new distributions, increase the space devote to each one, etc. LVM does add complexity, though, and IIRC the standard Ubuntu desktop installer doesn't directly support LVM, so you'll need to use the server installer to set up your system.

As to partitions, LVM can exist either "raw" on the disk or in one or more partitions. (See the LVM documentation for details.) You can have only four primary or extended partitions on a standard Master Boot Record (MBR) configuration. One extended partition, however, can hold an arbitrary number of logical partitions, so the usual configuration has one to three primary partitions and as many logical partitions as you need. Alternatively, you can use the GUID Partition Table (GPT) format rather than MBR. GPT has a number of advantages, one of which is that it does away with the awkward and annoying primary/extended/logical distinction. Overall, I recommend use of GPT on Linux-only installations; however, Windows can't boot from GPT on a BIOS-based computer, so if you intend to dual-boot with Windows, you're better off sticking with MBR. (This doesn't affect network clients; a Windows client can access a Linux server that boots from GPT just fine.)

In your case, you'll probably have at least three partitions total on each disk: One for swap space, one for /boot, and one for RAID. (If you use MBR logical partitions, you'll also have an extended partition, which holds all your logical partitions.) You'll use separate (non-RAID) swap space on both disks for best speed. You'll then create an LVM configuration in the RAID partition. Your two /boot partitions can be copies of each other for one OS, or you can devote each to a separate Linux installation. If you add more /boot partitions (say, two per disk), you'll be able to install more Linux distributions.

---

### Post by KaiserBachfeld on 2010-05-28
Sorry for just now getting back to you [srs5694]("http://ubuntuforums.org/member.php?u=1032238").  It have been traveling.  Thank you so much for the information.  That is very helpful.  I like the idea of going with the GPT. I will only have one OS installation on this machine and it will be Ubuntu so I don't have to worry about MBR or even having multiple /boot partitions for multiple distros.

I am still waiting for some additional parts for my machine but I look forward to being able to put everything together soon.

---

