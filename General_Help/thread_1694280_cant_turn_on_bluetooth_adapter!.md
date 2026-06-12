---
title: "cant turn on bluetooth adapter!"
date: 2011-02-24
forum: General Help
---

### Post by birdy.f on 2011-02-24
hello!
      im a new user of ubuntu..i seem to have problem connecting to bluetooth..there is a messege saying there are no bluetooth adapter...how do i turn on the adapter now that iv  switched from windows 7 to ubuntu...my blutooth was working fine in windows...

---

### Post by zenwalker on 2011-02-24
Do you know what is your Bluetooth make/vendor info??

Use lspci or lsusb commands and paste it here if you dont know info. You need to be root to run those commands

---

### Post by birdy.f on 2011-02-24
i went to the terminal and typed lsusb.. the following was generated


Bus 002 Device 003: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:641d Microdia
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

AND THIS... on lspci





00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by zenwalker on 2011-02-24
From the output i dont see any detected Bluetooth adapter listed. Has it been enabled in the BIOS? Please check.

Also do this please dmesg | grep bluetooth 
after sytem booted. Again as root.

---

### Post by birdy.f on 2011-02-24
i wud sound pathetic but how do i enable it in BIOS??

---

### Post by gandaran on 2011-02-24
> **birdy.f said:**
> hello!
      im a new user of ubuntu..i seem to have problem connecting to bluetooth..there is a messege saying there are no bluetooth adapter...how do i turn on the adapter now that iv  switched from windows 7 to ubuntu...my blutooth was working fine in windows...
what exactly was the message displayed, no Bluetooth adapter or could not enable Bluetooth power, if it was something to do with enabling power I recommend to install Blueman from package manager, blueman does a better quick job enabling bluetooth than the default gnome-bluetooth.

---

### Post by birdy.f on 2011-02-25
the messege said no bluetooth adapters present. i dnt hav adapter installed and from the site of dell...its for windows only...so wat should i do?

---

### Post by birdy.f on 2011-02-27
can someone plz reply<1

---

