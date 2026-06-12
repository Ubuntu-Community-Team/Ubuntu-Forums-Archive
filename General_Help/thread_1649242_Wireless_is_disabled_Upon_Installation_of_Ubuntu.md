---
title: "Wireless is disabled Upon Installation of Ubuntu"
date: 2010-12-19
forum: General Help
---

### Post by Neliel on 2010-12-19
I don't usually have any issues with installing ubuntu but I figured I would ask around here before I try anything major. I just installed the latest version of ubuntu on a compaq presario cq60. I have no issues connecting to the internet via ethernet but for some reason the wireless says its disabled in the top corner. Now there is a button that has the wireless off/on capablilty but whats strange is in Windows it would always boot to be off and I would have to press it to activate it. It boots orange but when ubuntu boots it goes blue(on, but clearly it isn't.

I basically wanted to know if anyone has any ideas on how to fix this without me doing some probing with my soldering iron.

Any help is appreciated.

---

### Post by Torombolo on 2010-12-19
happen to me on 10.04 with my gateway laptop, ethernet and ran the System / administration / Hardware drivers, and it found my broadcom Card, installed, restart worked great.

---

### Post by Neliel on 2010-12-19
Alright I'll try it.

---

### Post by Neliel on 2010-12-20
Yeah no dice. The only thing that comes up when I choose that are the video drivers for Nvidia and I already activated the reccomended one.

---

### Post by Torombolo on 2010-12-20
open terminal an type

```
sudo /etc/init.d/networking start
```

Or
```
sudo /etc/init.d/networking restart
```

---

### Post by Neliel on 2010-12-20
The first one gave me this reply

Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service networking start. Since the script you are attempting to invoke has been conerted to an upstart job, you may also use the start (8) utility, e.g. start networking networking stop/waiting

the second one seemed to reconfigure them and ignored the wired connection, but that didnt work either.

---

### Post by Ibidem on 2010-12-20
Do you happen to know what the wireless chipset is?
If you don't, what's the output when you run ```
lspci
```in the terminal?

---

### Post by Neliel on 2010-12-20
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

---

### Post by Ibidem on 2010-12-20
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
is the relevant line.
AR5001 is supported by ath5k or madwifi (ath_pci)

Is the driver 'ath5k' loaded?
(run 'lsmod|grep ath5k')
Also, what network interfaces show up when you run 'ifconfig'?

---

### Post by Neliel on 2010-12-20
The above list is what I received when typing that in.

---

### Post by Neliel on 2010-12-20
This shows up when running the ifconfig command.
eth0      Link encap:Ethernet  HWaddr 00:1f:16:68:4b:fa  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe68:4bfa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4265753 (4.2 MB)  TX bytes:428325 (428.3 KB)
          Interrupt:42 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

---

### Post by Ibidem on 2010-12-20
I apologize for double-posting.
Anyhow, I'd run two commands in the terminal for more info:
```
 lsmod|grep ath #List all modules with 'ath' in the name
#since all Atheros wireless drivers include that 
ifconfig #list all network interfaces 
```

I know that what I'd do is go install madwifi-hal from source; but that certainly won't be easy.
be a simple process.

---

### Post by Neliel on 2010-12-20
This is what I received when running the atheros command
ath5k                 143332  0 
mac80211              266657  1 ath5k
ath                    10413  1 ath5k
cfg80211              170293  3 ath5k,mac80211,ath
led_class               3393  1 ath5k
 

the ath5k is highlighted in red in the terminal.

---

### Post by Neliel on 2010-12-20
Running those commands only repeated the information I already presented. How would I install the madwifi

---

### Post by Ibidem on 2010-12-20
[http://ubuntuforums.org/showthread.php?t=1484242]("http://ubuntuforums.org/showthread.php?t=1484242")
is a decent howto, but I suggest a couple changes:
1.  You shouldn't need to add any packages except perhaps uudecode. (Replaces steps 1-5)
2.  Download [ http://snapshots.madwifi-project.org/madwifi-trunk-current.tar.gz]("http://snapshots.madwifi-project.org/madwifi-trunk-current.tar.gz") to /home/<user>/; then extract it. (Replaces step 7)

3. Open a terminal, and run 'cd madwifi-trunk-r*' (Step 8)
Then run 'sudo -i', as per step 6
Follow steps 9 and on.

---

### Post by Neliel on 2010-12-22
Is it supposed to ask me to insert the cd when using the command sudo apt-get update?

---

### Post by Neliel on 2010-12-22
Okay I believe I fixed it but am currently unable to actually test it since I don't have a wireless router, but now the button is orange and the application wicd is installed

Any real way to test it without using a wireless router?

---

