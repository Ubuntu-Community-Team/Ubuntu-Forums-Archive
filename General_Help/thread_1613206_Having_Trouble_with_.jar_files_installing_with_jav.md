---
title: "Having Trouble with .jar files installing with java and Encoding Video to DVD"
date: 2010-11-04
forum: General Help
---

### Post by Wayne1987 on 2010-11-04
---------------------- 
/Linux Ubuntu 10.10//
-----------------------

I'm trying to install a .jar file to make this encoding program work I guess, but I keep getting blocked.

The file '/home/wayne/Desktop/varsha.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit
Would anybody know of any software that would Encode any type of video format to a dvd/ dvd-dl ?
[ I can't find anything user friendly ]
--------
Adding 
--------
I'm also having trouble running WINE 1.3 or 1.2, what happens is I'll click on the program called wine then it'll log me off, so I must log back in with my password then try it again.  This problem also happens with Zsnes, so I dunno whats going on that could be going wrong.  

--------
One more add
--------
When I'm playing a movie with VLC or any media player the sound begins to become choppy really bad choppy, just wondering about that, music seems to play nicely but movies/ Videos don't.  


{Thanks}

---

### Post by efflandt on 2010-11-04
It is easiest to put any scripts or executables in your own **bin** directory in your home directory so you do not need to type a full path.  But first you need to create your bin.  The next time you login, that will automatically be added to your PATH.

```
mkdir ~/bin
mv ~/Desktop/varsha.jar ~/bin
chmod u+x ~/bin/varsha.jar
```Log out of X and back in.  Then /home/wayne/bin should end up in your PATH:

```
echo $PATH
```Then assuming you have installed the other necessary tools for that (see [http://varsha.sourceforge.net/](http://varsha.sourceforge.net/) ) you could create a Launcher on your Desktop or top panel that runs: **java -jar varsha.jar**

I have not run wine, so I cannot help with that.

Is video copy or just the sound with video.  What cpu and how much RAM do you have?  Post the output of **sudo lspci -v** and put code tags around that by highlighting that output and clicking **#** in the message window to put code tags around it.

---

### Post by Wayne1987 on 2010-11-04
```
Subsystem: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
    Flags: bus master, 66MHz, medium devsel, latency 8
    Memory at d0000000 (32-bit, prefetchable) [size=128M]
    Capabilities: [a0] AGP version 2.0
    Capabilities: [c0] Power Management version 2
    Kernel driver in use: agpgart-via
    Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP] (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: e0000000-e1ffffff
    Prefetchable memory behind bridge: d8000000-dfffffff
    Capabilities: [80] Power Management version 2
    Kernel modules: shpchp

00:07.0 Communication controller: Agere Systems LT WinModem (rev 02)
    Subsystem: Agere Systems LT WinModem
    Flags: bus master, medium devsel, latency 32, IRQ 255
    Memory at e2000000 (32-bit, non-prefetchable) [size=256]
    I/O ports at d000 [size=8]
    I/O ports at d400 [size=256]
    Capabilities: [f8] Power Management version 2

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 3902
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at d800 [size=32]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 3902
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at dc00 [size=32]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 3902
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at e000 [size=32]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 3902
    Flags: bus master, medium devsel, latency 32, IRQ 21
    Memory at e2001000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
    Subsystem: VIA Technologies, Inc. VT8235 ISA Bridge
    Flags: bus master, stepping, medium devsel, latency 0
    Capabilities: [c0] Power Management version 2
    Kernel modules: i2c-viapro, via-ircc

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
    Subsystem: Micro-Star International Co., Ltd. Device 3902
    Flags: bus master, medium devsel, latency 32, IRQ 20
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at e400 [size=16]
    Capabilities: [c0] Power Management version 2
    Kernel driver in use: pata_via
    Kernel modules: pata_via

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
    Subsystem: Micro-Star International Co., Ltd. Device 3902
    Flags: medium devsel, IRQ 22
    I/O ports at e800 [size=256]
    Capabilities: [c0] Power Management version 2
    Kernel driver in use: VIA 82xx Audio
    Kernel modules: snd-via82xx

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
    Subsystem: Micro-Star International Co., Ltd. Device 390c
    Flags: bus master, medium devsel, latency 32, IRQ 23
    I/O ports at ec00 [size=256]
    Memory at e2002000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine

01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266] (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. Device 3908
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    Memory at e1000000 (32-bit, non-prefetchable) [size=512K]
    Memory at d8000000 (32-bit, prefetchable) [size=128M]
    [virtual] Expansion ROM at e0000000 [disabled] [size=64K]
    Capabilities: [dc] Power Management version 2
    Capabilities: [80] AGP version 2.0
    Kernel modules: savagefb

```

---

### Post by Wayne1987 on 2010-11-04
######### ##
# ~Problems~
#  ^^^^^^^
#    1. Movie/ Video Sound Issue.
#    2. Reboot Screen, looks scrambled when shutting down or restarting.
#    3. Some software doesn't work, (Broken software sends me to main password login-screen)
#    4. Firewall, seems to be getting hit a-lot..
#    5. Can't scan computer for viruses because its not allowed.
#    6. System Feels unstable when browsing the Internet, with the firewall on.
#    7. Can't ENCODE video file for dvd tried to but failed big time.
======================================================= 
                                       FIREWALL LOG
=======================================================
```
Time:Nov  4 09:23:03 Direction: Unknown In:eth0 Out: Port:41952 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:03 Direction: Unknown In:eth0 Out: Port:41953 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:03 Direction: Unknown In:eth0 Out: Port:41954 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:03 Direction: Unknown In:eth0 Out: Port:41955 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:03 Direction: Unknown In:eth0 Out: Port:41956 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:04 Direction: Unknown In:eth0 Out: Port:36777 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:04 Direction: Unknown In:eth0 Out: Port:41953 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:04 Direction: Unknown In:eth0 Out: Port:41955 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:04 Direction: Unknown In:eth0 Out: Port:41957 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:05 Direction: Unknown In:eth0 Out: Port:41956 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:07 Direction: Unknown In:eth0 Out: Port:41952 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:07 Direction: Unknown In:eth0 Out: Port:41953 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:07 Direction: Unknown In:eth0 Out: Port:41954 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:07 Direction: Unknown In:eth0 Out: Port:41955 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:07 Direction: Unknown In:eth0 Out: Port:41956 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:07 Direction: Unknown In:eth0 Out: Port:36777 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:07 Direction: Unknown In:eth0 Out: Port:41952 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:08 Direction: Unknown In:eth0 Out: Port:41956 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:08 Direction: Unknown In:eth0 Out: Port:41954 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:10 Direction: Unknown In:eth0 Out: Port:41953 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:10 Direction: Unknown In:eth0 Out: Port:41952 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:10 Direction: Unknown In:eth0 Out: Port:36777 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:10 Direction: Unknown In:eth0 Out: Port:41955 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:10 Direction: Unknown In:eth0 Out: Port:41954 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:10 Direction: Unknown In:eth0 Out: Port:41957 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:11 Direction: Unknown In:eth0 Out: Port:41956 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:13 Direction: Unknown In:eth0 Out: Port:41952 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:13 Direction: Unknown In:eth0 Out: Port:41953 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:13 Direction: Unknown In:eth0 Out: Port:41954 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:13 Direction: Unknown In:eth0 Out: Port:41955 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:13 Direction: Unknown In:eth0 Out: Port:41956 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:13 Direction: Unknown In:eth0 Out: Port:36777 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:13 Direction: Unknown In:eth0 Out: Port:36777 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:14 Direction: Unknown In:eth0 Out: Port:41952 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:14 Direction: Unknown In:eth0 Out: Port:41956 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:14 Direction: Unknown In:eth0 Out: Port:41954 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:14 Direction: Unknown In:eth0 Out: Port:36777 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:20 Direction: Unknown In:eth0 Out: Port:36777 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:22 Direction: Unknown In:eth0 Out: Port:41953 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:22 Direction: Unknown In:eth0 Out: Port:41955 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:22 Direction: Unknown In:eth0 Out: Port:41954 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:22 Direction: Unknown In:eth0 Out: Port:41952 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:22 Direction: Unknown In:eth0 Out: Port:36777 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:22 Direction: Unknown In:eth0 Out: Port:41957 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:23 Direction: Unknown In:eth0 Out: Port:41956 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:25 Direction: Unknown In:eth0 Out: Port:41952 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:25 Direction: Unknown In:eth0 Out: Port:41953 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:25 Direction: Unknown In:eth0 Out: Port:41954 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:25 Direction: Unknown In:eth0 Out: Port:41955 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:25 Direction: Unknown In:eth0 Out: Port:41956 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:25 Direction: Unknown In:eth0 Out: Port:41953 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:25 Direction: Unknown In:eth0 Out: Port:36777 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:26 Direction: Unknown In:eth0 Out: Port:41952 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:26 Direction: Unknown In:eth0 Out: Port:41956 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:26 Direction: Unknown In:eth0 Out: Port:41954 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:32 Direction: Unknown In:eth0 Out: Port:36777 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:41 Direction: Unknown In:eth0 Out: Port:52805 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:43 Direction: Unknown In:eth0 Out: Port:52805 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:44 Direction: Unknown In:eth0 Out: Port:52805 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:46 Direction: Unknown In:eth0 Out: Port:41953 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:46 Direction: Unknown In:eth0 Out: Port:41952 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:46 Direction: Unknown In:eth0 Out: Port:36777 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:46 Direction: Unknown In:eth0 Out: Port:41955 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:46 Direction: Unknown In:eth0 Out: Port:41957 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:46 Direction: Unknown In:eth0 Out: Port:41954 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:47 Direction: Unknown In:eth0 Out: Port:41956 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:48 Direction: Unknown In:eth0 Out: Port:52819 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:49 Direction: Unknown In:eth0 Out: Port:52820 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:49 Direction: Unknown In:eth0 Out: Port:52821 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:49 Direction: Unknown In:eth0 Out: Port:52822 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:49 Direction: Unknown In:eth0 Out: Port:52819 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:49 Direction: Unknown In:eth0 Out: Port:52821 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:49 Direction: Unknown In:eth0 Out: Port:52820 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:49 Direction: Unknown In:eth0 Out: Port:41953 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:49 Direction: Unknown In:eth0 Out: Port:52822 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:50 Direction: Unknown In:eth0 Out: Port:41952 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:50 Direction: Unknown In:eth0 Out: Port:41956 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:50 Direction: Unknown In:eth0 Out: Port:41954 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:50 Direction: Unknown In:eth0 Out: Port:52805 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:51 Direction: Unknown In:eth0 Out: Port:52805 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:55 Direction: Unknown In:eth0 Out: Port:52819 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:55 Direction: Unknown In:eth0 Out: Port:52821 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:55 Direction: Unknown In:eth0 Out: Port:52820 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:55 Direction: Unknown In:eth0 Out: Port:52822 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:56 Direction: Unknown In:eth0 Out: Port:52837 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:56 Direction: Unknown In:eth0 Out: Port:36777 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:57 Direction: Unknown In:eth0 Out: Port:52838 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:57 Direction: Unknown In:eth0 Out: Port:52839 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:57 Direction: Unknown In:eth0 Out: Port:52840 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:57 Direction: Unknown In:eth0 Out: Port:52837 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:57 Direction: Unknown In:eth0 Out: Port:52840 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:57 Direction: Unknown In:eth0 Out: Port:52805 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:57 Direction: Unknown In:eth0 Out: Port:52839 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:58 Direction: Unknown In:eth0 Out: Port:52838 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:59 Direction: Unknown In:eth0 Out: Port:52837 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:59 Direction: Unknown In:eth0 Out: Port:52837 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:59 Direction: Unknown In:eth0 Out: Port:52838 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:59 Direction: Unknown In:eth0 Out: Port:52839 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:23:59 Direction: Unknown In:eth0 Out: Port:52840 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:01 Direction: Unknown In:eth0 Out: Port:52805 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:02 Direction: Unknown In:eth0 Out: Port:52805 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:03 Direction: Unknown In:eth0 Out: Port:52840 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:03 Direction: Unknown In:eth0 Out: Port:52837 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:03 Direction: Unknown In:eth0 Out: Port:52839 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:04 Direction: Unknown In:eth0 Out: Port:52838 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:05 Direction: Unknown In:eth0 Out: Port:52837 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:05 Direction: Unknown In:eth0 Out: Port:52837 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:06 Direction: Unknown In:eth0 Out: Port:52838 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:06 Direction: Unknown In:eth0 Out: Port:52839 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:06 Direction: Unknown In:eth0 Out: Port:52838 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:06 Direction: Unknown In:eth0 Out: Port:52839 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:07 Direction: Unknown In:eth0 Out: Port:52819 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:07 Direction: Unknown In:eth0 Out: Port:52821 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:07 Direction: Unknown In:eth0 Out: Port:52820 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:07 Direction: Unknown In:eth0 Out: Port:52822 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:09 Direction: Unknown In:eth0 Out: Port:52805 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:12 Direction: Unknown In:eth0 Out: Port:52838 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:12 Direction: Unknown In:eth0 Out: Port:52839 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:15 Direction: Unknown In:eth0 Out: Port:52840 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:15 Direction: Unknown In:eth0 Out: Port:52837 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:15 Direction: Unknown In:eth0 Out: Port:52839 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:16 Direction: Unknown In:eth0 Out: Port:52838 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:17 Direction: Unknown In:eth0 Out: Port:52837 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:17 Direction: Unknown In:eth0 Out: Port:52837 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:17 Direction: Unknown In:eth0 Out: Port:52838 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:17 Direction: Unknown In:eth0 Out: Port:52839 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:17 Direction: Unknown In:eth0 Out: Port:52840 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:19 Direction: Unknown In:eth0 Out: Port:52840 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:24 Direction: Unknown In:eth0 Out: Port:52838 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:25 Direction: Unknown In:eth0 Out: Port:52840 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:25 Direction: Unknown In:eth0 Out: Port:52839 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:25 Direction: Unknown In:eth0 Out: Port:52805 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:27 Direction: Unknown In:eth0 Out: Port:52854 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:27 Direction: Unknown In:eth0 Out: Port:52854 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:30 Direction: Unknown In:eth0 Out: Port:52854 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:31 Direction: Unknown In:eth0 Out: Port:52819 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:31 Direction: Unknown In:eth0 Out: Port:52821 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:31 Direction: Unknown In:eth0 Out: Port:52820 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:32 Direction: Unknown In:eth0 Out: Port:52822 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:33 Direction: Unknown In:eth0 Out: Port:52854 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:33 Direction: Unknown In:eth0 Out: Port:52805 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:34 Direction: Unknown In:eth0 Out: Port:52856 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:34 Direction: Unknown In:eth0 Out: Port:52857 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:34 Direction: Unknown In:eth0 Out: Port:52858 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:34 Direction: Unknown In:eth0 Out: Port:52859 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:34 Direction: Unknown In:eth0 Out: Port:52860 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:34 Direction: Unknown In:eth0 Out: Port:41953 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:34 Direction: Unknown In:eth0 Out: Port:41954 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:34 Direction: Unknown In:eth0 Out: Port:52858 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:35 Direction: Unknown In:eth0 Out: Port:52860 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:35 Direction: Unknown In:eth0 Out: Port:41956 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:35 Direction: Unknown In:eth0 Out: Port:52857 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:36 Direction: Unknown In:eth0 Out: Port:52856 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:36 Direction: Unknown In:eth0 Out: Port:52857 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:36 Direction: Unknown In:eth0 Out: Port:52858 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:36 Direction: Unknown In:eth0 Out: Port:52859 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:36 Direction: Unknown In:eth0 Out: Port:52860 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:37 Direction: Unknown In:eth0 Out: Port:52840 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:37 Direction: Unknown In:eth0 Out: Port:52857 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:37 Direction: Unknown In:eth0 Out: Port:52859 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:37 Direction: Unknown In:eth0 Out: Port:52860 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:37 Direction: Unknown In:eth0 Out: Port:41953 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:38 Direction: Unknown In:eth0 Out: Port:52858 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:38 Direction: Unknown In:eth0 Out: Port:41955 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:38 Direction: Unknown In:eth0 Out: Port:41957 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:38 Direction: Unknown In:eth0 Out: Port:41956 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:39 Direction: Unknown In:eth0 Out: Port:41954 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:39 Direction: Unknown In:eth0 Out: Port:52837 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:39 Direction: Unknown In:eth0 Out: Port:52840 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:40 Direction: Unknown In:eth0 Out: Port:52839 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:40 Direction: Unknown In:eth0 Out: Port:52838 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:40 Direction: Unknown In:eth0 Out: Port:52856 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:40 Direction: Unknown In:eth0 Out: Port:52858 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:41 Direction: Unknown In:eth0 Out: Port:52859 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:41 Direction: Unknown In:eth0 Out: Port:52860 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:41 Direction: Unknown In:eth0 Out: Port:52857 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:41 Direction: Unknown In:eth0 Out: Port:52837 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:42 Direction: Unknown In:eth0 Out: Port:52856 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:42 Direction: Unknown In:eth0 Out: Port:52857 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:42 Direction: Unknown In:eth0 Out: Port:52858 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:42 Direction: Unknown In:eth0 Out: Port:52859 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:42 Direction: Unknown In:eth0 Out: Port:52860 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:43 Direction: Unknown In:eth0 Out: Port:52857 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:43 Direction: Unknown In:eth0 Out: Port:52859 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:43 Direction: Unknown In:eth0 Out: Port:52860 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:44 Direction: Unknown In:eth0 Out: Port:52858 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:44 Direction: Unknown In:eth0 Out: Port:52856 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:45 Direction: Unknown In:eth0 Out: Port:36777 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:45 Direction: Unknown In:eth0 Out: Port:52854 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:48 Direction: Unknown In:eth0 Out: Port:52838 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:49 Direction: Unknown In:eth0 Out: Port:52839 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:50 Direction: Unknown In:eth0 Out: Port:52856 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:53 Direction: Unknown In:eth0 Out: Port:52856 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:53 Direction: Unknown In:eth0 Out: Port:52858 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:53 Direction: Unknown In:eth0 Out: Port:52859 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:53 Direction: Unknown In:eth0 Out: Port:52860 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:53 Direction: Unknown In:eth0 Out: Port:52857 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:54 Direction: Unknown In:eth0 Out: Port:52856 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:54 Direction: Unknown In:eth0 Out: Port:52857 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:54 Direction: Unknown In:eth0 Out: Port:52858 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:54 Direction: Unknown In:eth0 Out: Port:52859 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:54 Direction: Unknown In:eth0 Out: Port:52860 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:55 Direction: Unknown In:eth0 Out: Port:52857 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:55 Direction: Unknown In:eth0 Out: Port:52860 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:55 Direction: Unknown In:eth0 Out: Port:52859 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:24:56 Direction: Unknown In:eth0 Out: Port:52858 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:01 Direction: Unknown In:eth0 Out: Port:52840 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:02 Direction: Unknown In:eth0 Out: Port:52856 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:09 Direction: Unknown In:eth0 Out: Port:52854 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:13 Direction: Unknown In:eth0 Out: Port:52805 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:16 Direction: Unknown In:eth0 Out: Port:52856 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:17 Direction: Unknown In:eth0 Out: Port:52858 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:17 Direction: Unknown In:eth0 Out: Port:52859 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:17 Direction: Unknown In:eth0 Out: Port:52860 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:17 Direction: Unknown In:eth0 Out: Port:52857 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:18 Direction: Unknown In:eth0 Out: Port:42609 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:18 Direction: Unknown In:eth0 Out: Port:52907 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:18 Direction: Unknown In:eth0 Out: Port:52908 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:18 Direction: Unknown In:eth0 Out: Port:52909 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:18 Direction: Unknown In:eth0 Out: Port:52910 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:19 Direction: Unknown In:eth0 Out: Port:52819 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:19 Direction: Unknown In:eth0 Out: Port:42609 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:19 Direction: Unknown In:eth0 Out: Port:52909 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:19 Direction: Unknown In:eth0 Out: Port:52820 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:19 Direction: Unknown In:eth0 Out: Port:52821 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:20 Direction: Unknown In:eth0 Out: Port:52860 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:20 Direction: Unknown In:eth0 Out: Port:52858 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:20 Direction: Unknown In:eth0 Out: Port:52907 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:21 Direction: Unknown In:eth0 Out: Port:52805 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:22 Direction: Unknown In:eth0 Out: Port:42609 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:22 Direction: Unknown In:eth0 Out: Port:52907 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:22 Direction: Unknown In:eth0 Out: Port:52908 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:22 Direction: Unknown In:eth0 Out: Port:52909 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:22 Direction: Unknown In:eth0 Out: Port:52910 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:22 Direction: Unknown In:eth0 Out: Port:52911 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:23 Direction: Unknown In:eth0 Out: Port:52907 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:23 Direction: Unknown In:eth0 Out: Port:42609 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:25 Direction: Unknown In:eth0 Out: Port:42609 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:25 Direction: Unknown In:eth0 Out: Port:52909 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:25 Direction: Unknown In:eth0 Out: Port:52910 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:25 Direction: Unknown In:eth0 Out: Port:52911 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:26 Direction: Unknown In:eth0 Out: Port:52908 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:26 Direction: Unknown In:eth0 Out: Port:52907 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:26 Direction: Unknown In:eth0 Out: Port:52856 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:27 Direction: Unknown In:eth0 Out: Port:42609 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:27 Direction: Unknown In:eth0 Out: Port:52837 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:27 Direction: Unknown In:eth0 Out: Port:52907 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:27 Direction: Unknown In:eth0 Out: Port:52840 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:27 Direction: Unknown In:eth0 Out: Port:52908 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:28 Direction: Unknown In:eth0 Out: Port:52839 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:28 Direction: Unknown In:eth0 Out: Port:52838 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:29 Direction: Unknown In:eth0 Out: Port:52907 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:29 Direction: Unknown In:eth0 Out: Port:42609 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:30 Direction: Unknown In:eth0 Out: Port:52837 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:36 Direction: Unknown In:eth0 Out: Port:52838 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:37 Direction: Unknown In:eth0 Out: Port:52839 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:37 Direction: Unknown In:eth0 Out: Port:52909 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:37 Direction: Unknown In:eth0 Out: Port:42609 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:37 Direction: Unknown In:eth0 Out: Port:52910 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:38 Direction: Unknown In:eth0 Out: Port:52911 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:38 Direction: Unknown In:eth0 Out: Port:52908 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:38 Direction: Unknown In:eth0 Out: Port:52907 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:40 Direction: Unknown In:eth0 Out: Port:42609 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:40 Direction: Unknown In:eth0 Out: Port:52907 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:40 Direction: Unknown In:eth0 Out: Port:52908 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:40 Direction: Unknown In:eth0 Out: Port:52909 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:40 Direction: Unknown In:eth0 Out: Port:52910 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:40 Direction: Unknown In:eth0 Out: Port:52911 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:41 Direction: Unknown In:eth0 Out: Port:42609 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:41 Direction: Unknown In:eth0 Out: Port:52907 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:46 Direction: Unknown In:eth0 Out: Port:42609 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:49 Direction: Unknown In:eth0 Out: Port:52840 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:58 Direction: Unknown In:eth0 Out: Port:52854 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:25:58 Direction: Unknown In:eth0 Out: Port:42609 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:01 Direction: Unknown In:eth0 Out: Port:42609 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:01 Direction: Unknown In:eth0 Out: Port:52909 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:01 Direction: Unknown In:eth0 Out: Port:52910 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:02 Direction: Unknown In:eth0 Out: Port:52911 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:02 Direction: Unknown In:eth0 Out: Port:52908 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:02 Direction: Unknown In:eth0 Out: Port:52907 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:04 Direction: Unknown In:eth0 Out: Port:52959 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:05 Direction: Unknown In:eth0 Out: Port:42609 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:05 Direction: Unknown In:eth0 Out: Port:52856 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:05 Direction: Unknown In:eth0 Out: Port:52907 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:05 Direction: Unknown In:eth0 Out: Port:52858 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:05 Direction: Unknown In:eth0 Out: Port:52959 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:05 Direction: Unknown In:eth0 Out: Port:52859 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:05 Direction: Unknown In:eth0 Out: Port:52860 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:05 Direction: Unknown In:eth0 Out: Port:52857 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:07 Direction: Unknown In:eth0 Out: Port:52959 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:07 Direction: Unknown In:eth0 Out: Port:52857 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:08 Direction: Unknown In:eth0 Out: Port:52859 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:08 Direction: Unknown In:eth0 Out: Port:52860 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:08 Direction: Unknown In:eth0 Out: Port:52858 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:11 Direction: Unknown In:eth0 Out: Port:52959 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:12 Direction: Unknown In:eth0 Out: Port:52959 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:14 Direction: Unknown In:eth0 Out: Port:52959 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:14 Direction: Unknown In:eth0 Out: Port:52856 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:20 Direction: Unknown In:eth0 Out: Port:52959 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:22 Direction: Unknown In:eth0 Out: Port:42609 Source:184.87.92.20 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:23 Direction: Unknown In:eth0 Out: Port:52959 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:25 Direction: Unknown In:eth0 Out: Port:52959 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov  4 09:26:32 Direction: Unknown In:eth0 Out: Port:52959 Source:184.87.83.172 Destination:192.168.1.102 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
```

---

### Post by Wayne1987 on 2010-11-04
[IMG]http://i172.photobucket.com/albums/w29/PunkORama87/Screenshot-2.png[/IMG]

---

### Post by efflandt on 2010-11-04
#    1. Movie/ Video Sound Issue.
[FONT=monospace]
[/FONT]AC97 Audio is fairly common and I have not had trouble with that unless it is something peculiar with the VIA implementation of it.  I'll check later what modules my computers use for AC97 (but I don't think they are VIA).

#    2. Reboot Screen, looks scrambled when shutting down or restarting.
#    3. Some software doesn't work, (Broken software sends me to main password login-screen)

It is easiest to install software using Synaptic or Software Center.  You sort of have to know what you are doing and follow directions if you get software from other sources.

#    4. Firewall, seems to be getting hit a-lot..

That traffic is from AKAMAI's web block which does all sorts of internet and web related things like load balancing web servers or finding the closest server to you, etc. [http://www.akamai.com/](http://www.akamai.com/)
```
NetRange:       184.84.0.0 - 184.87.255.255
CIDR:           184.84.0.0/14
OriginAS:       
NetName:        AKAMAI
```#    5. Can't scan computer for viruses because its not allowed.

With what program?  Viruses usually concentrate on Windows, so they are not usually an issue for Linux.

#    6. System Feels unstable when browsing the Internet, with the firewall on.

I am behind a router on a private IP, so I have not even tried ufw, since I don't have any ports forwarded by my router other than replies to outgoing traffic.  And the only ports my PC has listening for connections I did not initiate are sshd and cups:

**netstat -tl**
```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
tcp6       0      0 efflandt-XPS-8100:ipp   [::]:*                  LISTEN
```#    7. Can't ENCODE video file for dvd tried to but failed big time.

You copied and pasted too much at a time.  It looks like you may have already had a bin directory and moved varsha.jar there, but then you stumbled trying to chmod it by having other info attached to the path that did not belong there.

Do: **ls -l ~/bin**

And if that lists varsha.jar

Do: **chmod u+x ~/bin/varsha.jar**

Whether it works then depends whether you installed whatever else it needs from the varsha link in my previous reply.

---

### Post by sandyd on 2010-11-04
> **Wayne1987 said:**
> ---------------------- 
/Linux Ubuntu 10.10//
-----------------------

I'm trying to install a .jar file to make this encoding program work I guess, but I keep getting blocked.

The file '/home/wayne/Desktop/varsha.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit
Would anybody know of any software that would Encode any type of video format to a dvd/ dvd-dl ?
[ I can't find anything user friendly ]
--------
Adding 
--------
I'm also having trouble running WINE 1.3 or 1.2, what happens is I'll click on the program called wine then it'll log me off, so I must log back in with my password then try it again.  This problem also happens with Zsnes, so I dunno whats going on that could be going wrong.  

--------
One more add
--------
When I'm playing a movie with VLC or any media player the sound begins to become choppy really bad choppy, just wondering about that, music seems to play nicely but movies/ Videos don't.  


{Thanks}
sound.
```

gksudo gedit /etc/pulse/daemon.conf
```
find
```
 ;default-sample-rate = 44100

```
change to 
```

default-sample-rate = 48000

```
save.
run
```

pulseaudio -k
pulseaudio -D
```

---

### Post by Wayne1987 on 2010-11-04
```
Could not open the following files: /var/log/jockey.log.1: Error stating file '/var/log/jockey.log.1': No such file or directory
/var/log/syslog.1: Error stating file '/var/log/syslog.1': No such file or directory
```"Program: Wine" is still 100% not working, weird..

[Maybe this could help]

```
Nov  2 07:55:31 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1651]: pid.c: Daemon already running.
Nov  2 07:56:35 wayne-P8656S-ABA-S5000J-NA310 python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Nov  2 08:08:12 wayne-P8656S-ABA-S5000J-NA310 bonobo-activation-server (wayne-2196): could not associate with desktop session: Error connecting: Connection refused
Nov  2 08:08:40 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[2382]: pid.c: Stale PID file, overwriting.
Nov  2 08:08:41 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[2414]: pid.c: Daemon already running.
Nov  2 08:09:37 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[2382]: ratelimit.c: 3 events suppressed
Nov  2 08:14:13 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[2382]: ratelimit.c: 1 events suppressed
Nov  2 08:20:45 wayne-P8656S-ABA-S5000J-NA310 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Nov  2 08:20:45 wayne-P8656S-ABA-S5000J-NA310 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Nov  2 08:20:45 wayne-P8656S-ABA-S5000J-NA310 os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Nov  2 08:20:45 wayne-P8656S-ABA-S5000J-NA310 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Nov  2 08:20:45 wayne-P8656S-ABA-S5000J-NA310 50mounted-tests: debug: /dev/sda5 is a swap partition; skipping
Nov  2 08:20:45 wayne-P8656S-ABA-S5000J-NA310 os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Nov  2 08:23:37 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[14417]: pid.c: Stale PID file, overwriting.
Nov  2 08:23:37 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[14417]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-Sk0yuGZTjj: Connection refused
Nov  2 08:23:38 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[14513]: pid.c: Daemon already running.
Nov  2 08:24:05 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[16749]: pid.c: Daemon already running.
Nov  2 08:40:04 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1374]: pid.c: Daemon already running.
Nov  2 08:41:22 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1347]: ratelimit.c: 3 events suppressed
Nov  2 09:05:59 wayne-P8656S-ABA-S5000J-NA310 &#65279;<30>AptDaemon: INFO: InstallFile() was called: /home/wayne/Desktop/wayne/Downloads/nerolinux-3.5.3.1-x86.deb
Nov  2 09:06:12 wayne-P8656S-ABA-S5000J-NA310 &#65279;<30>AptDaemon.Worker: INFO: Installing local package file: /home/wayne/Desktop/wayne/Downloads/nerolinux-3.5.3.1-x86.deb
Nov  2 09:27:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1347]: ratelimit.c: 24 events suppressed
Nov  2 09:54:54 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1347]: ratelimit.c: 10 events suppressed
Nov  2 09:55:25 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1347]: ratelimit.c: 246 events suppressed
Nov  2 10:42:21 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1390]: pid.c: Daemon already running.
Nov  2 10:46:20 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1352]: ratelimit.c: 3 events suppressed
Nov  2 10:59:03 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1352]: ratelimit.c: 24 events suppressed
Nov  2 11:15:10 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1352]: ratelimit.c: 115 events suppressed
Nov  2 11:15:32 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1352]: ratelimit.c: 25 events suppressed
Nov  2 11:18:57 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1376]: pid.c: Daemon already running.
Nov  2 11:19:37 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1355]: ratelimit.c: 45 events suppressed
Nov  2 11:21:58 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1355]: sink-input.c: Assertion 'PA_SINK_INPUT_IS_LINKED(i->state)' failed at pulsecore/sink-input.c:1248, function pa_sink_input_finish_move(). Aborting.
Nov  2 11:21:58 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1690]: pid.c: Stale PID file, overwriting.
Nov  2 11:21:58 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1698]: pid.c: Daemon already running.
Nov  2 11:21:58 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1699]: pid.c: Daemon already running.
Nov  2 11:21:58 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1700]: pid.c: Daemon already running.
Nov  2 11:21:59 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1701]: pid.c: Daemon already running.
Nov  2 11:47:56 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1370]: pid.c: Daemon already running.
Nov  2 11:48:40 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1352]: ratelimit.c: 3 events suppressed
Nov  2 11:49:39 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1352]: ratelimit.c: 24 events suppressed
Nov  2 11:50:18 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1352]: ratelimit.c: 44 events suppressed
Nov  2 12:04:26 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1374]: pid.c: Daemon already running.
Nov  2 12:06:43 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1358]: ratelimit.c: 1288 events suppressed
Nov  2 12:43:16 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1358]: ratelimit.c: 967 events suppressed
Nov  2 12:45:59 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1358]: ratelimit.c: 91 events suppressed
Nov  2 12:55:12 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1358]: ratelimit.c: 188 events suppressed
Nov  2 12:56:12 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1358]: ratelimit.c: 188 events suppressed
Nov  2 12:56:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1358]: alsa-util.c: Got POLLNVAL from ALSA
Nov  2 12:56:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1358]: alsa-util.c: Could not recover from POLLERR|POLLNVAL|POLLHUP with snd_pcm_prepare(): No such device
Nov  2 13:15:11 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1303]: alsa-util.c: Could not recover from POLLERR|POLLNVAL|POLLHUP and XRUN: Broken pipe
Nov  2 13:15:14 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1303]: ratelimit.c: 33 events suppressed
Nov  2 13:15:38 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1303]: ratelimit.c: 29 events suppressed
Nov  2 16:00:26 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[10177]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  2 16:00:26 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[10180]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  2 16:00:26 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[10179]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  2 16:00:26 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[10178]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  2 16:00:27 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[10196]: pid.c: Stale PID file, overwriting.
Nov  2 16:00:27 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[10198]: pid.c: Daemon already running.
Nov  2 16:00:27 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[10200]: pid.c: Daemon already running.
Nov  2 16:00:27 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[10196]: server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-FlRWZhqFHF: Connection refused
Nov  2 16:00:27 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[10202]: server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-FlRWZhqFHF: Connection refused
Nov  2 16:00:54 wayne-P8656S-ABA-S5000J-NA310 bonobo-activation-server (wayne-10545): could not associate with desktop session: Error connecting: Connection refused
Nov  2 16:01:05 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[10703]: pid.c: Stale PID file, overwriting.
Nov  2 16:12:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1641]: pid.c: Daemon already running.
Nov  2 22:05:54 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[26573]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  2 22:05:54 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[26575]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  2 22:05:55 wayne-P8656S-ABA-S5000J-NA310 bonobo-activation-server (wayne-26577): could not associate with desktop session: Error connecting: Connection refused
Nov  2 22:05:55 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[26591]: pid.c: Stale PID file, overwriting.
Nov  2 22:05:55 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[26593]: pid.c: Daemon already running.
Nov  2 22:05:55 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[26591]: server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-9m7cXYiBPb: Connection refused
Nov  2 23:24:49 wayne-P8656S-ABA-S5000J-NA310 &#65279;<30>AptDaemon: INFO: InstallFile() was called: /home/wayne/Desktop/wayne/Downloads/avast4workstation_1.3.0-2_i386.deb
Nov  2 23:25:01 wayne-P8656S-ABA-S5000J-NA310 &#65279;<30>AptDaemon.Worker: INFO: Installing local package file: /home/wayne/Desktop/wayne/Downloads/avast4workstation_1.3.0-2_i386.deb
Nov  3 00:31:56 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[8492]: pid.c: Stale PID file, overwriting.
Nov  3 00:31:57 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[8508]: pid.c: Daemon already running.
Nov  3 12:04:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[2082]: pid.c: Daemon already running.
Nov  3 16:55:21 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1779]: pid.c: Daemon already running.
Nov  4 00:21:15 wayne-P8656S-ABA-S5000J-NA310 python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Nov  4 00:25:33 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1765]: ratelimit.c: 69 events suppressed
Nov  4 00:28:00 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[1765]: ratelimit.c: 18 events suppressed
Nov  4 03:59:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[14676]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  4 03:59:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[14675]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  4 03:59:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[14677]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  4 03:59:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[14684]: pid.c: Stale PID file, overwriting.
Nov  4 03:59:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[14686]: pid.c: Daemon already running.
Nov  4 03:59:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[14688]: pid.c: Daemon already running.
Nov  4 03:59:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[14684]: server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-zyF9j6H680: Connection refused
Nov  4 04:00:26 wayne-P8656S-ABA-S5000J-NA310 bonobo-activation-server (wayne-14946): could not associate with desktop session: Error connecting: Connection refused
Nov  4 04:00:36 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[15114]: pid.c: Stale PID file, overwriting.
Nov  4 04:09:55 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[15114]: ratelimit.c: 1 events suppressed
Nov  4 04:18:49 wayne-P8656S-ABA-S5000J-NA310 computerjanitord: INFO: cleaning cruft[Y]: deb:avast4workstation
Nov  4 04:18:50 wayne-P8656S-ABA-S5000J-NA310 computerjanitord: INFO: post-cleanup: <autoremoval_plugin.AutoRemovablePlugin object at 0x8585a2c>
Nov  4 04:18:50 wayne-P8656S-ABA-S5000J-NA310 computerjanitord: INFO: post-cleanup: <dpkg_dotfile_plugin.DpkgDotfilePlugin object at 0x858b34c>
Nov  4 04:18:50 wayne-P8656S-ABA-S5000J-NA310 computerjanitord: INFO: post-cleanup: <unsupported_plugin.UnsupportedPackagesPlugin object at 0x858b4cc>
Nov  4 04:18:50 wayne-P8656S-ABA-S5000J-NA310 computerjanitord: INFO: post-cleanup: <deb_plugin.DebPlugin object at 0x858b6ac>
Nov  4 04:35:21 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[21417]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  4 04:35:21 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[21421]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  4 04:35:21 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[21420]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  4 04:35:22 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[21433]: pid.c: Stale PID file, overwriting.
Nov  4 04:35:22 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[21438]: pid.c: Daemon already running.
Nov  4 04:35:22 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[21441]: pid.c: Daemon already running.
Nov  4 04:35:23 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[21433]: server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-EYcFeJNdoD: Connection refused
Nov  4 04:59:25 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[22395]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  4 04:59:25 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[22398]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  4 04:59:25 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[22404]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  4 04:59:25 wayne-P8656S-ABA-S5000J-NA310 bonobo-activation-server (wayne-22400): could not associate with desktop session: Error connecting: Connection refused
Nov  4 04:59:26 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[22414]: pid.c: Stale PID file, overwriting.
Nov  4 04:59:26 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[22417]: pid.c: Daemon already running.
Nov  4 04:59:27 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[22421]: pid.c: Daemon already running.
Nov  4 04:59:27 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[22414]: server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-7xxNeJnFA0: Connection refused
Nov  4 04:59:52 wayne-P8656S-ABA-S5000J-NA310 bonobo-activation-server (wayne-22700): could not associate with desktop session: Error connecting: Connection refused
Nov  4 05:00:02 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[22860]: pid.c: Stale PID file, overwriting.
Nov  4 05:06:37 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[23076]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  4 05:06:37 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[23080]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  4 05:06:37 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[23086]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  4 05:06:39 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[23092]: pid.c: Stale PID file, overwriting.
Nov  4 05:06:39 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[23098]: pid.c: Daemon already running.
Nov  4 05:06:39 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[23101]: pid.c: Daemon already running.
Nov  4 05:06:39 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[23092]: server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-CPA1sZtxqe: Connection refused
Nov  4 05:30:21 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[23250]: ratelimit.c: 308 events suppressed
Nov  4 05:30:27 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[23250]: ratelimit.c: 306 events suppressed
Nov  4 05:32:32 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[23250]: ratelimit.c: 20 events suppressed
Nov  4 12:25:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[2938]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  4 12:25:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[2937]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  4 12:25:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[2942]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  4 12:25:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[2943]: client-conf-x11.c: xcb_connection_has_error() returned true
Nov  4 12:25:45 wayne-P8656S-ABA-S5000J-NA310 bonobo-activation-server (wayne-2941): could not associate with desktop session: Error connecting: Connection refused
Nov  4 12:25:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[2957]: pid.c: Stale PID file, overwriting.
Nov  4 12:25:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[2960]: pid.c: Daemon already running.
Nov  4 12:25:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[2965]: pid.c: Daemon already running.
Nov  4 12:25:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[2967]: pid.c: Daemon already running.
Nov  4 12:25:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[2957]: server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-3E4GwDxbKO: Connection refused
Nov  4 12:34:13 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[3646]: pid.c: Stale PID file, overwriting.
Nov  4 13:25:09 wayne-P8656S-ABA-S5000J-NA310 bonobo-activation-server (wayne-3350): could not associate with desktop session: Error connecting: Connection refused
Nov  4 13:25:29 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[3518]: pid.c: Stale PID file, overwriting.
Nov  4 14:37:30 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4287]: pid.c: Stale PID file, overwriting.
Nov  4 14:51:43 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4701]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:43 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4700]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:43 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4702]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:43 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4703]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:43 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4704]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:43 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4705]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:43 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4707]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:43 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4706]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:43 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4708]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:43 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4709]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4710]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4711]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4712]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4713]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4714]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4715]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4716]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4718]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4717]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4719]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4720]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4721]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4722]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4723]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4724]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4725]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4726]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4727]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4728]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4729]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4730]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:44 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4731]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4732]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4734]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4733]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4735]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4736]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4742]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4741]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4740]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4739]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4738]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4737]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4748]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4747]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4745]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4746]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4744]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:45 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4743]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4749]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4750]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4751]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4754]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4753]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4752]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4756]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4755]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4757]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4758]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4759]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4761]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4762]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4763]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4760]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4765]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4764]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4766]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4767]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4768]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4770]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:46 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4769]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4771]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4772]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4773]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4774]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4775]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4776]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4778]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4779]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4777]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4780]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4781]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4782]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4784]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4783]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4785]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4786]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4788]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4787]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4789]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4791]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4790]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4792]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4793]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:47 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4794]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4795]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4797]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4796]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4798]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4799]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4800]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4801]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4802]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4803]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4805]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4804]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4806]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4808]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4807]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4810]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4809]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4812]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4811]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4813]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4814]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4815]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4816]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4817]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4818]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:48 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4819]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4821]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4820]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4824]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4823]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4822]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4825]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4827]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4826]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4828]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4829]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4830]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4831]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4832]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4833]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4834]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4836]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4835]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4837]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4838]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:49 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4839]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4840]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4842]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4841]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4843]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4844]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4845]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4846]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4847]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4848]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4849]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4850]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4851]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4852]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4854]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4853]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4855]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4856]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4858]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4857]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4859]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4860]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4861]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:50 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4862]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4863]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4864]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4865]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4866]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4867]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4868]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4869]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4870]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4871]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4872]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4873]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4874]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4875]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4878]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4876]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4877]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4879]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4880]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4881]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4884]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4882]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4883]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4885]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4886]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:51 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4888]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4887]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4889]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4890]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4891]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4892]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4893]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4895]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4894]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4896]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4897]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4899]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4898]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4901]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4900]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4902]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4903]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4904]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4905]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4906]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4907]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4908]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4909]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:52 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4910]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:53 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4912]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:53 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4911]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:53 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4913]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:53 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4914]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:53 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4915]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:53 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4916]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:53 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4917]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:53 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4918]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:53 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4919]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.
Nov  4 14:51:53 wayne-P8656S-ABA-S5000J-NA310 pulseaudio[4920]: main.c: User-configured server at {3353e113f90cbbaee2f4d5cf00000008}unix:/home/wayne/.pulse/3353e113f90cbbaee2f4d5cf00000008-runtime/native, not autospawning.

```
I need a program that scans for system errors and makes logs of the whole system, without making it into a book..

{thanks guys}

:EDIT:
_____
If I could get wine working, I could use CovertXtoDvd for my video Encoding......

---

### Post by gordintoronto on 2010-11-04
For making a DVD, I suggest devede. It will take a long time to run. (You still haven't told us about your processor or memory, but I'm guessing your computer was made in 2003 or 2004. S3 graphics are less than wonderful.)

---

### Post by Wayne1987 on 2010-11-05
Memory total: 1996 MiB

CPU:1- V: AuthenticAMD- M. D: AMD Athlon(tm) XP 2600+
F: 2131.747 MHz 
L2 Cache: 256 KB

---

