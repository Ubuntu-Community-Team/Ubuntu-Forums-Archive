---
title: "Attempting to clean install XP - HDD not recognised"
date: 2011-10-01
forum: General Help
---

### Post by sammya on 2011-10-01
Hey guys. I created a bootable usb of Windows XP Pro SP3 and plan to do a clean install of it then dual boot ubuntu 11.04 but before I can even start I have run into a problem..

The USB boots fine but when I get to the stage where I have to choose a HDD to install it on/create partition my laptops HDD isn't recognised.. only the thumb drive that is being used to install XP.

I thought it may be because the HDD was formatted and didn't have an actual format (unallocated) so I started up GPARTED on the Ubuntu Live-USB and created a ntsf partition. Booted XP again from the usb and same problem..it just isn't showing.

Any ideas? Should the drive be formatted as unallocated in gparted? Should it have a partition?

Thanks guys

*edit*

Forgot to mention. I used the shred command after I backed up everything I needed from the HDD and I am thinking I most likely deleted the driver used to help make it recognizable.. so what is the procedure I have to go through to install the new driver and where to get it?

Cheers

---

### Post by oldfred on 2011-10-01
Is the NTFS partition a primary partition sda1 thru sda4 and did you in gparted put a boot flag on the partition? Windows only installs (and repairs and boots from) an active primary NTFS partition. Active in Windows is boot flag in Linux.

Grub2 does not use boot flag, but some BIOS will not let you boot at all without a boot flag on a primary partition.

---

### Post by prodigy_ on 2011-10-01
This has nothing to do with partitions. Any OS installer will happily remove/overwrite any partitions if you'll tell it to do so.

Most probably the drivers for your HDD controller just weren't on the XP installation CD. This is a very common problem. You need textmode drivers for your HDD controller (should be available on the vendor website) and a tool like [nLite](http://www.nliteos.com/).

---

