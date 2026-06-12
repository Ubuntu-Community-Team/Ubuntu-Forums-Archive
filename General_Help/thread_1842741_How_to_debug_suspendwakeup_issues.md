---
title: "How to debug suspend/wakeup issues ?"
date: 2011-09-12
forum: General Help
---

### Post by vsespb on 2011-09-12
I have ubuntu 10.04 with kernel 2.6.38, motherboard - Intel DP67BG.

When I suspend machine it hang with probability ~ 30%
Even in case of success, sometimes it does not wake up.

The question is - I dont see any  logging info in syslog.
And pm-suspend.log consist of just of list of modules loaded etc.

I want to findout what is actually happening. How to do it ?
How do  I set up proper logging ? (i.e. log _every_ operation which happened when running into suspend)

---

### Post by Toz on 2011-09-13
To debug kernel suspend at its lowest level, you should follow the procedures listed here: [https://wiki.ubuntu.com/DebuggingKernelSuspend]("https://wiki.ubuntu.com/DebuggingKernelSuspend"). Make note of the changes made to your RTC clock and the effects this will have on your files system (see the "Caveat Emptor" note).

I'd be really interested in what you find using this procedure. Please post back your findings.

---

### Post by vsespb on 2011-09-14
ok, thanks! That's exactly what I need. I ll try within a few days.

---

### Post by vsespb on 2011-09-27
the computer was sleeping and waking up without problems during a week.
but finally It hanged again during wakeup.

i've got
 Magic number: 0:540:492
 hash matches /build/buildd/linux-lts-backport-natty-2.6.38/drivers/base/power/main.c:535
 pci 0000:06:00.0: hash matches

lspci gives me

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

this is a r8168 controller for which I downloaded and compiled driver named "r8169" from a Realtek site (r8168 driver for it is know as buggy).

yep, this is probably a main reason.

btw system clock was fine. weird.

---

### Post by Toz on 2011-09-27
Thanks for posting back you're findings. Interesting stuff indeed. 

You can now try editing (or creating if it doesn't exist) the file **/etc/pm/config.d/defaults** with the following content:
```
SUSPEND_MODULES="r8169"
```
The "r8169" should be the module name. You can confirm by running:
```
lsmod
```

This will unload the module prior to suspend and reload upon resume.

---

### Post by vsespb on 2011-09-28
ok. thanks.
but
i've read several times that all network drivers are unloaded by default, so no need to include it into suspend_modules...

---

### Post by vsespb on 2011-11-02
now this solution suddenly stopped working. when computer wakes up internet connection related to r8169 is not working. i have to run ifup/ifdown to make it alive.

---

### Post by Toz on 2011-11-02
Anything interesting in /var/log/pm-suspend.log or the result of:
```
cat /var/log/syslog* | grep PM:
```

---

### Post by vsespb on 2011-11-06
cat /var/log/syslog* | grep PM:

> 
Nov  5 19:53:36 GREEN-U kernel: [    0.000000] PM: Registered nosave memory: 000000000008f000 - 00000000000a0000
Nov  5 19:53:36 GREEN-U kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Nov  5 19:53:36 GREEN-U kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Nov  5 19:53:36 GREEN-U kernel: [    0.000000] PM: Registered nosave memory: 00000000dccef000 - 00000000dcdaa000
Nov  5 19:53:36 GREEN-U kernel: [    0.000000] PM: Registered nosave memory: 00000000df699000 - 00000000df6bf000
Nov  5 19:53:36 GREEN-U kernel: [    0.000000] PM: Registered nosave memory: 00000000df756000 - 00000000df7bf000
Nov  5 19:53:36 GREEN-U kernel: [    0.000000] PM: Registered nosave memory: 00000000df7e8000 - 00000000df7f2000
Nov  5 19:53:36 GREEN-U kernel: [    0.000000] PM: Registered nosave memory: 00000000df7f3000 - 00000000df7ff000
Nov  5 19:53:36 GREEN-U kernel: [    0.000000] PM: Registered nosave memory: 00000000df800000 - 00000000e0000000
Nov  5 19:53:36 GREEN-U kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f8000000
Nov  5 19:53:36 GREEN-U kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 0000000100000000
Nov  5 19:53:36 GREEN-U kernel: [    1.994468] PM: Hibernation image not present or could not be loaded.
Nov  6 13:10:50 GREEN-U kernel: [21576.467437] PM: Syncing filesystems ... done.
Nov  6 13:10:50 GREEN-U kernel: [21576.585126] PM: Preparing system for mem sleep
Nov  6 13:10:50 GREEN-U kernel: [21576.622873] PM: Entering mem sleep
Nov  6 13:10:50 GREEN-U kernel: [21576.752479] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 128.871 msecs
Nov  6 13:10:50 GREEN-U kernel: [21576.991806] PM: suspend of drv:e1000e dev:0000:00:19.0 complete after 368.846 msecs
Nov  6 13:10:50 GREEN-U kernel: [21577.161331] PM: suspend of drv:HDA Intel dev:0000:01:00.1 complete after 539.293 msecs
Nov  6 13:10:50 GREEN-U kernel: [21577.161351] PM: suspend of drv:pcieport dev:0000:00:01.0 complete after 538.800 msecs
Nov  6 13:10:50 GREEN-U kernel: [21577.426757] PM: suspend of drv:sd dev:2:0:0:0 complete after 805.903 msecs
Nov  6 13:10:50 GREEN-U kernel: [21577.426861] PM: suspend of drv:scsi dev:target2:0:0 complete after 805.889 msecs
Nov  6 13:10:50 GREEN-U kernel: [21577.426901] PM: suspend of drv:scsi dev:host2 complete after 805.804 msecs
Nov  6 13:10:50 GREEN-U kernel: [21577.480434] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 859.102 msecs
Nov  6 13:10:50 GREEN-U kernel: [21577.480534] PM: suspend of drv: dev:pci0000:00 complete after 858.876 msecs
Nov  6 13:10:50 GREEN-U kernel: [21577.480542] PM: suspend of devices complete after 859.901 msecs
Nov  6 13:10:50 GREEN-U kernel: [21577.480543] PM: suspend devices took 0.860 seconds
Nov  6 13:10:50 GREEN-U kernel: [21577.480979] PM: late suspend of devices complete after 0.435 msecs
Nov  6 13:10:50 GREEN-U kernel: [21577.481498] PM: Saving platform NVS memory
Nov  6 13:10:50 GREEN-U kernel: [21579.036613] PM: Restoring platform NVS memory
Nov  6 13:10:50 GREEN-U kernel: [21580.738256] PM: early resume of devices complete after 1.193 msecs
Nov  6 13:10:50 GREEN-U kernel: [21580.881593] PM: resume of drv:e1000e dev:0000:00:19.0 complete after 143.683 msecs
Nov  6 13:10:50 GREEN-U kernel: [21580.881601] PM: resume of drv:net dev:eth0 complete after 140.146 msecs
Nov  6 13:10:50 GREEN-U kernel: [21580.914903] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 177.021 msecs
Nov  6 13:10:50 GREEN-U kernel: [21586.218244] PM: resume of drv:sd dev:2:0:0:0 complete after 5495.217 msecs
Nov  6 13:10:50 GREEN-U kernel: [21586.218262] PM: resume of drv:scsi_disk dev:2:0:0:0 complete after 5351.727 msecs
Nov  6 13:10:50 GREEN-U kernel: [21586.218344] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 5495.296 msecs
Nov  6 13:10:50 GREEN-U kernel: [21586.218386] PM: resume of devices complete after 5495.609 msecs
Nov  6 13:10:50 GREEN-U kernel: [21586.218467] PM: resume devices took 5.500 seconds
Nov  6 13:10:50 GREEN-U kernel: [21586.218488] PM: Finishing wakeup.
when I running ifdown/ifup on this nic (eth1) i am getting in logs

> 
[26958.478752] r8169 0000:06:00.0: eth1: link down
[26958.478787] r8169 0000:06:00.0: eth1: link down
[26958.479781] ADDRCONF(NETDEV_UP): eth1: link is not ready
[26960.798527] r8169 0000:06:00.0: eth1: link up
[26960.799890] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
also in dmesg:

> 
[21586.218244] PM: resume of drv:sd dev:2:0:0:0 complete after 5495.217 msecs
[21586.218262] PM: resume of drv:scsi_disk dev:2:0:0:0 complete after 5351.727 msecs
[21586.218344] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 5495.296 msecs
[21586.218386] PM: resume of devices complete after 5495.609 msecs
[21586.218467] PM: resume devices took 5.500 seconds
[21586.218488] PM: Finishing wakeup.
[21586.218490] Restarting tasks ... done.
[21586.824893] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[21586.824915] r8169 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[21586.824973] r8169 0000:06:00.0: setting latency timer to 64
[21586.825078] r8169 0000:06:00.0: irq 49 for MSI/MSI-X
[21586.825621] r8169 0000:06:00.0: eth1: RTL8168b/8111b at 0xffffc90001862000, 94:0c:6d:80:49:e0, XID 18000000 IRQ 49
[21586.842228] r8169 0000:06:00.0: eth1: link down
[21586.842236] r8169 0000:06:00.0: eth1: link down
[21586.843769] ADDRCONF(NETDEV_UP): eth1: link is not ready
I've googled for " ADDRCONF(NETDEV_UP): eth1: link is not ready" but it's always bad cable issues. Not my case. I've just moved flats. I have new cables and new router now, and had same issue in my old flat.

---

### Post by Toz on 2011-11-06
This is interesting. Its as if when the system is trying to reload the module, the network is somehow not ready, forcing it to fail. But when you do it manually, it works (network is ready). Also interesting is that it worked in your old location and not in the new one.

As a workaround, try adding a script to /etc/pm/sleep.d to run the ifdown/ifup commands automatically (with a sleep factor to delay the initialization):
```
sudo gedit /etc/pm/sleep.d/99ifdownifup
```
...with something like:
```

#!/bin/bash
case "$1" in
   suspend|hibernate
      #do nothing
      ;;
   thaw|resume)
      ifdown eth1
      sleep 5
      ifup eth1
      ;;
   *)
   ;;
esac

```
...and make the file executable.

You can try adjusting the sleep value to give it more (or less) of a delay time.

---

### Post by vsespb on 2011-11-06
hi. thanks. well, yes, looks live obvious decision - ifup/ifdown when wake up.
btw 
> 
Also interesting is that it worked in your old location and not in the new one

no, it didn't work in old location, and is not working in new one too.
that means that it's not a cable/ISP/router issue.

---

### Post by vsespb on 2011-12-18
hello. thanks. your solution was working fine. until today

> cat /etc/pm/sleep.d/99ifdownifup
#!/bin/bash

case "$1" in
   suspend|hibernate)
      #do nothing
      ;;
   thaw|resume)
      ifdown eth1
      sleep 3
      ifup eth1
      ;;
   *)
   ;;
esac

usually it works like this

> [185445.609214] r8169 0000:06:00.0: eth1: link down                                                                                                                                                                                                                            
[185447.733634] r8169 0000:06:00.0: eth1: link up   
I have two computers. Mine and gf's Windows pc. eth1 is connected to it. Usually my computer wakes first, but today Windows PC woke up first.
so today's logs


> [197803.309759] r8169 0000:06:00.0: eth1: link up                                                                                                                                                                                                                              
[197803.310485] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready                                                                                                                                                                                                              
[197809.714190] r8169 0000:06:00.0: eth1: link down  > /etc/pm/sleep.d/99ifdownifup resume suspend:ifdown: interface eth1 not configured                                                                                                                                                                                              
SIOCSIFADDR: No such device                                                                                                                                                                                                                                                    
eth1: ERROR while getting interface flags: No such device                                                                                                                                                                                                                      
SIOCSIFNETMASK: No such device                                                                                                                                                                                                                                                 
eth1: ERROR while getting interface flags: No such device                                                                                                                                                                                                                      
Failed to bring up eth1.                                                                                                                                                                                                                                                       
success.
in the end I fixed this by calling ifdown/ifup again

---

