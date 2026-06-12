---
title: "multiple pciehp card present not present errors"
date: 2012-01-28
forum: General Help
---

### Post by gaskit on 2012-01-28
I'm trying to get Ubuntu 11.10 running without issues on an ASRock Ion3D.  There was some fun with the Realtek wifi and network but that seems to be fixed now. 
The problem I'm trying to fix now are thousands of error messages coming from the pciehp module - more than a few times every second.
dmesg repeats the error "Card not present on slot 0-2" followed by "Card present on slot 0-2". Every so often there's a "No new device found" error among the repeated lines.

My error logs are ballooning and use of dmesg is nearly useless as a result.  It takes ages to load and scroll through the logs.  I think the resulting constant disk activity is also stopping my pc from powering down as a result. 

I've read that I can disable the pciehp hotplug module from the kernel - but how can I tell if I really need it ?  I know it's to do with reconnecting devices on the fly and I think the wifi controller is connected internally to a USB header so I'm concerned that by removing the module I'll stop the wifi working properly.
Is there anything else I should be looking at to fix this?

I'm still learning lots about Ubuntu so please be gentle!
Thx

---

### Post by gaskit on 2012-02-03
bumping with more info:

The problem...

```
[ 2050.604038] pciehp 0000:00:1c.5:pcie04: No new device found
[ 2050.604048] pciehp 0000:00:1c.5:pcie04: Cannot add device at 0000:04:00
[ 2050.615144] pciehp 0000:00:1c.5:pcie04: Card not present on Slot(0-2)
[ 2050.619104] pciehp 0000:00:1c.5:pcie04: Card present on Slot(0-2)
```

Last 2 lines repeat endlessly

lspci:

```
chris@ion3d:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
02:00.0 VGA compatible controller: nVidia Corporation GT218 [ION] (rev a2)
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
chris@ion3d:~$ 
```

lsusb

```
chris@ion3d:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
Bus 002 Device 002: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick
Bus 003 Device 002: ID 04f2:0230 Chicony Electronics Co., Ltd 
chris@ion3d:~$
```

---

### Post by zorkerz on 2012-06-25
Did you ever figure anything out around this? 

I seem to be getting these four lines before the system locks up requiring a hard boot. > [ 2095.762378] pciehp 0000:00:1c.0:pcie04: Card not present on Slot(2)
[ 2095.766526] pciehp 0000:00:1c.0:pcie04: Card present on Slot(2)
[ 2096.874175] pciehp 0000:00:1c.0:pcie04: No new device found
[ 2096.874190] pciehp 0000:00:1c.0:pcie04: Cannot add device at 0000:02:00

Not sure what to do about it.

---

### Post by jmfal on 2012-06-25
Take a look at this:

[https://help.ubuntu.com/community/ExpressCard](https://help.ubuntu.com/community/ExpressCard)

I'm not sure the link is working. you should be able to copy/paste URL to google or ......

---

### Post by zorkerz on 2012-06-25
Wow thanks for the quick reply jmfal.
I'm not quite sure how the express card page relates.

---

### Post by jmfal on 2012-06-25
Have you added a usb expansion card or are yiu just getting those errors.

---

### Post by zorkerz on 2012-06-25
I've added nothing to the computer, just getting those errors.

I've also gotten a few [Hardware Error]: Machine check events logged. I don't know if these are related only a few times has the system freeze been right after the MCE. My understanding is that this is some hardware problem. I tried to install and run mcelog but it returns this ```
mcelog: warning: 16 bytes ignored in each record
mcelog: consider an update
```

Here is my /var/log/mcelog
```
mcelog: failed to prefill DIMM database from DMI data
mcelog: mcelog read: No such device
Hardware event. This is not a software error.
MCE 0
CPU 0 BANK 0
TIME 1340634209 Mon Jun 25 10:23:29 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-0 Local-CPU-originated-request Generic Memory-access Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
timeout BINIT (ROB timeout). No micro-instruction retired for some time
failure that caused IERR
STATUS f200084000000800 MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0
CPUID Vendor Intel Family 6 Model 15
Hardware event. This is not a software error.
MCE 1
CPU 0 BANK 5
TIME 1340634209 Mon Jun 25 10:23:29 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_AERR2_TYPE BQ_ERR_AERR2_TYPE
received parity error on response transaction
MCE driven
STATUS f200001014000e0f MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0
CPUID Vendor Intel Family 6 Model 15
Hardware event. This is not a software error.
MCE 2
CPU 1 BANK 5
TIME 1340634209 Mon Jun 25 10:23:29 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
received parity error on response transaction
MCE driven MCE is observed
STATUS f200001030000e0f MCGSTATUS 0
MCGCAP 806 APICID 1 SOCKETID 0
CPUID Vendor Intel Family 6 Model 15
```

Maybe its time to start a dedicated thread for this. I'm getting pretty over my head I only kind of know what most of this stuff means. Your input is greatly appreciated.

---

### Post by jmfal on 2012-06-25
OK , I did a little research and those errors  are not fatal mostly a nuisance.

Try this in a terminal:

```
  sudo gedit /etc/modprobe.d/blacklist.conf    
```

Enter your password and hit enter, the blacklist file will open up and add:

>   #These modules may be causing errors
                   blacklist  pciehp
                   blacklist  shphp        

To the bottom of the file.
If there is no empty line at the bottom ,, put your cursor after the last word on the last line and hit enter key twice.
Make sure that each of the three entries are on a separate line.
You don't have to put the comment I added it just in case you forget why it was blacklisted, Make sure you have # in front of the comment.
When done save and exit,  and restart PC.

---

### Post by zorkerz on 2012-06-25
Ok all set. I'll let you know how it goes.

---

### Post by zorkerz on 2012-06-25
Shoot system is still locking up. Some with the same log messages (Card not present on Slot(2) pciehp 0000:00:1c.0:pcie04: Card present on Slot(2) pciehp 0000:00:1c.0:pcie04: No new device found pciehp 0000:00:1c.0:pcie04: Cannot add device at 0000:02:00) before freeze some without.

I don't know how to go about diagnosing this. What do you do to find out what is wrong, if your system keeps freezing up?

---

### Post by jmfal on 2012-06-25
Is it just the mouse and keyboard freezing ?

Are the windows getting dull or fading?

It probably won't do anything but reboot to the grub screen and  select the recovery kernal >> then select  dpkg  fix broken packages and follow the prompts.

The only way out of a freeze is a hard restart.
try going back to the blacklist file and comment out or remove "shphp".

I'm running out of options myself.

---

