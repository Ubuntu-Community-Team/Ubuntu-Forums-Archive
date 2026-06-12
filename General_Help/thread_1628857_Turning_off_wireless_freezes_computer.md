---
title: "Turning off wireless freezes computer"
date: 2010-11-23
forum: General Help
---

### Post by timgood on 2010-11-23
I have an Acer Aspire Revo 3700 on which I have installed Maverick 32 bit. The problem is that when wireless is disabled the computer will freeze, mouse dies, can't switch to virtual terminal, have to do a hard reset. So when I select 'shut down' the same thing happens - as soon as the wireless is disabled the computer freezes and I can't shut down. The last message I'm getting is something to do with r2800 pci. I have tried to re-install, but the same thing happens after installation is complete - I select restart and the computer freezes. Have to hard reset. Any ideas? I can't seem to disable wireless either...

EDIT: Just tried Mint as well, same problem. As soon as wireless is un-enabled, system freezes. Will also try Fedora.

---

### Post by timgood on 2010-11-23
Hmm, interesting. Installing the 64bit version of Meerkat seems to solve this problem...

EDIT: Except it doesn't as the wireless does not work at all in 64bit...

---

### Post by timgood on 2010-11-23
Output of lspci -v | less:

Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
        Subsystem: Lite-On Communications Inc Device 6622
        Physical Slot: 34
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt2800pci
        Kernel modules: rt3090sta, rt2860sta, rt2800pci

So would I need to blacklist all three modules to disable wireless? If I remove them from the blacklist will they work again? Are there any other drivers for the RT3090 that might help?

---

### Post by timgood on 2010-11-23
Finally fixed it by following the instructions [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/103")

```
echo blacklist rt2800pci | sudo tee -a /etc/modprobe.d/blacklist.conf
```

seems to be the bit that does the magic. Now I can shut down without freezing!

---

