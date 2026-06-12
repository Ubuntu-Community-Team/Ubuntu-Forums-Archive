---
title: "Installing Realtek wireless card driver"
date: 2011-06-14
forum: General Help
---

### Post by misterbreadcrum on 2011-06-14
Hello all, I'm having trouble connecting to the internet without a wired connection.  I just made the jump from dual-booting windows and Ubuntu to sole-booting Ubuntu, and now my computer won't detect networks in range.  My card is a RTL8101E/RTL8102E PCI Express Fast Ethernet controller by Realtek.  When running the autorun.sh in terminal I get this output:

Check old driver and unload it.
rmmod r8169
ERROR: Removing 'r8169': Operation not permitted
Build the module and install
/home/colin/Documents/r8101-1.020.00/src/r8101_n.c: In function ‘rtl8101_check_link_status’:
/home/colin/Documents/r8101-1.020.00/src/r8101_n.c:858:4: warning: suggest parentheses around comparison in operand of ‘&’
/home/colin/Documents/r8101-1.020.00/src/r8101_n.c:878:5: warning: suggest parentheses around comparison in operand of ‘&’
Check old driver and unload it.
rmmod r8169

Simply connecting to the internet should not be a problem this monumental, and I'm getting very frustrated.  If anyone has any ideas as to what to do I'd greatly appreciate it

---

### Post by gandaran on 2011-06-14
>  RTL8101E/RTL8102E PCI Express Fast Ethernet controller by Realtek
is this the wireless device? or just ethernet?
look, better post the output of 
```
lspci
```
so we can see all devices first

---

### Post by misterbreadcrum on 2011-06-14
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
**01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)**
15:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
15:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20)
15:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
15:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

I set what I believe to be my card in bold

---

### Post by gandaran on 2011-06-14
no wireless device here, only ethernet, what type of computer do you have, laptop or desktop? and what type of wireless card?, pci, usb or pcmcia?

---

### Post by misterbreadcrum on 2011-06-14
I have a Toshiba Satellite m-645 laptop.  How is that possible? Just yesterday I was on the internet sans an ethernet cable.  How in the world did it just get rid of it?

---

### Post by gandaran on 2011-06-14
> **misterbreadcrum said:**
> I have a Toshiba Satellite m-645 laptop.  How is that possible? Just yesterday I was on the internet sans an ethernet cable.  How in the world did it just get rid of it?
could have broken down then it wont be detected, if it worked before try running the live cd again just to check.

---

### Post by misterbreadcrum on 2011-06-14
I'll boot from the live cd once again, but I don't understand how a wireless card could have simply broken down and failed to be detected.  I'll post back when I've rebooted

---

### Post by misterbreadcrum on 2011-06-14
My wireless network remains undetected and the terminal shows no new wireless card.  So what gives? It's not like the damn thing just got up and left

---

### Post by misterbreadcrum on 2011-06-14
Hazaa! The problem has been solved!  I did rfkill list and saw that wireless lan was hardblocked.  I did sudo rfkill unblock all and redid rfkill list and lan was no longer hardblocked!  What a strange situation that was.  Thanks for the help!

---

