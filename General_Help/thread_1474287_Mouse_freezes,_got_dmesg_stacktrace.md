---
title: "Mouse freezes, got dmesg stacktrace"
date: 2010-05-05
forum: General Help
---

### Post by damien_d on 2010-05-05
Hello all,

I have been having some problems with a mouse on my system (amd64 variant).

The problem has exhibited both with Karmic and Lucid, even after a clean install of Lucid.

I have a logictech wireless keyboard and mouse combo.  After some time, the mouse just randomly freezes, although the keyboard is still responsive.

I plugged in a second USB (standalone) mouse.  It initially worked, but after some time, it also freezes.  I attempted to unplug the frozen second mouse and place into another USB port.  When I did, the red light on the bottom of the mouse failed to light up. 

I then attempted to plug in a third mouse, and it failed to show the light as well.

When ssh'ing from another box, I get the following from dmesg:

```

[79275.300031] usb 4-1: new low speed USB device using ohci_hcd and address 2
[79275.524106] usb 4-1: configuration #1 chosen from 1 choice
[79275.534251] input: USB Optical Mouse as /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.0/input/input7
[79275.534406] generic-usb 0003:0461:4D15.0003: input,hidraw2: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:04.0-1/input0
[82007.655187] npviewer.bin[9999]: segfault at ff999ea8 ip 00000000ff999ea8 sp 00000000ff9f0a7c error 14
[84681.129497] usb 4-1: USB disconnect, address 2
[84840.960030] INFO: task khubd:44 blocked for more than 120 seconds.
[84840.960036] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[84840.960040] khubd         D 0000000000000000     0    44      2 0x00000000
[84840.960048]  ffff880371393bb0 0000000000000046 0000000000015bc0 0000000000015bc0
[84840.960055]  ffff880371371ab0 ffff880371393fd8 0000000000015bc0 ffff8803713716f0
[84840.960060]  0000000000015bc0 ffff880371393fd8 0000000000015bc0 ffff880371371ab0
[84840.960065] Call Trace:
[84840.960077]  [<ffffffff813d4d25>] usb_kill_urb+0x85/0xc0
[84840.960085]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
[84840.960090]  [<ffffffff813d4fbb>] ? usb_get_urb+0x1b/0x30
[84840.960095]  [<ffffffff813d3643>] usb_hcd_flush_endpoint+0x133/0x140
[84840.960100]  [<ffffffff813d598d>] usb_disable_endpoint+0x5d/0x90
[84840.960105]  [<ffffffff813d5a09>] usb_disable_device+0x49/0x130
[84840.960111]  [<ffffffff813cf802>] usb_disconnect+0xd2/0x170
[84840.960116]  [<ffffffff813cfe7f>] hub_port_connect_change+0x8f/0x980
[84840.960121]  [<ffffffff813d1172>] hub_events+0x3b2/0x5a0
[84840.960127]  [<ffffffff8153e738>] ? thread_return+0x48/0x420
[84840.960132]  [<ffffffff813d13b5>] hub_thread+0x55/0x190
[84840.960137]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
[84840.960142]  [<ffffffff813d1360>] ? hub_thread+0x0/0x190
[84840.960147]  [<ffffffff81084fa6>] kthread+0x96/0xa0
[84840.960152]  [<ffffffff810141ea>] child_rip+0xa/0x20
[84840.960156]  [<ffffffff81084f10>] ? kthread+0x0/0xa0
[84840.960160]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
[84960.960030] INFO: task khubd:44 blocked for more than 120 seconds.
[84960.960036] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[84960.960040] khubd         D 0000000000000000     0    44      2 0x00000000
[84960.960048]  ffff880371393bb0 0000000000000046 0000000000015bc0 0000000000015bc0
[84960.960055]  ffff880371371ab0 ffff880371393fd8 0000000000015bc0 ffff8803713716f0
[84960.960060]  0000000000015bc0 ffff880371393fd8 0000000000015bc0 ffff880371371ab0
[84960.960065] Call Trace:
[84960.960077]  [<ffffffff813d4d25>] usb_kill_urb+0x85/0xc0
[84960.960085]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
[84960.960090]  [<ffffffff813d4fbb>] ? usb_get_urb+0x1b/0x30
[84960.960095]  [<ffffffff813d3643>] usb_hcd_flush_endpoint+0x133/0x140
[84960.960100]  [<ffffffff813d598d>] usb_disable_endpoint+0x5d/0x90
[84960.960104]  [<ffffffff813d5a09>] usb_disable_device+0x49/0x130
[84960.960110]  [<ffffffff813cf802>] usb_disconnect+0xd2/0x170
[84960.960115]  [<ffffffff813cfe7f>] hub_port_connect_change+0x8f/0x980
[84960.960120]  [<ffffffff813d1172>] hub_events+0x3b2/0x5a0
[84960.960126]  [<ffffffff8153e738>] ? thread_return+0x48/0x420
[84960.960131]  [<ffffffff813d13b5>] hub_thread+0x55/0x190
[84960.960136]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
[84960.960141]  [<ffffffff813d1360>] ? hub_thread+0x0/0x190
[84960.960145]  [<ffffffff81084fa6>] kthread+0x96/0xa0
[84960.960155]  [<ffffffff810141ea>] child_rip+0xa/0x20
[84960.960159]  [<ffffffff81084f10>] ? kthread+0x0/0xa0
[84960.960163]  [<ffffffff810141e0>] ? child_rip+0x0/0x20

```

