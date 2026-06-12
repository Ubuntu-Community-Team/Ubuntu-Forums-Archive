---
title: "Mouse only working when clicked"
date: 2011-10-13
forum: General Help
---

### Post by Simeo on 2011-10-13
This is a weird one. For some reason my USB mouse suddenly stopped working unless I first left-click, then move the mouse. When it stops moving, it's almost like the mouse goes to sleep and is only awakened on a click. 

It's just a plain USB wired mouse and usually works fine plug and play. Ideas?

---

### Post by mikejonesey on 2011-10-13
be verbose on lspci to check states the mouse goes in and out of...

---

### Post by Simeo on 2011-10-13
> **mikejonesey said:**
> be verbose on lspci to check states the mouse goes in and out of...

Well it's working now after 2 reboots. If it starts acting up again I'll find out. This is the lspci output anyway:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

---

### Post by mikejonesey on 2011-10-13
if it starts acting up u'll need verose output on lspci to check what is switching off and on... 

save the following script, run as root for highest level of verbosity...
```
#!/bin/bash
# mike.j - 13/10/2011
# linux pci checker for dummies :P

if [ "$1" != "" ]; then
    searchTerm=$1
    shift
    if [ -z "$(lspci | nl | grep -i "$searchTerm")" ]; then
        echo "device not found..."
    else
        lspci -d $(echo $(lspci -n | nl | head -$(echo $(lspci | nl | grep -i "$searchTerm") | cut -d " " -f 1) | tail -1) | cut -d " " -f 4) -v $@
    fi
else
    echo "please specify peramiters..."
fi

```

eg...
```
./pci-checker.sh mouse -vvv
```

---

### Post by mikejonesey on 2011-10-13
dunno why i sent you to pci devices... half asleap... xinput on verbose is what you want...

same script tweeked for xinput will do what you want...

---

### Post by mikejonesey on 2011-10-13
```
#!/bin/bash
# mike.j - 13/10/2011
# linux xinput checker for dummies :P

if [ "$1" != "" ]; then
    searchTerm=$1
    shift
    searchedDevice=$(xinput list | grep -i $searchTerm | cut -d "=" -f 2 | cut -b 1-2)
    if [ -z "$searchedDevice" ]; then
        echo "device not found..."
    else
        echo "-------- device -------- "
        xinput --list $searchedDevice
        echo "-------- device props -------- "
        xinput --list-props $searchedDevice
    fi
else
    echo "please specify peramiters..."
fi

```

---

