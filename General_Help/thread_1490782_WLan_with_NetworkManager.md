---
title: "WLan with NetworkManager"
date: 2010-05-22
forum: General Help
---

### Post by HKei on 2010-05-22
(Ubuntu 10.4 lts)

Hi!

I am new to Ubuntu, and spend the entire afternoon (and a pretty large part of the night) setting up ubuntu. Or rather, setting up Ubuntu itself wasn't so much of a problem as getting my Internet to work was. My Network shows up in NetworkManager, so I suppose my WLan Adapter (WG111v2) was recognized. All my attempts to connect to my home network however failed until now. I can't connect to my Network with either WEP or WPA Personal, the first one doesn't work because (at least I assume that's the cause) my Router uses 64 Bit keys, NetworkManager however keeps asking me for a 128 Bit passphrase for WEP. If I try to use WPA (which I would prefer anyways) I can't select WPA as an option from the dropdown menu of when NetworkManager prompts me to enter a key. However, I can select WPA if I set up a new Network in NetworkManager, however NM seems to refuse to use those settings. I can guarantee that my card supports WPA because I used it earlier when I still had WinXP. I am, to say the least, completely clueless regarding what to do to solve this issue, and appreciate any help (and any attempt to help). Thanks in advance (and for reading).

PS: I've been reading quite a few articles online today, and nothing I found really helped me, so bear with me if this gets complicated. Though I'm all for simple solutions, so if you got a one-line shell command that fixes this that would be cool too :O

---

### Post by Guitar John on 2010-05-22
What is the output of this command?

```
lspci -v | less
```

---

### Post by HKei on 2010-05-22
it says > 00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
        Subsystem: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: d2f00000-d7ffffff
        Prefetchable memory behind bridge: d8000000-dfffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: ASUSTeK Computer Inc. Device 814e
        Flags: bus master, fast devsel, latency 0, IRQ 16



thanks for the fast reply

---

