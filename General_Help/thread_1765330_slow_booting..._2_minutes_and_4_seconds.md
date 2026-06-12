---
title: "slow booting... 2 minutes and 4 seconds"
date: 2011-05-23
forum: General Help
---

### Post by micael3000 on 2011-05-23
Hello...

I would like to know how to speed up ubuntu's boot... Mine is taking too much time! (This time 2:04, some times it goes over 3 minutes!)...

[Here]("http://postimage.org/image/1ooefmo10/full/") is an image from bootchart. Hope anyone can help me :)

Thanks.

---

### Post by linuxinstalledfromhdd on 2011-05-23
Can you do me a favor and post the results in terminal of:[FONT=monospace][B]

hwinfo --short
[/B][/FONT]

---

### Post by micael3000 on 2011-05-23
Hello linuxinstalledfromhdd, thanks for helping...
Here is the output:

> cpu:                                                            
                       Intel(R) Core(TM)2 Duo CPU     P7550  @ 2.26GHz, 1600 MHz
                       Intel(R) Core(TM)2 Duo CPU     P7550  @ 2.26GHz, 2266 MHz
keyboard:
  /dev/input/event7    Dell Keyboard
  /dev/input/event3    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Dell USB Mouse
  /dev/input/mice      SynPS/2 Synaptics TouchPad
graphics card:
                       ATI M92 [Mobility Radeon HD 4500 Series]
sound:
                       Intel 82801I (ICH9 Family) HD Audio Controller
                       ATI RV730XT Audio device [Radeon HD 4670]
storage:
                       Intel ICH9M/M-E SATA AHCI Controller
network:
  eth0                 Broadcom NetLink BCM5784M Gigabit Ethernet PCIe
  eth1                 Dell Wireless 1397 WLAN Mini-Card
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
  eth1                 Ethernet network interface
  vboxnet0             Ethernet network interface
disk:
  /dev/sda             ST9500325AS
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda5            Partition
  /dev/sda6            Partition
  /dev/sda7            Partition
cdrom:
  /dev/sr0             TSSTcorp DVD+-RW TS-T633C
usb controller:
                       Intel 82801I (ICH9 Family) USB UHCI Controller #4
                       Intel 82801I (ICH9 Family) USB UHCI Controller #5
                       Intel 82801I (ICH9 Family) USB UHCI Controller #6
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #1
                       Intel 82801I (ICH9 Family) USB UHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #3
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #1
bios:
                       BIOS
bridge:
                       Intel Mobile 4 Series Chipset Memory Controller Hub
                       Intel Mobile 4 Series Chipset PCI Express Graphics Port
                       Intel 82801I (ICH9 Family) PCI Express Port 1
                       Intel 82801I (ICH9 Family) PCI Express Port 2
                       Intel 82801I (ICH9 Family) PCI Express Port 3
                       Intel 82801 Mobile PCI Bridge
                       Intel ICH9M LPC Interface Controller
hub:
                       Linux 2.6.38-8-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.38-8-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.38-8-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.38-8-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.38-8-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.38-8-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.38-8-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.38-8-generic uhci_hcd UHCI Host Controller
                       Broadcom BCM2046B1
memory:
                       Main Memory
bluetooth:
                       Dell Wireless 365 Bluetooth Module
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       Intel 82801I (ICH9 Family) SMBus Controller
  /dev/input/event9    Microdia Laptop_Integrated_Webcam_2M


---

### Post by micael3000 on 2011-05-25
Hello? :S

---

### Post by micael3000 on 2011-05-29
bump :|

---

### Post by sbraz on 2011-05-29
i'm installing bootchart right now, thanks for making me discover this program.

this issue might depend on various factors: please reboot and post the result of **sudo dmesg**. this could reveal if it's a kernel issue.

it could also depend highly on how fast your hdd loads data, or maybe there's something wrong with it: check disks's SMART status with GSmartControl, you should find it in ubuntu software center.

rebooting... in 3..2.... no wait! there's a kernel compiling! LOL

---

### Post by linuxinstalledfromhdd on 2011-05-29
Do you have any NTFS formatted drives hooked to your system?

---

