---
title: "Slow boot with ATI Radeon HD  5570 proprietary drivers"
date: 2012-06-18
forum: General Help
---

### Post by JRBASTIEN on 2012-06-18
Hi,

I'm running 12.04 64 bits, with an ATI Radeon HD 5570.

No matter what version of the Catalyst driver I try, I always get an additional 45 seconds of boot time where nothing happens.

I have tried the version offered by the Additional Driver program (8.x), then the updated version (8.96) and then 12.4 downloaded directly from AMD.  All of them have this delay problem.

When I remove the proprietary driver, the delay is gone. 

fglrxinfo gives me:

```
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 5570
OpenGL version string: 4.2.11627 Compatibility Profile Context
```

dmesg gives me:

...
```
    15.666259] Bluetooth: RFCOMM ver 1.11
[   17.790001] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   18.125155] r8169 0000:03:00.0: eth4: link down
[   18.125162] r8169 0000:03:00.0: eth4: link down
[   18.126008] ADDRCONF(NETDEV_UP): eth4: link is not ready
[   18.126295] ADDRCONF(NETDEV_UP): eth4: link is not ready
[   19.863439] r8169 0000:03:00.0: eth4: link up
[   19.864268] ADDRCONF(NETDEV_CHANGE): eth4: link becomes ready
[   30.672019] eth4: no IPv6 routers present
[   31.472176] CIFS: Unknown mount option codepage
[   31.472179] CIFS: Unknown mount option unicode
[   31.472683] CIFS VFS: default security mechanism requested.  The default security mechanism will be upgraded from ntlm to ntlmv2 in kernel release 3.3
[   75.054719] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   75.054721] vesafb: scrolling: redraw
[   75.054724] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   75.059756] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90011d80000, using 5120k, total 5120k
[   75.059935] Console: switching to colour frame buffer device 160x64
[   75.059957] fb0: VESA VGA frame buffer device
[   75.078739] init: plymouth-splash main process (1471) terminated with status 1
[   75.950051] fglrx_pci 0000:01:00.0: irq 45 for MSI/MSI-X
[   75.950841] [fglrx] Firegl kernel thread PID: 1485
[   75.950910] [fglrx] Firegl kernel thread PID: 1486
[   75.950979] [fglrx] Firegl kernel thread PID: 1487
[   75.951078] [fglrx] IRQ 45 Enabled
[   76.053714] [fglrx] Gart USWC size:1280 M.
[   76.053717] [fglrx] Gart cacheable size:508 M.
[   76.053721] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   76.053723] [fglrx] Reserved FB block: Unshared offset:f8fd000, size:403000 
[   76.053725] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[   84.420207] 2:3:1: cannot get freq at ep 0x82
[   86.028102] 2:3:1: cannot get freq at ep 0x82


```

We can see clearly the delay between 31.472683 and 75.054719.

I have also attached a bootchart but I have to admit that I don't know how to interpret it.  

Anyone knows what is going on?  I don't remember my computer being that slow to boot on Maverick.

---

### Post by JRBASTIEN on 2012-06-19
Bump! Is there other fglrx users having this problem or I'm the only one?

---

### Post by JRBASTIEN on 2012-10-29
OK, after a couple of months without using the proprietary drivers I decided to give it a try again and I have installed 12.10.  The boot time is still horrible.

Can someone help me to troubleshoot this issue please?

---

### Post by Mark Phelps on 2012-10-29
You should go over to the Phoronix forums and read through their recent threads on the problems with AMD drivers.  I believe the latest beta (12.11?) fixes many of these.

---

### Post by JRBASTIEN on 2012-10-29
Thanks for the suggestion.  However there is very little hope by reading the comment on Phoronix:

*"As usual, there is no official release notes from AMD for this updated Linux Catalyst driver. However, for the information I happen to know about this new binary blob... There should be some 2D performance optimizations, Red Hat Enterprise Linux 6.3 support, and some other random work, but nothing too breakthrough."*

On the forum, I found a thread ([http://phoronix.com/forums/showthread.php?17450-Slow-xorg-start-with-fglrx-8-seconds-to-launch&highlight=boot+time](http://phoronix.com/forums/showthread.php?17450-Slow-xorg-start-with-fglrx-8-seconds-to-launch&highlight=boot+time)) were someone was complaining about a 8 second delay before Xorg has been launched.  My delay is much worse.  I have a 45 seconds delay.

In this thread, someone mentioned also disabling xrandr in the fglrx driver.  How can I do this?  Should I?

---

