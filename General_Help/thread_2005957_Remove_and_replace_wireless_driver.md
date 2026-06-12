---
title: "Remove and replace wireless driver"
date: 2012-06-18
forum: General Help
---

### Post by Longtrain on 2012-06-18
I have 11.10 on a Toshiba Satellite C6550-S5139 LT, in both this version and 12.04, the unit will hard lockup when it tries to connect to any wireless source, ethernet networking works fine.

I started on 12.04 and went to 11.04 after discovering this problem, can the wireless driver be removed and reinstalled?  If so, can you assist me in this process?

Thanks,

Tony

BTW: LT came with Win7 and wireless was fine until the switch over.

---

### Post by mikewhatever on 2012-06-18
Generally speaking, yes, but we'll need to see the output of the following:

lspci -nnk | grep -iA2 net

---

### Post by Longtrain on 2012-06-18
Thanks, this is what I got back...

user@PCHome:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8181]
    Kernel driver in use: rtl8192ce
--
06:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: atl1c
user@PCHome:~$

---

### Post by mikewhatever on 2012-06-19
Thanks. Did you have to do anything to install rtl8192ce, or is it the built in driver?

---

### Post by Longtrain on 2012-06-19
> **mikewhatever said:**
> Thanks. Did you have to do anything to install rtl8192ce, or is it the built in driver?

No, I don't believe so, just ran the install.  In prior versions, maybe 10ish or so I had to search for other drivers after the install, but that was on a Lenovo Netbook.

Thanks,  Tony

---

### Post by mikewhatever on 2012-06-20
Right, in this case, you can't really uninstall, but can blacklist it, which would prevent the rtl8192ce module from loading on startup. Just add **blacklist rtl8192ce** at the end of the /etc/modprobe.d/blacklist.conf file.
Now, you can get an alternative from [Realtek]("http://www.realtek.com.tw/search/default.aspx?keyword=8192ce") and install it. There are several options, but the first one, RTL8188CE (Software), looks just right.
To install, download the archive for Unix/Linux, and then:

```
cd Downloads

tar xf 92ce_se_de_linux_mac80211_0005.1230.2011.tar.gz

cd rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/

sudo apt-get install build-essential

make

sudo make install
```

PS: Hope it works. A small disadvantage is, you'd have to reinstall the driver after every kernel update (about once a month or so).

---

### Post by Longtrain on 2012-06-20
I downloaded the file and ran the commands, seemed go ok...here's what I get listing the network commands

user@PCHome:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8181]
    Kernel modules: rtl8192ce
06:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: atl1c
user@PCHome:~$ 

However, the LT still locks up if I remove the ethernet cable on boot.  The network menu shows a new "Wired Connection1", but no wireless information at all.
Added a wireless connection, made no difference, pull the cable or without locks up tighter then a drum.

Any other ideas or did I miss something?  Maybe not the wireless???  When I boot now I get the " Ubuntu music" three times then it locks up.  Plug the ethernet in reboot, works, as long as I'm wired.

Here's my other threads...

[http://ubuntuforums.org/showthread.php?t=1991271](http://ubuntuforums.org/showthread.php?t=1991271)
[http://ubuntuforums.org/showthread.php?t=2002355](http://ubuntuforums.org/showthread.php?t=2002355)

Basically, the same request for help, but no replies.

Thanks for your help, it is appreciated.

Tony

---

### Post by mikewhatever on 2012-06-20
Hm..., troubleshooting lockups can be tricky. Is Ubuntu the only operating system installed? If you have Windows on that machine, does it work well? 
Another thing that might be useful is the output of **lspci**, that should show the hardware basics.
...and the last I can think at the moment is the logs. They may have useful errors or messages.

---

### Post by Baulageng on 2012-06-20
I'm working on a machine in which someone (wasn't me!) installed a D-Link
DWL-G550 wireless adapter without first installing the third party driver.
Vista installed a generic "Atheros Wireless Network Adapter" driver. There's
no error messages and the device appears in the device manager but it
doesn't detect any wireless networks even though other machines do. I want
to install the correct driver and I've run the driver software to install it
but the old driver remains. When I right-click on the device in device
manager and choose "update driver software" and point it to the new driver
it doesn't load it. I can tell this by the date of the driver and the fact
that the name remains "Atheros Wireless Network Adapter". I tried
uninstalling the driver but it just picks it back up and installs it again.
I tried physically removing the device and then booting up and shutting down
and reinstalling it and letting Windows pick it up again but the same driver
gets loaded.

---

### Post by Longtrain on 2012-06-20
> **mikewhatever said:**
> Hm..., troubleshooting lockups can be tricky. Is Ubuntu the only operating system installed? If you have Windows on that machine, does it work well? 
Another thing that might be useful is the output of **lspci**, that should show the hardware basics.
...and the last I can think at the moment is the logs. They may have useful errors or messages.

No, no Windows, my wife isn't real happy with me for tossing it.  I have used Ubuntu on other LT's without any problems, until this one...

This is the output from lspci...

user@PCHome:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: ATI Technologies Inc AMD Radeon HD 6310 GraphicsATI
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
06:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)
user@PCHome:~$ 

How can obtain the logs that you mentioned?

Thanks again, really appreciate your time and expertise.

Tony

---

### Post by mikewhatever on 2012-06-21
I think it would be worthwhile to experiment with another distro to exclude hardware problems. Logically, if you get the same lockups across different operating system, that would point to faulty hardware, in which case, the first thing to do is probably run memtest. Memtest is a RAM testing program you can select from the Ubuntu boot screen (may need to hold the Shift key after the BIOS screen to see it).

The logs are just text files (some of them archived), located in /var/log. They can be open with any text editor from the Ubuntu installation or a Live CD/USB, so if possible, locate the **dmesg** log and post it to pastebin.com (and the link here).

---

