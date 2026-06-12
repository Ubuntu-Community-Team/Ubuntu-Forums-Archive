---
title: "PC powers-off during Gpart tasks"
date: 2009-09-06
forum: General Help
---

### Post by Blu-bit on 2009-09-06
Good Evening,

I have two primary partitions on my SATA HD in AHCI-mode and want to shrink the size of one partition, move it to the end of the disk and allocate the free space to the first/other primary partition.

Trying to move the partition to the end fails as the PC simply powers off every time.
There are no known hardware issues, RAM tested, CHKDSK passed and the PC works fine otherwise.
I tried using GParted Live but I experience the same problem...

Anyone got an idea?
Thanks in advance.

---

### Post by earthpigg on 2009-09-06
shifting partitions around can be a CPU-intensive task.

have you ruled out the CPU overheating and automatically sending the power off signal to prevent damage to itself? this would only really be a concern if you haven't cleaned the inside of the system out in ages, or if a fan stopped working...

way to rule out/confirm without opening the case:

run an ubuntu live cd (it includes gparted).

in the live enviornment, install and configure lm-sensors:
> sudo apt-get install lm-sensors
sudo sensors-detect

verify that it works by running 'sensors' in a terminal.

and run 'sensors' in a terminal periodically while attempting to modify the partitiont in gparted... see if your CPU temp is approaching temperatures over 80C.

---

### Post by davetv on 2009-09-06
in a terminal type "acpi -V" shows cpu temp

---

### Post by Blu-bit on 2009-09-07
Hello,
 
Yeah you guys were right... It was thermalrunaway.
As the fan was clean, I added a hairdryer (without heating) for additional cooling.
Worked great, well a bit loud :)
 
However, how come does this only happen whilst using Ubuntu LiveCD?
I was on a LAN the other day, 22 hours and my machine was running without an issue, can it be that ubuntu live cant access the fan settings?
 
With kind regards,
Jadm

---

### Post by earthpigg on 2009-09-07
it probably has more to do with how CPU-intensive *massive partitioning modifications* are than with it being on the LiveCD.

if you wanted to verify this (you probably dont care enough, but IF...):

start ubuntu like normal, from your computers internal hard drive.

plug in an external hard drive that has no data you care about keeping on it. 

delete all partitions on that external hard drive.

create three partitions, one NTFS, one ext4, and one FAT32, fill them all up with data.

try using gparted to move those partitions around on that hard drive.

my hypothesis: you will watch your CPU start going crazy again and shut down to prevent damage to itself.

---

### Post by Blu-bit on 2009-09-08
Okay...
 
I'll give that a try for the sake of interest.
Thanks for everything.

---

### Post by Exodist on 2009-09-08
Any chance you know what the Wattage is of you Power Supply and are you running any high end video cards?
You may not have enough wattage thus this will cause the entire system to run hot also?

---

