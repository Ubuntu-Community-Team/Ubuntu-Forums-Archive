---
title: "Setting up wireless"
date: 2010-07-31
forum: General Help
---

### Post by a sandwhich on 2010-07-31
I just installed ubuntu on my hp desktop that has wireless built in. I finally found the windows inf and sys driver files, and learned how to get ndiswrapper without internet and installed the driver. It says that i have the hardware it controls, but when I look at the connection icon, it says not connected, has lost the wireless connection block, and I am not connected to the internet. The wireless is called USB Wireless 802.11 b/g , but it is not usb and is plugged straight into the motherboard with the only physical part is the antenna. Why can't I connect?

---

### Post by mike555 on 2010-07-31
you need to find out what card you have , then post here ... there probably is a linux driver for it ...

---

### Post by bobcollard on 2010-07-31
Open Terminal and put this command in to see your networking card then copy the contents to this thread so we can help you.
  	 	 	 	 	 	  ```
lspci
```

---

### Post by Bladeforger on 2010-07-31
> **a sandwhich said:**
> I just installed ubuntu on my hp desktop that has wireless built in. I finally found the windows inf and sys driver files, and learned how to get ndiswrapper without internet and installed the driver. It says that i have the hardware it controls, but when I look at the connection icon, it says not connected, has lost the wireless connection block, and I am not connected to the internet. The wireless is called USB Wireless 802.11 b/g , but it is not usb and is plugged straight into the motherboard with the only physical part is the antenna. Why can't I connect?
Try going to Synaptic Package Manager and search for wicd.  It's not compatible with the Gnome Network Manager and will ask to uninstall it.  That's okay.  The install process will flag your user name and ask if you can be added to make changes via wicd.  You decide.  Then, when it's executed, it really goes out and finds the wireless network.  You can select the security and set the password and go.  

I spent hours trying to get the network manager to work and cruising various forum threads.  

wicd works great.  You'll like it.  If not, you can always go back and uninstall it and install the network manager... I'll bet you won't want to!

Keith

---

### Post by a sandwhich on 2010-08-01
output:
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
02:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 9400 GT] (rev a1)



Like i said earlier, microsoft calls it USB Wireless 802.11 b/g adapter. That is the name. There are hp drivers for it, and ralink drivers. The ralink don't work, and neither do the hp. The only that work are the ones on my windows drive. When booted up ubuntu after I uninstalled the nonworking windows drivers and before I installed the correct ones, it said a program was causing too much trouble and asked if i wanted to delete it. It also has taken away the option two connect two a wireless network or even display connected networks in the wireless dropdown menu.

---

### Post by bobcollard on 2010-08-01
Try this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by a sandwhich on 2010-08-01
I tried going through those directions and it didnt work. Now it isnt even detecting the card. I have wireless acess in windows though.

---

### Post by gordintoronto on 2010-08-01
> **a sandwhich said:**
> The wireless is called USB Wireless 802.11 b/g , but it is not usb and is plugged straight into the motherboard with the only physical part is the antenna. Why can't I connect?

"the only physical part is the antenna"????

It doesn't show up in lspci. If it plugged into the motherboard, it would show up in lspci.

---

### Post by gordintoronto on 2010-08-01
> **a sandwhich said:**
> I tried going through those directions and it didnt work. Now it isnt even detecting the card. I have wireless acess in windows though.

"It didn't work" What happened?

---

### Post by a sandwhich on 2010-08-01
When I went through the installation process it didn't detect the thing, and when I did the final command, it returned 17 errors. On the little dropdown networking tool it says nothing about wireless anymore. as for the physical shape of it, I attached a picture. The line in the middle is the back plate on my case.

---

### Post by bobcollard on 2010-08-01
Did you save or copy down any of the error messages?  Could you find them in your Logs?

---

### Post by a sandwhich on 2010-08-02
kevin@kevin-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
oem45 : driver installed
	device (15A9:0004) present (alternate driver: rt73usb)
kevin@kevin-desktop:~$ sudo depmod -a
[sudo] password for kevin: 
sudo modprkevin@kevin-desktop:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
kevin@kevin-desktop:~$ tail /var/log/messages
Aug  2 11:48:56 kevin-desktop kernel: [   27.682784] composite sync not supported
Aug  2 11:48:56 kevin-desktop kernel: [   27.884773] composite sync not supported
Aug  2 11:48:56 kevin-desktop kernel: [   28.086968] composite sync not supported
Aug  2 11:48:56 kevin-desktop kernel: [   28.289978] composite sync not supported
Aug  2 11:48:57 kevin-desktop kernel: [   28.492211] composite sync not supported
Aug  2 11:48:57 kevin-desktop kernel: [   28.751169] composite sync not supported
Aug  2 11:48:58 kevin-desktop kernel: [   29.813040] composite sync not supported
Aug  2 11:48:59 kevin-desktop kernel: [   31.151755] composite sync not supported
Aug  2 11:49:02 kevin-desktop kernel: [   33.977831] composite sync not supported
Aug  2 11:49:02 kevin-desktop kernel: [   34.180674] composite sync not supported
kevin@kevin-desktop:~$ 

Those were the error messages. This time when I booted ubuntu there were some messages during teh boot before the loggin screen that said something about ndiswrapper but they went by so quickly that  I couldn't read them.

---

### Post by bobcollard on 2010-08-02
I'm not a programmer, but, it looks like you have two drivers installed and a conflct between them, ndiswrapper and modprobe.  oem45 was the original equipment driver and you added rt73usb?

---

### Post by a sandwhich on 2010-08-02
No. rt73usb is the sys file and oem45 inf file. ndiswrapper requires the inf file to install the driver. In the gui it asks for an inf file and it installs both the sys and inf.

---

### Post by bobcollard on 2010-08-02
> **a sandwhich said:**
> No. rt73usb is the sys file and oem45 inf file. ndiswrapper requires the inf file to install the driver. In the gui it asks for an inf file and it installs both the sys and inf.
Sorry, I cannot help beyond this point, perhaps someone with experience with these drivers?

---

### Post by a sandwhich on 2010-08-02
I'm thinking about just getting a new legitimate wireless n card. I'm thinking about the dlink dwa-552. I've read the experience and info about it on the supported cards list, and the guy said that it sometimes stops in 64 bit. But that was two releases ago. I'm using lucid lynx now, will this be solved or work better?

---

### Post by gordintoronto on 2010-08-02
I'm betting the plug on the motherboard is an USB header.

If you enter the terminal command:
lsusb
it should show up. Sometimes USB devices only display a code, sometimes they fully identify themselves.

---

### Post by a sandwhich on 2010-08-02
I typed that also, nothing showed up that I hadn't already matched to a different item.

---

### Post by bobcollard on 2010-08-02
Perhaps, but it did show my dongle.
 lsusb
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 03f0:7004 Hewlett-Packard DeskJet 3320c
Bus 002 Device 005: ID 0bc2:3000 Seagate RSS LLC 
[COLOR=Red]Bus 002 Device 004: ID 0846:4260 NetGear, Inc. WG111v3 54 Mbps Wireless [realtek RTL8187B][/COLOR]
Bus 002 Device 002: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by a sandwhich on 2010-08-02
If I were to get a new card would I install it on windows and do nothing on ubuntu and expect it to use it or what would i do?

---

### Post by gordintoronto on 2010-08-04
With a supported card, on my system, I can select Preferences/Network Connections, click the Wireless tab, then click "add," enter my router's SSID, then select "wireless security," where I select the encryption type and enter the password. Click the "all users" box, then OK. All done.

---

