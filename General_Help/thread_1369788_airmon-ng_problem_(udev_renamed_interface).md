---
title: "airmon-ng problem (udev renamed interface)"
date: 2010-01-01
forum: General Help
---

### Post by checkm8 on 2010-01-01
I get the following error in airmon-ng 

udev renamed the interface. Read the following for a solution:
[http://www.aircrack-ng.org/doku.php?id=airmon-ng#interface_athx_number_rising_ath0_ath1_ath2...._ath45](http://www.aircrack-ng.org/doku.php?id=airmon-ng#interface_athx_number_rising_ath0_ath1_ath2...._ath45)

Read the wiki but the only file I have is 

70-persistent-net.rules

and the output is as follows:

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x1049 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1c:25:10:8f:24", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4227 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:77:b0:1a:f5", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:50:d8:81:7e", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="ath*", NAME="ath0"

# PCI device 0x168c:0x001a (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:50:d8:81:7e", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x168c:0x001a (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:50:d8:81:7e", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:50:d8:81:7e", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="Ath*", NAME="ath1"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:50:d8:81:7e", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath2"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:50:d8:81:7e", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath3"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:22:33:44:55", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath4"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:24:2a:8b:6c", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath5"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:24:2a:8b:6c", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath6"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:24:2a:8b:6c", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath7"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:24:2a:8b:6c", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath8"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:24:2a:8b:6c", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath9"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:22:33:44:55", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath10"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:22:33:44:56", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath11"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:22:33:44:56", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath12"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:22:33:44:56", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath13"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:24:2a:8b:6c", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath14"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:24:2a:8b:6c", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath15"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:24:2a:8b:6c", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath16"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:22:33:44:55", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath17"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:8f:54:93:98", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath18"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:8f:54:93:98", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath19"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:00:00:00:02", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath20"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:00:00:00:02", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath21"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:00:00:00:02", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath22"

# PCI device 0x168c:0x001a (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:00:00:00:01", ATTR{dev_id}=="0x0", ATTR{type}=="803", KERNEL=="ath*", NAME="ath23"

Any suggestions?

---

