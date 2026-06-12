---
title: "CQ10-525dx Netbook wireless 802.11b/g/n Wi-Fi not working!"
date: 2010-11-27
forum: General Help
---

### Post by xCasualty on 2010-11-27
Hello, I downloaded all the additional drivers from ubuntu and my wireless seems to not work at all. Maybe I'm not adding it correctly, but when I do it says it's connected but I can't get on firefox or anything. Please let me know if Broadcom is fixable. Thanks!

---

### Post by carl4926 on 2010-11-27
Post the result of this

```
lspci -nnk
```

---

### Post by xCasualty on 2010-11-27
xcasualty@Netbook:~$ lpsci -nnk
No command 'lpsci' found, did you mean:
 Command 'lspci' from package 'pciutils' (main)
lpsci: command not found
xcasualty@Netbook:~$ lpsci-nnk
lpsci-nnk: command not found


guess it didnt work

---

### Post by Quackers on 2010-11-27
Have a look at this thread and see if things look familiar, then follow the link in post # 3 for a possible resolution

[http://ubuntuforums.org/showthread.php?t=1631638](http://ubuntuforums.org/showthread.php?t=1631638)

lspci not lpsci

---

### Post by xCasualty on 2010-11-27
bad case of dyslexia....

```
xcasualty@Netbook:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
    Subsystem: Hewlett-Packard Company Device [103c:148a]
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
    Subsystem: Hewlett-Packard Company Device [103c:148a]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:148a]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:148a]
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:148a]
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:148a]
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:148a]
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:148a]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:148a]
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:148a]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:148a]
    Kernel modules: i2c-i801
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:148a]
    Kernel driver in use: r8169
    Kernel modules: r8169
01:00.1 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5288] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:148a]
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:145c]
    Kernel driver in use: wl
    Kernel modules: wl

```

---

### Post by Quackers on 2010-11-27
post # 4 dude :-)

---

### Post by xCasualty on 2010-11-27
Quackers,

he said:

i think for your version it's on the installer.

put the installer in an open it, go to pool-> restricted-> b-> bcmwl

double click on the deb file.

you'll most likely need to reboot for it to load.



what does he mean by installer?

---

### Post by Quackers on 2010-11-27
don't know boss -ask him :-)

---

### Post by carl4926 on 2010-11-27
```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:145c]
    Kernel driver in use: wl
    Kernel modules: wl
```
Looks like you have the driver installed to me

try

```
sudo modprobe wl
```
then reboot

---

### Post by xCasualty on 2010-11-27
Hey Carl,

When I type that code into the terminal I get:

```

FATAL: Module w1 not found.

```

---

### Post by xCasualty on 2010-11-27
it was wl sorry. I did that and now I'm restarting

---

### Post by xCasualty on 2010-11-27
Restarted computer and it is STILL not connecting.

---

### Post by carl4926 on 2010-11-27
wl (lower case L) !

---

### Post by xCasualty on 2010-11-27
I did do a lowercase L
then is asked me for my password. I typed it, and pressed enter then it created a new line of code: xcasualty@Netbook:~$


I restarted and then tried to connect again and nothing worked. It's saying Connection Established no matter what network I type in while creating a new wireless network. But none of them give me internet connection. My routers name is "NetGear" and theres no password what-so-ever. No WEP or anything.

---

### Post by carl4926 on 2010-11-27
what do get from

```
sudo iwlist scan
```

---

### Post by xCasualty on 2010-11-27
```

lo       Interface doesn't support scanning.

eth0     Interface doesn't support scanning.

eth1     Scan completed:
         Cell 01 - Address: C0:3f:0E:6D:33:74
         ESSIS:"NetGear"
         Mode:Managed
         Frequency:2.412 GHz (Channel 1)
         Quality:5/5  Signal level: -42 dBm Noise level: -93 dBm
         IE: Unkwon: DD7F00.... and so on...

```

---

### Post by xCasualty on 2010-11-27
After running that last line of code you gave me, when I click on the wireless connection it actually lists all of the wireless connections. So I'm guessing it fixed it. but I'll let you know if I connect or not.

---

### Post by xCasualty on 2010-11-27
Well I click on "NetGear" in the available connections, and it doesn't connect.

---

### Post by carl4926 on 2010-11-27
Is this same netbook also connecting with windows when you boot windows (if you have it)?

---

### Post by xCasualty on 2010-11-27
now its saying

lo   Interface doesn't support scanning.

eth0   Inerface doesn't support scanning.

eth1  Failed to read scan data: Invalid Argument.

---

### Post by carl4926 on 2010-11-27
Looking here:
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

Your device says:
> 14e4:4727 
   partially supported 2.6.33 and later 
   ? 
   b/g 
   ? 


So you could try unloading wl and try the b43
```
sudo apt-get install b43-fwcutter
```
```
sudo modprobe b43
```

---

### Post by xCasualty on 2010-11-27
Carl,

This fixed the problem. I can view all available wireless connections and it's letting me connect.

Much thanks!:D

---

### Post by carl4926 on 2010-11-27
> **xCasualty said:**
> Carl,

This fixed the problem. I can view all available wireless connections and it's letting me connect.

Much thanks!:D

Great news
Well done!

---

### Post by Quackers on 2010-11-27
mmmmmmmm  Lake District - sounds like heaven :-)

---

### Post by carl4926 on 2010-11-27
> **Quackers said:**
> mmmmmmmm  Lake District - sounds like heaven :-)
Pretty cold ATM
And a smattering of the white stuff

Here is local web cam
[http://www.fba.org.uk/index/ferrycam](http://www.fba.org.uk/index/ferrycam)

---

### Post by Quackers on 2010-11-27
> **carl4926 said:**
> Pretty cold ATM
And a smattering of the white stuff

Here is local web cam
[http://www.fba.org.uk/index/ferrycam](http://www.fba.org.uk/index/ferrycam)

No problem for a duck :-)

---

### Post by xCasualty on 2010-11-27
> **Quackers said:**
> No problem for a duck :-)

hahahaha

---

### Post by carl4926 on 2010-11-27
> **Quackers said:**
> No problem for a duck :-)

You'd have to be 'Quackin' 'Quackers' to get in the lake today.

Hey. We'll be slapped for off topic if we are not careful;)

---

### Post by xCasualty on 2010-11-29
> **carl4926 said:**
> You'd have to be 'Quackin' 'Quackers' to get in the lake today.

Hey. We'll be slapped for off topic if we are not careful;)


Meh, who cares if you're off topic, issue was resolved. Hahaha ;)

---

### Post by Urbuntus on 2011-01-27
I have the same problem as OP. Only that it doesn't show for me eth1.
Tried already the suggested solutions (e.g. pool-> restricted-> b-> bcmwl and executing the deb file) but no changes.
Any alternative suggestions?

> **xCasualty said:**
> ```

lo       Interface doesn't support scanning.

eth0     Interface doesn't support scanning.

eth1     Scan completed:
         Cell 01 - Address: C0:3f:0E:6D:33:74
         ESSIS:"NetGear"
         Mode:Managed
         Frequency:2.412 GHz (Channel 1)
         Quality:5/5  Signal level: -42 dBm Noise level: -93 dBm
         IE: Unkwon: DD7F00.... and so on...

```

---

