---
title: "can't get eSATA to work with Ubuntu 10.04.01 LTS Server, DP55KG Motherboard"
date: 2010-12-17
forum: General Help
---

### Post by ajk9 on 2010-12-17
Hello, I have run into a problem with eSATA that so far I have been unable to find a solution to it on any of the Ubuntu or Intel forums.  My set up is as below:

OS: Ubuntu 10.04.01 LTS Server (base install)
Motherboard: DP55KG
BIOS: ver. KGIBX10J.86A..5893.2010.1116.0001
Marvell Controller: 88SE6145, BIOS 1.2.0.31
eSATA Device: Seagate 1TB drive inside Shintaro 3.5" SATA External Enclosure
 
Settings in BIOS:
Chipset-SATA Mode: <RAID>
S.M.A.R.T: <Enable>
Discrete-SATA: <Enable>
Discrete-SATA Controller Mode <RAID>


Two internal disk dirves configured with software raid
SDA: Seagate 1TB drive
SDB: Seagate 1TB drive

 
I want to be able to use the eSATA drive as hot swappable to add and remove disks from the raid array.  I have followed a bunch of different instructions from various forums trying to get Ubuntu to recognize the device but nothing has worked.  So far I have:

* Checked the BIOS version, it is the latest version.
* Enabled eSATA in the BIOS by selecting "enable" in the discrete-sata and "raid" in the discrete-sata controller mode.  I read eSATA only works in RAID mode??  Note: The BIOS detects the disk and displays it when in RAID mode but not IDE mode.
* Set Chipset-SATA Mode: <AHCI> and  discrete-sata controller mode: <RAID> - again detected in bios but not in by Ubuntu
* In another forum it was suggested to try and mount the drive using USB first.  Tried mounting the drive with the USB cable, which Ubuntu detects as sdc.  I then unmount and turn off the drive, plug in the eSATA cable and turn the drive back on - nothing.  Not in fdisk, not in logs (dmesg or messages), it's just not detected.
* Tested the hard drive, cable and enclosure on another (Windows 7) machine and it is detected and works)
* Installed scsiadd and tried rescanning, again nothing.
* Boot Ubuntu with eSATA drive attached - not recognised
* Boot Ubuntu then power on eSATA drive - not recognised
* Tried adding blacklist ahci to /etc/modprobe.d/blacklist.conf - again not recognised after reboot.

My understanding is that Ubuntu is suppose to detect the eSATA drive without any extra drivers, my experience is it does not - I am missing something or is anyone else having/had this problem and been able to get eSATA to work?

Any help on this would be appreciated, I did find an answer on the following page [https://bbs.archlinux.org/viewtopic.php?id=105653](https://bbs.archlinux.org/viewtopic.php?id=105653) but I don't believe this applies to Ubuntu.

I am happy to keep trying different things but a point in the right direction would help.


Thanks.

---

### Post by dcstar on 2010-12-17
[LIST=1]
[*]eSATA works fine in Ubuntu (I use it).
[*]There is no "autodetection" of additional drives of any sort in a server environment - only desktops do this.
[*]Plug in and power up the drive, then run the following commands:
```
sudo partprobe
sudo fdisk -l
sudo blkid
```
[*]You should then see the drive and the UUIDs of any partitions on it.
[/LIST]

---

### Post by ajk9 on 2010-12-19
Thanks dcstar, tried that but still got nothing.  Can not see the drive when I use cat /proc/diskstats, do not see it when I use fdisk -l and below is the output of blkid:

/dev/sda1: UUID="2691d216-c9d4-b02f-b0d9-03a64d89b626" TYPE="linux_raid_member"
/dev/sda2: UUID="e89da17b-298b-44b8-8f97-8951b700f363" TYPE="swap"
/dev/sda3: UUID="5674f91d-9ead-e9c5-bc15-f8b4fca40ca1" TYPE="linux_raid_member"
/dev/sdb1: UUID="2691d216-c9d4-b02f-b0d9-03a64d89b626" TYPE="linux_raid_member"
/dev/sdb2: UUID="7904639a-5ece-4cbe-8c01-6c1e35709f05" TYPE="swap"
/dev/sdb3: UUID="5674f91d-9ead-e9c5-bc15-f8b4fca40ca1" TYPE="linux_raid_member"
/dev/md0: UUID="HxYW2B-71h4-38Vd-KBOB-o4QS-wDTn-MVdzm3" TYPE="LVM2_member"
/dev/md1: UUID="27XoTc-bNXK-OMst-fUfk-vvD4-uLDe-bm0H7k" TYPE="LVM2_member"
/dev/mapper/vg1-vg1: UUID="fb22fc25-eadb-4dbc-8742-7bdae616216e" TYPE="ext4"
/dev/mapper/VolGroup-LogVol: UUID="0e93e7e6-51a4-4637-adea-279039a905c1" TYPE="ext4"

Checked with BIOS again and the disk is still seen, just not being detected by Ubuntu - good to know eSATA does work for your Ubuntu installation, now I guess I need to work out what is preventing mine from working :)

