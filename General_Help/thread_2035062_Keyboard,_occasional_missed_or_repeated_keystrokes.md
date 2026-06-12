---
title: "Keyboard, occasional missed or repeated keystrokes, in both gnome and on tty"
date: 2012-07-29
forum: General Help
---

### Post by porrifolius on 2012-07-29
Hello.

A couple of days ago I installed Ubuntu 12.04 (directly) on my laptop.  Previously I was running a Debian squeeze host with an Ubuntu 11 guest VM.

Since the upgrade I occasionally lose one or two keypresses at a time when typing, less frequently the lost characters will be replaced with the prior character typed.

It is not due to typing errors and I'm certain it's not a keyboard hardware problem.  No changes have been made to the BIOS.


The problem occurs when using the desktop and when using e.g. vim on a tty.

I think that the problem occurs less frequently when using the tty but it does still happen.  I don't type blisteringly fast.

My laptop has a EN US keyboard but I use a EN Dvorak keyboard layout.  I still have the problem when I select the EN US layout in the desktop and after  doing
$ loadkeys us
on the tty.

I do get a message stating "unknown charset unicode - ignoring charset request" when doing loadkeys but otherwise it seems to work fine.


What diagnostic information should I collect to help solve this? 


Thanks very much.


As an example of the problem and frequency (which makes using the laptop an extreme pain):

the quick brown fox jumped over the lazy dog
the quick brown fox jumped over the lly dog
the quick brown fox jumped over the lazy dog
the quick brown fox jumped over the lazy dog
the quick brown fox jumped over the lazy dog
the quick brown fox jumped over the ly dog
the quick brown fox jumped over the lazy dog
the quick brown fox jumped over the lazy dog
the quick brown fox jumped over the lazy dog
the quick brown fox jumped over thhhlazy dog
the quick brown fox jumped over the lazy dog
the quick brown fox jumped over the lazy dog
the quick brown fox jumped over the lazy dog
the quick brown fox jumped over the lazy dog
the quick brown fox jumped over the lazy dog
the quick brown fox jumped over the lazy dog
the quick brown fox jumped over the lazy dog
the quick brown fox jumped over the lazy dog
the quick brown foxjumped over the lazy dog
the quick brown fox jumped over the lazy dog

---

### Post by porrifolius on 2012-07-31
It seems that an external USB keyboard does not suffer the same problems, so could it perhaps be to do with some kernel facilities for handling misbehaving laptop chipsets?

The laptop is a HP Pavilion DV7, here is the lspci and lsusb output:

```

root:~# lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core  Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler XT [AMD Radeon HD 6700M Series]
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
19:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

``````

root:~# lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc. 
Bus 001 Device 004: ID 5986:02ac Acer, Inc 

```Any ideas on solutions or diagnosing this problem?

Thanks.

---

### Post by porrifolius on 2012-07-31
Lots of these:

 psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1

in /var/log/kern.log

Looks like a kernel bug, maybe as per [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/717970](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/717970)

Adding psmouse to SUSPEND_MODULES in /etc/pm/config.d/modules seems to be fixing my problem... dunno if it still happens on battery or other situations reported in the various tickets.

I'll call it solved for now.

Thanks.

---