The mouse freeze happens fairly regularly, but this is the first time that I have managed to get a stacktrace.  Note that some wired mice seem to be more reliable than others, though I don't have any hard information on that yet.

I have not yet plugged a mouse through a PS2 adapter to see if the problem is repeatable that way. I hope I still have one :) 
[edit]I've just realised that this computer does not have a mouse PS/2 port, so I can't explore this option[/edit]

Has anyone else seen a similar problem?

  -- Damien

---

### Post by thebaz on 2010-05-14
Hi,

I am getting the exact same behavior.


[ 2774.502708] usb 3-4: USB disconnect, address 2
[ 3000.813850] INFO: task khubd:44 blocked for more than 120 seconds.
[ 3000.813856] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3000.813861] khubd         D 0000000000000000     0    44      2 0x00000000
[ 3000.813870]  ffff880074517bb0 0000000000000046 0000000000015bc0 0000000000015bc0
[ 3000.813878]  ffff880074519ab0 ffff880074517fd8 0000000000015bc0 ffff8800745196f0
[ 3000.813883]  0000000000015bc0 ffff880074517fd8 0000000000015bc0 ffff880074519ab0
[ 3000.813889] Call Trace:
[ 3000.813902]  [<ffffffff813d4d25>] usb_kill_urb+0x85/0xc0
[ 3000.813910]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
[ 3000.813915]  [<ffffffff813d4fbb>] ? usb_get_urb+0x1b/0x30
[ 3000.813920]  [<ffffffff813d3643>] usb_hcd_flush_endpoint+0x133/0x140
[ 3000.813925]  [<ffffffff813d598d>] usb_disable_endpoint+0x5d/0x90
[ 3000.813930]  [<ffffffff813d5a09>] usb_disable_device+0x49/0x130
[ 3000.813936]  [<ffffffff813cf802>] usb_disconnect+0xd2/0x170
[ 3000.813941]  [<ffffffff813cfe7f>] hub_port_connect_change+0x8f/0x980
[ 3000.813947]  [<ffffffff813d1172>] hub_events+0x3b2/0x5a0
[ 3000.813953]  [<ffffffff8153e738>] ? thread_return+0x48/0x420
[ 3000.813959]  [<ffffffff813d13b5>] hub_thread+0x55/0x190
[ 3000.813964]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
[ 3000.813969]  [<ffffffff813d1360>] ? hub_thread+0x0/0x190
[ 3000.813973]  [<ffffffff81084fa6>] kthread+0x96/0xa0
[ 3000.813979]  [<ffffffff810141ea>] child_rip+0xa/0x20
[ 3000.813983]  [<ffffffff81084f10>] ? kthread+0x0/0xa0
[ 3000.813987]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
[ 3120.810026] INFO: task khubd:44 blocked for more than 120 seconds.
[ 3120.810032] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3120.810037] khubd         D 0000000000000000     0    44      2 0x00000000
[ 3120.810045]  ffff880074517bb0 0000000000000046 0000000000015bc0 0000000000015bc0
[ 3120.810053]  ffff880074519ab0 ffff880074517fd8 0000000000015bc0 ffff8800745196f0
[ 3120.810058]  0000000000015bc0 ffff880074517fd8 0000000000015bc0 ffff880074519ab0
[ 3120.810064] Call Trace:
[ 3120.810076]  [<ffffffff813d4d25>] usb_kill_urb+0x85/0xc0
[ 3120.810085]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
[ 3120.810090]  [<ffffffff813d4fbb>] ? usb_get_urb+0x1b/0x30
[ 3120.810095]  [<ffffffff813d3643>] usb_hcd_flush_endpoint+0x133/0x140
[ 3120.810100]  [<ffffffff813d598d>] usb_disable_endpoint+0x5d/0x90
[ 3120.810105]  [<ffffffff813d5a09>] usb_disable_device+0x49/0x130
[ 3120.810111]  [<ffffffff813cf802>] usb_disconnect+0xd2/0x170
[ 3120.810116]  [<ffffffff813cfe7f>] hub_port_connect_change+0x8f/0x980
[ 3120.810122]  [<ffffffff813d1172>] hub_events+0x3b2/0x5a0
[ 3120.810128]  [<ffffffff8153e738>] ? thread_return+0x48/0x420
[ 3120.810133]  [<ffffffff813d13b5>] hub_thread+0x55/0x190
[ 3120.810138]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
[ 3120.810143]  [<ffffffff813d1360>] ? hub_thread+0x0/0x190
[ 3120.810148]  [<ffffffff81084fa6>] kthread+0x96/0xa0
[ 3120.810153]  [<ffffffff810141ea>] child_rip+0xa/0x20
[ 3120.810158]  [<ffffffff81084f10>] ? kthread+0x0/0xa0
[ 3120.810162]  [<ffffffff810141e0>] ? child_rip+0x0/0x20

