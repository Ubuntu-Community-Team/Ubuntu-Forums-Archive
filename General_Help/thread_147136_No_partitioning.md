---
title: "No partitioning"
date: 2006-03-19
forum: General Help
---

### Post by jpotex on 2006-03-19
Hey. I'm trying to install Ubuntu 5.10, but there is a problem that I can't understand. 

Normally the installation starts with partitioning after it has identified hardware, network and things like that. But not in my case. I can't get to the partitioning part as the installation program instead take me to a part where I can configure raid, volumes and things like that. Any ideas how I can get to the partioning instead? 

If I try to install on my sister's computer, it works just fine. But not on my own computer.

---

### Post by jerrykenny on 2006-03-19
I think I vaguely remember that page . . . . surely one of the last options is to "manually edit the partition table" or something like that ?

That would be the option for you . . . . are you dual booting ? remember to defrag windows first if you are . . .

---

### Post by az on 2006-03-19
[QUOTE=jpotex]. But not in my case. I can't get to the partitioning part as the installation program instead take me to a part where I can configure raid, volumes and things like that. [/QUOTE]

That is sorta part of the partitionner.  I gues it is not detecting and ide hardware but only raid hardware.  What kind of box is it?  Can you get to that part and CTRL-ALT-F2 to the shell and run
parted /dev/***  (whatever your device is, hda1 hdb1 sda1 scd12...whatever...)
print

---

### Post by jpotex on 2006-03-22
[QUOTE=azz]That is sorta part of the partitionner.  I gues it is not detecting and ide hardware but only raid hardware.  What kind of box is it?  Can you get to that part and CTRL-ALT-F2 to the shell and run
parted /dev/***  (whatever your device is, hda1 hdb1 sda1 scd12...whatever...)
print[/QUOTE]

What will happen when I do that?

---

### Post by justleen on 2006-03-22
it will run parted, a partitioning tool

---

### Post by jpotex on 2006-03-22
[QUOTE=justleen]it will run parted, a partitioning tool[/QUOTE]

Ok.

However that didn't help me. The partition part in the installation still can't find my harddrive for making partitions on it and use it.

I tried listing it with "sudo fdisk -l" with no success. I can't see any sda-entries in /etc/fstab either.

---

### Post by az on 2006-03-22
Is this a new hard drive?  Did you install anything else on the ide cable?  Are the devices detected by your bios?  Are there settings you can change in your bios?  Jumpers to play around with?  Are both devices set to master?  Is the cable plugged in the right way?

Is it raining?  Are you wearing shoes and socks?

---

### Post by jpotex on 2006-03-25
[QUOTE=azz]Is this a new hard drive?  Did you install anything else on the ide cable?  Are the devices detected by your bios?  Are there settings you can change in your bios?  Jumpers to play around with?  Are both devices set to master?  Is the cable plugged in the right way?

Is it raining?  Are you wearing shoes and socks?[/QUOTE]

Windows XP is installed on the biggest partition on the hard drive. It's a s-ATA, so I guess there are no IDE-cables. The dvdrom is something like that too.. what I can see, there are no IDE-cables connected between the dvdrom and the motherboard.. it's another type of cable.

I cannot answer the last questions as I don't know. It's a Fujitsu-Siemens Scaleo-T computer I'm using.

---

