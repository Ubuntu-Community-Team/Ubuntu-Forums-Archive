---
title: "Windows go blank when resized"
date: 2011-07-09
forum: General Help
---

### Post by snakedya on 2011-07-09
I just installed Ubuntu 11.04 on my HP Pavilion dv6500 laptop (originally came with windows vista but had a bootlegged Windows 7 on it). I can view most windows fine, but when i go to make them bigger the window goes blank. It doesn't seem to matter how long I wait, they just stay blank until I resize them smaller. This means I can't fullscreen Flash games or Youtube videos. I can get Firefox bigger a little at a time, but past a certain point it goes blank again. I tried a few things with the graphic interface but don't really know how to go to fallback mode or a previous, less graphic/processor intense way to show the windows. Thank you.

---

### Post by spiky001 on 2011-07-09
You might want to post more details of laptop specs and the output of lspci

---

### Post by snakedya on 2011-07-09
typed lspci in terminal and here's the output 
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

adam@adam-HP-Pavilion-dv6500-Notebook-PC:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
adam@adam-HP-Pavilion-dv6500-Notebook-PC:~$

---

### Post by spiky001 on 2011-07-09
Have you tried updating the system since you have installed and have you tried updating the drivers

---

### Post by snakedya on 2011-07-09
I made the LiveCD and installed it with network connectivity and updated the drivers all this morning so they are the latest ones available. It's not the fastest computer ever but it didn't have this problem with windows 7 or even the "try ubuntu" off the Live CD. I can make a firefox window bigger little by little but then it blanks and even if I leave it along for a half hour or so it stays blank until I resize the window smaller.

---

### Post by ajgreeny on 2011-07-09
Are you using unity desktop?

If so, just as an experiment, login to a **classic-ubuntu** desktop from the login screen session menu to see if the problem disappears.  If the problem persists, try the command ```
metacity --replace
```in a "run" command box from Alt+F2.  That will stop compiz and use metacity instead as window manager, though I would have not expected your nvidia card to show that problem with running compiz.

---

### Post by snakedya on 2011-07-09
Logging in with Ubuntu Classic (no effects) fixed the problem and I can watch high def videos in youtube in full screen. Thanks for the help guys!

---

### Post by ajgreeny on 2011-07-09
> **snakedya said:**
> Logging in with Ubuntu Classic (no effects) fixed the problem and I can watch high def videos in youtube in full screen. Thanks for the help guys!
Great!

I forgot about the Ubuntu-classic (without effects) in the session menu.  I am not using 11.04 as you can see from my userCP; still on 10.04, the best!

---