---

### Post by damien_d on 2010-05-15
> **thebaz said:**
> Hi,

I am getting the exact same behavior.



Are you using AMD64?  Do you have a multiple-monitor setup? If so, what's your configuration?

What brand of mouse are you using?

I'm trying to see if we have any common ground.

  -- Damien

---

### Post by thebaz on 2010-05-15
AMD64, yes. Asus M3N78-VM motherboard.

Dual monitors, no.

Bus 004 Device 004: ID 045e:002b Microsoft Corp. Internet Keyboard Pro
Bus 004 Device 003: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 004 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

If I unplug the cordless mouse "base station", I get the errors.

Leaving it plugged in, it seems to work without issue in my case. But as soon as I remove the USB mouse device it tanks.

---

### Post by damien_d on 2010-05-15
> **thebaz said:**
> AMD64, yes. Asus M3N78-VM motherboard.

Dual monitors, no.

Bus 004 Device 004: ID 045e:002b Microsoft Corp. Internet Keyboard Pro
Bus 004 Device 003: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 004 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

If I unplug the cordless mouse "base station", I get the errors.

Leaving it plugged in, it seems to work without issue in my case. But as soon as I remove the USB mouse device it tanks.

Interesting. I have an M4N78 Pro.  Thanks for the (lack of) dual monitor thing - it rules that out.

Can you output the following:
```

damien@damien-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 SATA controller: nVidia Corporation MCP78S [GeForce 8200] AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:11.0 PCI bridge: nVidia Corporation Device 0779 (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:07.0 Serial controller: Device 4348:3253 (rev 10)
01:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation C77 [nForce 750a SLI] (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation GT200b [GeForce GTX 275] (rev a1)
04:00.0 VGA compatible controller: nVidia Corporation GT215 [GeForce GT 240] (rev a2)
04:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
05:00.0 RAID bus controller: Silicon Image, Inc. Device 0242 (rev 01)

```

---

### Post by damien_d on 2010-05-16
> **thebaz said:**
> AMD64, yes. Asus M3N78-VM motherboard.


Another question for you... are you able to connect the mouse to an old-school PS/2 port on that motherboard?  Mine doesn't have one.

  -- Damien

---

### Post by damien_d on 2010-05-26
> **damien_d said:**
> Interesting. I have an M4N78 Pro.  Thanks for the (lack of) dual monitor thing - it rules that out.


Repeated on a different chipset (Motherboard == GA-M750SLI-DS4).

Maybe time to file a bug?

  -- Damien

---