### Post by linuxinstalledfromhdd on 2011-05-29
Do you have any NTFS formatted drives/partitions hooked to your system?

---

### Post by micael3000 on 2011-05-29
Hi, thanks for the answers :D

No, i believe my hard drive is in ext4 (if not, it is ext3). I am mounting no other partition (however I do have some more that I don't use. And I don't have windows.)...

Going to restart and post the results of that command. Thanks :)

---

### Post by micael3000 on 2011-05-29
Hello,

Here is the log (I couldn't attach here so I uploaded at pastebin):
[http://pastebin.com/cmb2tFE5](http://pastebin.com/cmb2tFE5)

Thanks.

---

### Post by linuxinstalledfromhdd on 2011-05-29
Big bump!

---

### Post by sbraz on 2011-05-29
```
[    2.926154] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
**[    3.131673] **usb 4-1.2: new full speed USB device using uhci_hcd and address 4
**[   21.172715]** Adding 9999356k swap on /dev/sda6.  Priority:-1 extents:1 across:9999356k
[   22.044874] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
```

this seems like a fairly big delay. try **lsusb** and **lsusb -v** to find what's that "4-1.2: new full speed USB device using uhci_hcd and address 4". :)
you can also check it by removing usb peripherals one at the time, or even disabling usb entirely from bios.

```
[   62.532515] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   65.382404] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
```
i don't know, i never saw this behaviour but it's ovbiously something regarding the hdd's health or a partition in bad need of needs a fsck.

i'm out of ideas for now, let's hope someone brings in more info.

---

### Post by oldfred on 2011-05-30
You might try some of these settings. I do not know an exact answer. Nomodeset is more for video but maybe noapci?

You might turn off any thing you do not use perhaps bluetooth etc from System, Preferences, Startup Manager. 

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line

You had a lot of acpi issues it seemed.
23.771495] ACPI Warning: _BQC returned an invalid level (20110112/video-473)

---

### Post by linuxinstalledfromhdd on 2011-05-30
Go ahead and try a simple check if you get a chance as well.

Let's try Disk Utility.

In Gnome:

Desktop >> System >> Administration >> Disk Utility

On the left of that screen you will see a list of hard drives or hard drive.

Go ahead and click on it. 

To the right now should be breakdown of the specs for that hard drive.

What is the readout on SMART Status?

---

### Post by micael3000 on 2011-05-30
@[sbraz]("http://ubuntuforums.org/member.php?u=1212104")

lsusb:
```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 413c:8160 Dell Computer Corp. 
Bus 004 Device 004: ID 413c:8162 Dell Computer Corp. 
Bus 004 Device 003: ID 413c:8161 Dell Computer Corp. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6407 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

lsusb -v:
Just can't copy the whole log of this command! If I use lsusb -v > file.txt it still display some errors (that are not logged in the text file on the right position) so, I will post what I can :s

I used "lsusb -v > log.txt"... Here is the content of log.txt:

[http://pastebin.com/bD958aCb](http://pastebin.com/bD958aCb)

And here are the errors that the command shown me (even with the > at the end):
```
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
```

I have no USB device plugged in atm (and had no USB when I did this test).

@[linuxinstalledfromhdd]("http://ubuntuforums.org/member.php?u=1050936")

"Disk is healthy" (With a green circle at its left) << Even not revealing the problem, that's good right? XD


@[oldfred]("http://ubuntuforums.org/member.php?u=852711")

I think I don't have grub2 installed... (Mine is 1.99) I read something about installing it (grub-pc I think) but it seems to be risky.

Checking the other things as soon as I get some free time :P





@ ALL

Thank you for helping! There are really a lot of smart people that seems to know Ubuntu and Linux SO MUCH spending time on this thread :P

---

### Post by sbraz on 2011-05-30
> **micael3000 said:**
> 
Just can't copy the whole log of this command! If I use lsusb -v > file.txt it still display some errors (that are not logged in the text file on the right position) so, I will post what I can :s
I used "lsusb -v > log.txt"... Here is the content of log.txt:


from what i understand there's something weird about an internal bluetooth card wrongly detected as an HID device. [http://natisbad.org/E4300/](http://natisbad.org/E4300/) (scroll down to "bluetooth")

when you run a program using **> textfile** you instruct the shell to redirect stdout (standard output) into a file. on a different stream, errors gets posted through stderr (standard error).  [http://en.wikipedia.org/wiki/Standard_streams](http://en.wikipedia.org/wiki/Standard_streams)
those errors you see aren't actually a problem: if you try **sudo lsusb -v** the problem goes away. :) you were trying to list information which requires admin rights from a normal user.

> **micael3000 said:**
> 
@[linuxinstalledfromhdd]("http://ubuntuforums.org/member.php?u=1050936")

"Disk is healthy" (With a green circle at its left) << Even not revealing the problem, that's good right? XD


it's good, but there might be a problem anyway.

gsmartcontrol (**sudo apt-get install gsmartcontrol**) is a gnome frontend of "smartctl" (which instead runs from command line) similar to "disk utility" but aimed on checking SMART parameters in a fairly comprehensive way (roll your mouse over a value and you get a popup with explaiations). you can save the whole report on a file.
after you install it, you can find it under "applications > system tools" on your gnome menu.
i use it at work when i have to "legally declare" a disk unreliable or dead.

---

### Post by oldfred on 2011-05-30
Grub2 is grub version 1.99 with Natty. It was 1.98 with Maverick, but 1.99 has some signifcant changes. Also the package name for grub2 is grub-pc. 

Do not try any repairs that are for grub legacy or version 0.97. Old grub never made it to version 1.0.

---

### Post by micael3000 on 2011-05-30
Hi,

Here is the output of gsmartcontrol:

```
smartctl 5.40 2010-07-12 r3124 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.6 series
Device Model:     ST9500325AS
Serial Number:    6VE7L84Y
Firmware Version: D005DEM1
User Capacity:    500,107,862,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Tue May 31 00:04:56 2011 BRT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (   0) seconds.
Offline data collection
capabilities:              (0x73) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 137) minutes.
Conveyance self-test routine
recommended polling time:      (   3) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   116   099   006    Pre-fail  Always       -       110385269
  3 Spin_Up_Time            0x0003   099   098   085    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1120
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   077   060   030    Pre-fail  Always       -       57777541
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       2918
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       1019
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   098   000    Old_age   Always       -       693
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   065   052   045    Old_age   Always       -       35 (Lifetime Min/Max 30/35)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       121
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       79
193 Load_Cycle_Count        0x0032   094   094   000    Old_age   Always       -       12428
194 Temperature_Celsius     0x0022   035   048   000    Old_age   Always       -       35 (0 15 0 0)
195 Hardware_ECC_Recovered  0x001a   050   045   000    Old_age   Always       -       110385269
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       37769942403834
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       4263502599
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       393998948
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      2918         -
# 2  Short offline       Completed without error       00%         0         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

