---
title: "Search or pci"
date: 2010-12-13
forum: General Help
---

### Post by David52 on 2010-12-13
I have been into this ubuntu for 4 months now but never really played with it. I am looking to find out how can you make the system in ubuntu 10.10 to find a installed pci tuner card on my mother board?

---

### Post by Verbeck on 2010-12-13
from a terminal, enter *lspci*

---

### Post by David52 on 2010-12-13
following your guidelines here is what I get
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f1)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f3)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
01:09.0 Multimedia controller: Auvitek AU85X1 PCI REV1.1 (rev 01)
david@ubuntu:~$ 


It is not showing the tv turner card I don't believe. Can you tell me how to or guide me to a link that will instruct they system to find this pci tv tuner card?
tks.
david52

---

### Post by tredegar on 2010-12-13
> 01:09.0 Multimedia controller: Auvitek AU85X1 PCI REV1.1 (rev 01)
Is your TV card.
AFAIK there is no linux support for it.

---

### Post by David52 on 2010-12-13
well, that part I do not think so. Looking at it you might like I did but per the box and the software it is a ATSC HDTV and it uses the blaze tv software when booted into windows xp.

---

### Post by tredegar on 2010-12-13
> well, that part I do not think so.
I think you are mistaken. See [here]("https://answers.launchpad.net/ubuntu/+source/tvtime/+question/91422")

But now you have told us a little more about your device ("per the box") I can search better.

So now see [here]("http://linuxtv.org/wiki/index.php/ATSC_PCI_Cards")

---

### Post by David52 on 2010-12-13
thats why I came to the forum for help. This is my 1st day trying to figure this one out. If you can find something please let me know will ya
david

---