---

### Post by dcstar on 2010-12-20
> **ajk9 said:**
> Thanks dcstar, tried that but still got nothing.  Can not see the drive when I use cat /proc/diskstats, do not see it when I use fdisk -l and below is the output of blkid:

/dev/sda1: UUID="2691d216-c9d4-b02f-b0d9-03a64d89b626" TYPE="linux_raid_member"
/dev/sda2: UUID="e89da17b-298b-44b8-8f97-8951b700f363" TYPE="swap"
/dev/sda3: UUID="5674f91d-9ead-e9c5-bc15-f8b4fca40ca1" TYPE="linux_raid_member"
/dev/sdb1: UUID="2691d216-c9d4-b02f-b0d9-03a64d89b626" TYPE="linux_raid_member"
/dev/sdb2: UUID="7904639a-5ece-4cbe-8c01-6c1e35709f05" TYPE="swap"
/dev/sdb3: UUID="5674f91d-9ead-e9c5-bc15-f8b4fca40ca1" TYPE="linux_raid_member"
/dev/md0: UUID="HxYW2B-71h4-38Vd-KBOB-o4QS-wDTn-MVdzm3" TYPE="LVM2_member"
/dev/md1: UUID="27XoTc-bNXK-OMst-fUfk-vvD4-uLDe-bm0H7k" TYPE="LVM2_member"
/dev/mapper/vg1-vg1: UUID="fb22fc25-eadb-4dbc-8742-7bdae616216e" TYPE="ext4"
/dev/mapper/VolGroup-LogVol: UUID="0e93e7e6-51a4-4637-adea-279039a905c1" TYPE="ext4"

Checked with BIOS again and the disk is still seen, just not being detected by Ubuntu - good to know eSATA does work for your Ubuntu installation, now I guess I need to work out what is preventing mine from working :)

If there are no partitions then you won't see any partitions.

Use **parted** to put partitions on it.

---

### Post by ajk9 on 2010-12-22
Again thank you for your response but I had already created a linux partition on this drive, this can be seen as sdc1 when using the USB connection:

#cat /proc/diskstats
   8       0 sda 2314 1972 109290 53700 16729 22427 287424 117910 0 100750 171600
   8       1 sda1 1995 1847 105768 52010 13496 22427 287384 73770 0 56200 125770
   8       2 sda2 87 31 944 330 0 0 0 0 0 330 330
   8       3 sda3 187 72 2042 880 5 0 40 80 0 770 960
   8      16 sdb 2191 1926 152394 53600 16711 22445 287424 113110 0 99330 166710
   8      17 sdb1 1919 1804 149266 51970 13478 22445 287384 69700 0 55410 121670
   8      18 sdb2 87 31 944 330 0 0 0 0 0 330 330
   8      19 sdb3 140 69 1648 650 5 0 40 70 0 710 720
  11       0 sr0 0 0 0 0 0 0 0 0 0 0 0
   9       0 md0 7500 0 254466 0 33907 0 245432 0 0 0 0
   9       1 md1 406 0 3194 0 3 0 24 0 0 0 0
 251       0 dm-0 7332 0 253122 197400 30679 0 245432 1403190 0 108020 1600590
 251       1 dm-1 249 0 1938 3030 3 0 24 60 0 910 3090
   8      32 sdc 51 72 402 120 0 0 0 0 0 120 120
   8      33 sdc1 37 72 290 70 0 0 0 0 0 70 70