### Post by xeemeex on 2011-01-26
Same behaviour for me.
The computer has rebooted unexpectedly. When gdm started, the mouse (standard usb) was absolutely frozen but the computer worked fine. I attached another usb mouse but nothing changed. After rebooting everything worked.
Here is the last dmesg output:
```

[  240.900058] INFO: task khubd:43 blocked for more than 120 seconds.
[  240.900065] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  240.900072] khubd         D 00000000ffff8d4d     0    43      2 0x00000000
[  240.900083]  ffff88010ad23b00 0000000000000046 ffff880100000000 0000000000015980
[  240.900093]  ffff88010ad23fd8 0000000000015980 ffff88010ad23fd8 ffff88010ad1c4a0
[  240.900102]  0000000000015980 0000000000015980 ffff88010ad23fd8 0000000000015980
[  240.900110] Call Trace:
[  240.900125]  [<ffffffff814077ed>] usb_kill_urb+0x8d/0xd0
[  240.900136]  [<ffffffff8107f730>] ? autoremove_wake_function+0x0/0x40
[  240.900146]  [<ffffffff81408c40>] usb_start_wait_urb+0xe0/0x100
[  240.900154]  [<ffffffff81407f18>] ? usb_init_urb+0x28/0x40
[  240.900162]  [<ffffffff814092ae>] usb_control_msg+0xee/0x180
[  240.900170]  [<ffffffff81401040>] hub_port_init+0x460/0x850
[  240.900179]  [<ffffffff8138f45c>] ? device_pm_init+0x4c/0x60
[  240.900189]  [<ffffffff81036db9>] ? default_spin_lock_flags+0x9/0x10
[  240.900196]  [<ffffffff814024a6>] hub_port_connect_change+0x326/0xa40
[  240.900204]  [<ffffffff81403d32>] hub_events+0x332/0x580
[  240.900212]  [<ffffffff8158775f>] ? schedule+0x3df/0x830
[  240.900219]  [<ffffffff81403fd5>] hub_thread+0x55/0x190
[  240.900226]  [<ffffffff8107f730>] ? autoremove_wake_function+0x0/0x40
[  240.900233]  [<ffffffff81403f80>] ? hub_thread+0x0/0x190
[  240.900240]  [<ffffffff8107f1d6>] kthread+0x96/0xa0
[  240.900247]  [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
[  240.900254]  [<ffffffff8107f140>] ? kthread+0x0/0xa0
[  240.900261]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10

```

And here is my lspci output:
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: ASRock Incorporation Device 9602
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4250]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 USB Controller: Device 1b73:1000 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

```

My architecture is AMD64 too, and I'm using ubuntu maverick.
The problem appeared only once until now.

---

### Post by dbloom on 2011-08-31
i'm having the exact same problem on 11.04. dmesg is very similar when it occurs.  and it sounds like with have very similar setups.  Asus motherboard, AMD 64-bit cpu (quad core), 8gb ram, nvidia sli setup.  i was also using a logitech keyboard and mouse.  keyboard is usually fine (99% of the time).  i've also tried a logitech wireless mouse, same problem.  note, the wireless adapter has both a usb plug as well as a ps/2 plug for the mouse (green).  not sure how it connects.  not sure if it matters due to the usb.

this problem occurred maybe once every 6 months on previous versions.  now it's almost every day and sometimes a few times a day.  this started over the past month or two. during that time, i've added a backup server and UPS to my network -- i map to the server using NFS and i use rsnapshot to run backups.  i've noticed rsnapshot failing to complete probably due to my rebooting to get the mouse function back so i've been wondering if something about that setup may be the culprit.

i'm curious. it's been a while since the last posts.  has anyone found a solution?

thanks.

---

### Post by harryharryharry on 2011-09-09
Same problem here:
M3N78-VM in combination with wireless keyboard & mouse (with one RF nano-receiver):

When I type: no problem
When I use the mouse: no problem

When I move the mouse (excessively) whílst typing: cursor freezes, keyboard still functions...

---

### Post by turbopunsch on 2011-10-17
Yesterday I upgraded to Ubuntu 11.10 (Oneiric Ocelot, kernel 3.0.0-12) and I am still experiencing USB mouse freezes similar to those mentioned above. They occur at least once per day and occasionally also the USB keyboard freezes. Unfortunately nothing chanced since Ubuntu 11.04 (kernel 2.6.27-17 and 2.6.38-11). One additional observation: if I connect a USB microphone, the mouse freezes instantaneously (see attached syslog output).

Machine: AMD Phenom 9850 Quad-Core, 4GB, nVidia MCP78S [GeForce 8200] controller

Any ideas how the problem could be solved would be highly appreciated!

PS: I have attached my dmesg output as well as the syslog kernel messages after a USB mouse freeze following the USB microphone insertion.

---

### Post by turbopunsch on 2012-02-07
My problem is SOLVED!! :D :D :D
There has been not a single USB mouse freeze for several weeks.

I did two things:

1. Adding a kernel option: I added the following line to /etc/default/grub:[INDENT]GRUB_CMDLINE_LINUX="noapic nolapic"
[/INDENT]2. Upgraded kernel to 3.0.0-15 (automatically through Ubuntu updates)

Maybe upgrading the kernel is enough to solve the issue. I kept the kernel options in place since there are no adverse effects. Maybe someone else can report his/her experience.

---

### Post by save2 on 2013-04-18
Hi All
it seems to be a well known problem with Asus motherboards of the M3N78 family.
Not that it is a hardware problem since the same motherboard can work very well in Ubuntu 10.04 or Windows7.
Something bad happened in the later kernels of 11.04+

---