---

### Post by sbraz on 2011-05-31
5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0

from what i can see from here as long as these values stays at zero there's no immediate problem with the hard drive. if not zero, they indicate an eventual physical damage to the platter.

---

### Post by micael3000 on 2011-06-01
> **sbraz said:**
> 5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0

from what i can see from here as long as these values stays at zero there's no immediate problem with the hard drive. if not zero, they indicate an eventual physical damage to the platter.

So, no problem at hard drive...

I removed all of the useless stuff on startup applications and it's still lagging (when I type my password at login screen it takes a huge time to show anything but the background image of ubuntu).

---

### Post by sungjoon1992 on 2011-06-01
hey people... i am a ubuntu user.. i am not familiar with using the terminal and all that ...
my latop has two OS... xp and ubuntu 11.04..
the thing is it was fine at first... then i installed compiz extra plugin... 
then i rebooted then it started taking like 5 minutes to boot...
can any one please tell me how to fix this prob?

---

### Post by katykat on 2011-06-01
Remove Compiz,.

lspci

If you have an Nvidia based video chip there are likely to be some conflicts.

Also: Compiz is hardware intensive - if you have an older machine, it may not be able to handle it without more memory, or speed.

---

### Post by micael3000 on 2011-08-02
I have reinstalled the system and now everything is working fine.

---

