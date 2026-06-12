---
title: "Installing to raid1"
date: 2006-01-20
forum: General Help
---

### Post by glave on 2006-01-20
Two days and I'm a bit baffled by what my install keeps doing... Nothing seems consistant between each try. First off, to clarify, I have been referencing these howtos/tutorials:

[https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)
[http://www.howtoforge.com/linux_software_raid](http://www.howtoforge.com/linux_software_raid)
[http://www.planamente.ch/emidio/pages/linux_howto_root_lvm_raid.php#Creating%20RAID%20devices](http://www.planamente.ch/emidio/pages/linux_howto_root_lvm_raid.php#Creating%20RAID%20devices)


My first success was with lilo, using lvm over raid1. This seemed to work fine, until I installed another sata controller and 3 drives on it. Then when I powered up, LILO had 99 99 99 99, etc all over the place. So I reinstall... This time I did not use lvm, and I opted for grub (I'd rather have grub anyday!). This worked out ok (eventually) but I had lots of trouble with the partitioner still trying to force some of my partitions back into lvm. Once the system got booted up, I tried to test a failure buy unplugging the first drive in the array. I tried to shutdown and reboot but it got numerous errors and never did shutdown. Upon rebooting, LILO kicked in from the 2nd drive (huh??) and attempted to boot, but didn't get fully loaded. I'm assuming this was a leftover from the first installation, but I'm not sure how.

After plugging the primary drive back up, the system would no longer boot at all. Tired and frustrated, I opted for the fakeraid instead. I got all the way to installing grub, and when I began to copy the stage files, the grub dir didn't exist. I tried creating it, and I got an I/O error. ARRRRGGGG!!!!

Has anyone had any success installing breezy onto raid 1? I'm trying to install it onto two 80g drives (sata) attached to the motherboard, while having 3 other sata drives on a controller card that are in raid5 lvm. Ideally I'm after

/boot        50mb
swap        3gb
/             10gb
/usr/local  67gb (remainder of space)

I don't supposed lvm matters on that portion, but I'm looking to make the 3drive raid5 array expandable without being destructive when I do so.  Does ANYONE have any pointers? I'm losing sanity trying to get this installed stabily!!

---

### Post by lha on 2006-01-20
One successful Ubuntu installation on software raid1 here!

I used pata drives and no lvm, just good ol' plain partitions. I don't have a separate /boot as this causes some issues with grub files being in /boot/boot/grub instead of /boot/grub but if you are able to handle this and need /boot partition, I guess you can do it that way, 

Before starting installation, I made partitions with cfdisk. I prefer cfdisk mostly because it produces clean partition tables and has a nice and simple interface. It can show partition sizes in cylinders, so it is easier to see if two partitions are exactly the same size. You can use whatever partition tool (including installers partitioner) to make your partitions, Just make sure that your drives' partition tables are identical.

During installation, I chose to manually edit partition tables and selected create md devices. Then I selected mount points for these new md devices like they were usual partitions and finished the install.

The reason you had lilo on the second hd is grub is installed only to one disk. If you want to have it on both disks, [here are some instructions]("http://alioth.debian.org/download.php/668/rootraiddoc.97.html").

---

### Post by glave on 2006-01-20
Did you do any additional partitioning or did you install your whole system with just one partition?

I'm so hopeful of getting this nailed down once I get home from work!

---

### Post by lha on 2006-01-20
[QUOTE=glave]Did you do any additional partitioning or did you install your whole system with just one partition?

I'm so hopeful of getting this nailed down once I get home from work![/QUOTE]

I have root, /var, /home and one partition for misc data.

---

### Post by Ocxic on 2006-01-20
[QUOTE=glave] Once the system got booted up, I tried to test a failure buy unplugging the first drive in the array.[/QUOTE]

You just unplugged it! i hope the computer wasn't turn on at the time, that is a really good way to fry a controller

---

### Post by glave on 2006-01-20
Yup, I unplugged it. These are all sata drives, amd a little known fact about sata is that it is plug and play, they can work sorta like a usb drive.

---

### Post by glave on 2006-01-20
[QUOTE=lha]
During installation, I chose to manually edit partition tables and selected create md devices. Then I selected mount points for these new md devices like they were usual partitions and finished the install.

The reason you had lilo on the second hd is grub is installed only to one disk. If you want to have it on both disks, [here are some instructions]("http://alioth.debian.org/download.php/668/rootraiddoc.97.html").[/QUOTE]

When the installation finished, did it ask you to use grub or did it assume lilo? Also when it came to grub, I'm assuming that I only need to follow

7. Put grub into the MBR of the second disk

after completing a normal install and things should be peachy?

---

### Post by lha on 2006-01-21
[QUOTE=glave]When the installation finished, did it ask you to use grub or did it assume lilo? Also when it came to grub, I'm assuming that I only need to follow

7. Put grub into the MBR of the second disk

after completing a normal install and things should be peachy?[/QUOTE]

My installer asked if it was okay to install grub to mbr. Didn't offer me lilo.

As far as I can remember, that's the only part (7. Put grub...) you are interested in. Everything else was configured automatically. Sorry for posting a link to such a page that had so much unneeded and maybe distracting info. I wanted to give [this link]("http://deb.riseup.net/storage/software-raid/"), but I could not find it at that time.

---

### Post by kosmic on 2006-01-21
Do not put Grub in a LVM partition, Grub can't boot from a LVM

---

### Post by glave on 2006-01-21
No worries! All is well now. I booted from a live cd, cfdisk'd my partitions on both drives, rebooted from an install cd and everything went peachy.

I followed the instructions from step 7 of that one page, and voila! I went to test things out and it went perfect. Thanks for all the help.

Last question though, I've read about grub being on raid and not wanting to recognize new kernel updates on both grub installations. Is this something I do need to watch for?

---

### Post by lha on 2006-01-21
[QUOTE=glave]No worries! All is well now. I booted from a live cd, cfdisk'd my partitions on both drives, rebooted from an install cd and everything went peachy.

I followed the instructions from step 7 of that one page, and voila! I went to test things out and it went perfect. Thanks for all the help.

Last question though, I've read about grub being on raid and not wanting to recognize new kernel updates on both grub installations. Is this something I do need to watch for?[/QUOTE]

That's great!

I have upgraded my kernel once and I haven't run into any problems. (I know this doesn't guarantee there will be no problems. So maybe you should pay a bit attention to it. Who knows?)

---