and the info from parted:
(parted) print
Model: ST310005 28AS (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary  ext4

however when I plug the drive in using eSATA it is not detected:

#cat /proc/diskstats
   8       0 sda 2314 1972 109290 53700 16783 22436 287880 118070 0 100910 171760
   8       1 sda1 1995 1847 105768 52010 13544 22436 287840 73860 0 56290 125860
   8       2 sda2 87 31 944 330 0 0 0 0 0 330 330
   8       3 sda3 187 72 2042 880 5 0 40 80 0 770 960
   8      16 sdb 2191 1926 152394 53600 16765 22454 287880 113260 0 99480 166860
   8      17 sdb1 1919 1804 149266 51970 13526 22454 287840 69770 0 55480 121740
   8      18 sdb2 87 31 944 330 0 0 0 0 0 330 330
   8      19 sdb3 140 69 1648 650 5 0 40 70 0 710 720
  11       0 sr0 0 0 0 0 0 0 0 0 0 0 0
   9       0 md0 7500 0 254466 0 33954 0 245760 0 0 0 0
   9       1 md1 406 0 3194 0 3 0 24 0 0 0 0
 251       0 dm-0 7332 0 253122 197400 30720 0 245760 1403570 0 108230 1600970
 251       1 dm-1 249 0 1938 3030 3 0 24 60 0 910 3090


so I cant run parted:
# parted /dev/sdc
Error: Could not stat device /dev/sdc - No such file or directory.

For whatever reason Ubuntu just does not see this disk when using eSATA.

---

### Post by milocat on 2010-12-26
I found this thread because I was having the same problem with an ASUS TSMini. I purchased a Themaltake BlacX external enclosure and could not get it to be recognized via eSATA. It worked fine in USB mode just like yours. You actually gave me a clue, my RAID controller was disabled. I enabled it in RAID mode and I still could not get it to work. So just for the heck of it I enabled it in IDE mode and BINGO! I can now access my drive via eSATA!!

Maybe give that at try.

I am using Ubuntu 10.10 Server.

---

### Post by cascade9 on 2010-12-26
Ohhh, great, now intel is doing the same stupid stuff that everybody else is doing...dodgy marvel RAID controllers for the eSATA ports. 

You could just hook one of the intel ICH SATA ports up as an eSATA port, or you could try the fix from here- 

[https://bbs.archlinux.org/viewtopic.php?pid=851588](https://bbs.archlinux.org/viewtopic.php?pid=851588)

---

### Post by dcstar on 2010-12-26
....

---

### Post by dcstar on 2010-12-26
> **cascade9 said:**
> Ohhh, great, now intel is doing the same stupid stuff that everybody else is doing...dodgy marvel RAID controllers for the eSATA ports. 
.........

My eSATA port is built into my Gigabyte GA-MA78GM-S2HP MB, so  I guess I am just lucky that it seems to work natively with Ubuntu.

---

### Post by cascade9 on 2010-12-27
> **dcstar said:**
> My eSATA port is built into my Gigabyte GA-MA78GM-S2HP MB, so  I guess I am just lucky that it seems to work natively with Ubuntu.

Not really 'luck', that board uses the AMD SB 700 southbridge for SATA/eSATA control, and the AMD (and intel) chipsets dont seem to have many problems working with eSATA under linux.

---

### Post by ajk9 on 2011-01-23
Sorry for the long delay in checking this out, I have this machine running live now so it takes a week or so to get time out of hours to take the system down and test.  I am still having no luck although I have not tried the solution provide in the link by cascad9 - mainly as many of the files referenced do not exist on Ubuntu Server 10.04 so I will need to work out the equivalents and then try again.

I did however go back to the bios and change the settings.  I have tried each of the combination's in the BIOS including starting the server with the eSATA device powered on and powered off.  i did get some interesting results.  The options were as follows:

Chipset-SATA Mode: <IDE
Discrete-SATA: <Enable>
Discrete-SATA Controller Mode <IDE>
eSATA drive not detected in BIOS

Chipset-SATA Mode: <IDE>
Discrete-SATA: <Enable>
Discrete-SATA Controller Mode <RAID>
Server would not boot with eSATA powered on but the drive was detected in the BIOS

Chipset-SATA Mode: <RAID>
Discrete-SATA: <Enable>
Discrete-SATA Controller Mode <IDE>
eSATA not detected in BIOS

Chipset-SATA Mode: <RAID>
Discrete-SATA: <Enable>
Discrete-SATA Controller Mode <RAID>
Server would not boot with eSATA powered on, not detected in BIOS

Chipset-SATA Mode: <AHCI>
Discrete-SATA: <Enable>
Discrete-SATA Controller Mode <RAID>
Not detected in BIOS

Chipset-SATA Mode: <AHCI>
Discrete-SATA: <Enable>
Discrete-SATA Controller Mode <RAID>
Drive was detected in the BIOS but not detected on boot by Ubuntu.  Turned the eSATA drive off and on and received the following errors to the console:
[  152.9634127] irq 19: nobody cared (try booting with the "irqpoll" option)
[  152.963582] handlers:
[  152.963605] [<ffffffffa0086bb0>] (ohci_irq_handler+0x0/0x830 [ohci1394])
[  152.963685] [<ffffffff813c7830>] (ata_sff_interrupt+0x0/0x120)
[  152.963750] Disabling IRQ #19

ran dmesg and got:
[  152.963412] irq 19: nobody cared (try booting with the "irqpoll" option)
[  152.963477] Pid: 0, comm: swapper Not tainted 2.6.32-24-server #39-Ubuntu
[  152.963481] Call Trace:
[  152.963484]  <IRQ>  [<ffffffff810c69eb>] __report_bad_irq+0x2b/0xa0
[  152.963498]  [<ffffffff810c6bec>] note_interrupt+0x18c/0x1d0
[  152.963505]  [<ffffffff81019e79>] ? read_tsc+0x9/0x20
[  152.963510]  [<ffffffff810c72ed>] handle_fasteoi_irq+0xdd/0x100
[  152.963515]  [<ffffffff81015d12>] handle_irq+0x22/0x30
[  152.963522]  [<ffffffff8155fc6c>] do_IRQ+0x6c/0xf0
[  152.963527]  [<ffffffff81013b13>] ret_from_intr+0x0/0x11
[  152.963529]  <EOI>  [<ffffffff8130f0fb>] ? acpi_idle_enter_c1+0xa3/0xc1
[  152.963541]  [<ffffffff8130f0da>] ? acpi_idle_enter_c1+0x82/0xc1
[  152.963548]  [<ffffffff8144df67>] ? cpuidle_idle_call+0xa7/0x140
[  152.963555]  [<ffffffff81011e63>] ? cpu_idle+0xb3/0x110
[  152.963561]  [<ffffffff815427ab>] ? rest_init+0x6b/0x80
[  152.963568]  [<ffffffff8187edcc>] ? start_kernel+0x368/0x371
[  152.963574]  [<ffffffff8187e33a>] ? x86_64_start_reservations+0x125/0x129
[  152.963579]  [<ffffffff8187e438>] ? x86_64_start_kernel+0xfa/0x109
[  152.963582] handlers:
[  152.963605] [<ffffffffa0086bb0>] (ohci_irq_handler+0x0/0x830 [ohci1394])
[  152.963685] [<ffffffff813c7830>] (ata_sff_interrupt+0x0/0x120)
[  152.963750] Disabling IRQ #19

and similar in /var/log/messages:
Jan 21 19:09:52 ### kernel: [  152.963477] Pid: 0, comm: swapper Not tainted 2.6.32-24-server #39-Ubuntu
Jan 21 19:09:52 ### kernel: [  152.963481] Call Trace:
Jan 21 19:09:52 ### kernel: [  152.963484]  <IRQ>  [<ffffffff810c69eb>] __report_bad_irq+0x2b/0xa0
Jan 21 19:09:52 ### kernel: [  152.963498]  [<ffffffff810c6bec>] note_interrupt+0x18c/0x1d0
Jan 21 19:09:52 ### kernel: [  152.963505]  [<ffffffff81019e79>] ? read_tsc+0x9/0x20
Jan 21 19:09:52 ### kernel: [  152.963510]  [<ffffffff810c72ed>] handle_fasteoi_irq+0xdd/0x100
Jan 21 19:09:52 ### kernel: [  152.963515]  [<ffffffff81015d12>] handle_irq+0x22/0x30
Jan 21 19:09:52 ### kernel: [  152.963522]  [<ffffffff8155fc6c>] do_IRQ+0x6c/0xf0
Jan 21 19:09:52 ### kernel: [  152.963527]  [<ffffffff81013b13>] ret_from_intr+0x0/0x11
Jan 21 19:09:52 ### kernel: [  152.963529]  <EOI>  [<ffffffff8130f0fb>] ? acpi_idle_enter_c1+0xa3/0xc1
Jan 21 19:09:52 ### kernel: [  152.963541]  [<ffffffff8130f0da>] ? acpi_idle_enter_c1+0x82/0xc1
Jan 21 19:09:52 ### kernel: [  152.963548]  [<ffffffff8144df67>] ? cpuidle_idle_call+0xa7/0x140
Jan 21 19:09:52 ### kernel: [  152.963555]  [<ffffffff81011e63>] ? cpu_idle+0xb3/0x110
Jan 21 19:09:52 ### kernel: [  152.963561]  [<ffffffff815427ab>] ? rest_init+0x6b/0x80
Jan 21 19:09:52 ### kernel: [  152.963568]  [<ffffffff8187edcc>] ? start_kernel+0x368/0x371
Jan 21 19:09:52 ### kernel: [  152.963574]  [<ffffffff8187e33a>] ? x86_64_start_reservations+0x125/0x129
Jan 21 19:09:52 ### kernel: [  152.963579]  [<ffffffff8187e438>] ? x86_64_start_kernel+0xfa/0x109

I guess it's something but I don't know what.  I also realized that when installing the OS I had left the default BIOS settings which is IDE IDE, perhaps if I had of set this to AHCI and RAID in the first place it may have made a difference???

As noted I will try the solution in the link posted by cascade9 - it may be a week or two until I can get to that but I will try it and post back.

---

### Post by dcstar on 2011-02-13
Just found out that you can only Hot-swap drives that use AHCI mode.

My system's drives are set in my BIOS to AHCI, I do not use any BIOS RAID so that is why I can plug in my eSata drive after boot up and then have Ubuntu detect it.

---

### Post by imwithid on 2012-06-16
> **dcstar said:**
> Just found out that you can only Hot-swap drives that use AHCI mode.

My system's drives are set in my BIOS to AHCI, I do not use any BIOS RAID so that is why I can plug in my eSata drive after boot up and then have Ubuntu detect it.

This is odd as I'm having a similar problem. I was able to hook up my external 3TB drive for a while via eSATA, however, those rare times when I had to use WIndows to access the drive, I had to switch to USB mode. Now Ubuntu detects the drive but not the partition information. It sees it as a 3TB blank hard drive. It is capable of reading it via USB, however, I need the speed of eSATA when backing up my internal drive.

My desktop's BIOS is set to AHCI mode, however, no luck.

This is bizarre.

---

