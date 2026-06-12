---
title: "HOWTO: Partition a flash drive for LiveUSB and Windows accessable storage"
date: 2009-07-29
forum: General Help
---

### Post by joshedmonds on 2009-07-29
Most methods of creating a single partition liveUSB have two shortcomings:

1. The spare space on the drive is not available for storage from within the live environment (without persistence workarounds).

2. The / of the live environment is exposed in Windows, making it more likely files will be deleted or changed, and harder to find your everyday files.

Attempting to use multiple partitions will only work if the first partition recognised by Windows is the storage partition (other partitions are not recognised or ignored)

To get around these issues, partition using GParted (System->Administration->Partition Editor) in the following order:

1. Delete existing partitions
2. Create fat32 (etc. Windows readable) partition using all but 800mb
2. Create fat32 partition (it won't really matter for a non-persistent /) using the remaining space

The first partition will now be recognised by Windows as the storage space.

To install the liveUSB environment, run Unetbootin AS ROOT (required to install bootloader into flash mbr) and select the second partition as the install destination.

Voila, safe from accidental damage liveUSB, Windows & Linux friendly storage space.

Based on many attempts on my 8Gb flash drive, happy to hear of other approaches that achieve the same ends.

---

### Post by joshedmonds on 2009-07-30
This was posted to tips and tutorials, but the mods have put it in general help where it can be promptly buried and of no help to anyone. Can it be moved back please?

Thanks

---

### Post by alienkid10 on 2009-12-29
Thank you! I am tying this on my 4GB flash drive now.

---

### Post by alienkid10 on 2009-12-29
I tried it with the first partiton being 3.01GB and the next filling the rest something like 750MB. I used Unetbootin to install 9.10 on the 750MB partition everything checked out. Looked in Gparted and it's bootable. But when going my PC's boot menu I go to Harddisk and it only shows my internal HDD. There is a USB-ZIP entry but it doesn't appear to do anything. I have the PHOENIX Award BIOS v6 on a Emachines W3650. Any help? For now I am going to reformat to 1 partition unbootable.

---

### Post by efflandt on 2009-12-29
Some computers default to hard drive even if you change boot order in CMOS setup (BIOS).  You may also have to hit a specific key during your computer's splash screen to boot something else.  That is probably for safety, so you do not boot from CD, etc. unless you specifically intend to.

It is like that on an older Dell work laptop and a new Dell I just bought for someone else.  I did a regular installation of 64-bit Ubuntu 9.10 on a USB drive.  Even if USB is before hard drive in boot order, it will not boot USB unless I press F12 and select USB (other computers may use F10 or Esc).  If hard drive is before USB in boot order, it boots Win7 on main hard drive, regardless of pressing F12 and selecting USB.

The only virus I ever caught was a boot sector virus, Stoned Empire Monk (Monkey) spread by floppy disks before the internet as we know it.  It was on a refurbished computer and its Win3.1 boot floppy.  It spread by infecting any floppy inserted in the computer and infected the mbr of anyone who started their computer without removing an infected floppy.  It moved and XOR'd the partition table, which interfered which repartitioning or reformatting.  A CD or DVD could do the same thing, which is why many computers ask you to press a key if you really want to boot CD/DVD.

PS: Older computers might not boot directly from USB, and check any other BIOS settings related to USB.  There may be another USB setting about legacy or auto that can affect it.

---

### Post by alienkid10 on 2009-12-29
I didn't change any BIOS settings. I just hit F10 and before when I didn't partition the drive it showed in harddrive as Sandisk 4GB USB and USB-ZIP wasn't there before. Now after the partition then it doesn't show in Harddrive and a USB-ZIP entire is there that just takes me to my POST screen then continues booting as normal.

I am using WUBI to boot Ubuntu.

---

### Post by C.S.Cameron on 2009-12-29
Just for the record, on a single partition Bootable flash drive as created by unetbootin or usb--creator, data written to the flash drive by Windows can be read from the folder cdrom when booted into Ubuntu and vice versa.

---

### Post by alienkid10 on 2009-12-30
Cameron: I know that. But I would rather like one cordoned off. What if I just did like above but instead of bootable USB have the second partition casper-rw? What should my GRUB menu.lst on my boot CD need in it to be persistent?

---

### Post by C.S.Cameron on 2009-12-30
Here is a reprint from a previous post:
This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext3 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, removed CD, rebooted.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Changed desktop background, connected to wireless and installed FontForge.
Rebooted, changes were persistent.

---

### Post by alienkid10 on 2009-12-30
where is he installing Unetbootin? Any idea why my flash drive wouldn't boot via the USB-ZIP entire? Or why after partitioning it wouldn't appear in Harddrive? So I could make casper-rw and then add that line to a menu.lst on a boot DISC plug in drive and boot CD with persistent and it would save to flash drive? What's the difference between casper-rw and home-rw?

---

### Post by C.S.Cameron on 2009-12-31
In this case unetbootin was installed on a windows machine and the flash drive was created in windows, proceedure is same when running unetbootin from Ubuntu.
How old is the computer? I have an old one that mentions USB-ZIP in BIOS but it won't boot a flash drive. try the drive on a different computer. The flash drive should appear in Harddrives on a modern computer.
I'm not sure what you are saying about menu list, I don't think there is one in a 'persistent' install, however a flash drive with a casper-rw partition on it should be able to store the changes when booting a Live CD, you just have to boot the CD as persistent. Home-rw partition stores the stuff that would be stored in home on a full install, casper-rw stores all the other changes.

---

### Post by alienkid10 on 2009-12-31
ah. Fairly new bought in 09. Runs XP Emachines W3650. Menu.lst as in the GRUB menu list file.

---

