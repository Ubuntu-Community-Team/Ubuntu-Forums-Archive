---
title: "Window freeze for 30-60 seconds - making me switch away from Ubuntu"
date: 2012-03-29
forum: General Help
---

### Post by peterlauri on 2012-03-29
My computer (Samsung 9 Series 900X3A-A04) freeze from time to time, but get back to good state after some time (30-60 seconds). Using Unity2D all works fine, no freeze. I was thinking I have driver problems, but why would it then work in Unity2D? This happens in any application, and often when I perform "quick tasks" like switching between application or dragging/dropping things etc. I was monitoring "dmesg" and there were no additional logs coming there from before a freeze and after a freeze. Full dmesg is attached.

I don't know where to go from now, and I want to use Unity but this keeps me away from it.

Anyone with same problem that were able to fix it?

```

plauri@pjotr-ubuntu:~$ uname -a
Linux pjotr-ubuntu 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

```
plauri@pjotr-ubuntu:~$ lspci 
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230 (rev 34)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
```

---

### Post by Mark Phelps on 2012-03-29
> I was thinking I have driver problems, but why would it then work in Unity2D? 

Because ... Unity 2D places less demands on the graphics processor than does Unity 3D.

If your Intel graphics processor isn't up to the demands of Unity 3D, other than selecting 2D, there's nothing much you can do about it.

---

### Post by dcstar on 2012-03-30
> **peterlauri said:**
> My computer (Samsung 9 Series 900X3A-A04) freeze from time to time, but get back to good state after some time (30-60 seconds). Using Unity2D all works fine, no freeze. I was thinking I have driver problems, but why would it then work in Unity2D? This happens in any application, and often when I perform "quick tasks" like switching between application or dragging/dropping things etc. I was monitoring "dmesg" and there were no additional logs coming there from before a freeze and after a freeze. Full dmesg is attached.

I don't know where to go from now, and I want to use Unity but this keeps me away from it.
..........


Do a full SMART surface test on your hard drive as it is quite possible that you have bad blocks that are only hit when using the Unity 3D environment.

---

