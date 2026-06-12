---
title: "Old wacom graphire serial, can it work?"
date: 2010-12-28
forum: General Help
---

### Post by Affrikka on 2010-12-28
I have an old wacom graphire tablet that uses a serial port.. Is there any way to get it working on ubuntu, or should I go out and buy a new tablet?

---

### Post by tredegar on 2010-12-28
First, some Q's:

1] What happened when you plugged it in and booted to linux?

2] What did you expect to happen?

3] What are the exact details of this "old wacom graphire tablet that uses a serial port" ?

4] What distro are you running?

---

### Post by Affrikka on 2010-12-28
1) Nothing happened, and I went into the hardware drivers thing under Administration and it didn't find anything

2) I hoped that it would find it and/or install a driver for it

3) [here is a picture of it](http://www.google.com/imgres?imgurl=http://www.karbosguide.com/images/wacom01.jpg&imgrefurl=http://www.karbosguide.com/hardware/module5c2a.htm&h=447&w=550&sz=31&tbnid=VRHNyMWjtrnqwM:&tbnh=108&tbnw=133&prev=/images%3Fq%3Dwacom%2Bgraphire%2B1&zoom=1&q=wacom+graphire+1&usg=__-jjrUgRVY-Sg1oEecSE2HtntDG0=&sa=X&ei=s2gaTcKxC4LGlQeZo6nnCw&ved=0CCQQ9QEwAg) it just has a serial port, a ps/2 male and ps/2 female ports.  I have the serial port plugged in and the ps/2 male port plugged into the mouse spot.

4) 10.10

---

### Post by tredegar on 2010-12-28
> 1) Nothing happened, and I went into the hardware drivers thing under Administration and it didn't find anything
That's OK.
> 2) I hoped that it would find it and/or install a driver for it
Perhaps it did, but linux tends to be quiet, and "just work". It never says "You just plugged in something new and I'll annoy you with these popups while I try to configure it and ask you for your authorisation codes and all, and then ask you to save all your work and reboot". It either works, or gives error messages in the logfiles.

The picture doesn't help: It's just a piece of plastic stuff, with a pen. What is written underneath, on the label? 
USB-connected stuff will identify itself when probed by **lsusb** 
AFIK there is nothing equivalent for serial-port devices which are old... (but probably already well supported).

Seems to me that this is an old wacom tablet on a serial port.
The linux kernel must have known about these for years.

It is probably working already. I don't have one of these, but what sort of application would you expect to use one of these things *with* ?

Maybe something graphic, like **gimp**, or **inkscape** ?

Have you tried firing the gimp or inkscape up and looking for (guess) configure wacom tablet, or just use it and see what happens?

I suspect it's already working, but you haven't tried to use it, because you think you have more steps to go through because you are used to the windows (bad) way of doing things.

Plug it in, fire up an application that might understand the input from one of these things and see what happens.

My hope and expectation is that it'll "just work" when you fire up an application that knows how to use it.

Let us know how you get on.

---

### Post by Affrikka on 2010-12-28
I have tried using it with the gimp, and nothing happened, so I went to 'preferences' and then to 'input' and it isn't listed. It is a serial port, is there any way of looking somewhere and seeing "you're wacom tablet is plugged in and working fine!"?

---

### Post by Favux on 2010-12-28
Hi Affrikka and tredegar,

The short answer is yes your Graphire2 can be made to work.

The key question is what release of Ubuntu is Affrikka using?

Starting with Lucid and its default X server 1.7 Xorg took over the Wacom X driver wacom_drv.so with xf86-input-wacom from linuxwacom and dropped support for serial tablets (not serial tablet pc's).  But that was from lack of developer resources, not policy.  By policy they dropped wacdump, xidump, wacomcpl, and now multimonitor support.

Some folks who could code have developed a patch set to restore serial tablet function to xf86-input-wacom and by applying the patches to 0.10-5 or 0.10-6 you can add serial tablet function back in.

See "Notice for Serial Graphics Tablet Users" in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") for a brief discussion and links.

---

### Post by tredegar on 2010-12-28
I'm out of my depth here, and don't have a tablet to play with.

Next suggestion:
Plug it in. After next reboot read the contents of **/var/log/messages**

You can scroll down quite fast as there'll be a lot of irrelevant information. But somewhere there will be information about how the kernel sees the wacom.

Edit out those lines, and post them here, you should be able to recognise them. Maybe we can take it from there.

---

### Post by Affrikka on 2010-12-28
Hi Favux,

I'm using ubuntu 10.10, and not being good with technical jargon I am a little confused on with the notice to serial users on your guide-- is it still not support with anything about 10.04?

Edit: here's the stuff from my last boot-up

```
Dec 28 19:27:03 Prometheus kernel: imklog 4.2.0, log source = /proc/kmsg started.
Dec 28 19:27:03 Prometheus rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="857" x-info="http://www.rsyslog.com"] (re)start
Dec 28 19:27:03 Prometheus rsyslogd: rsyslogd's groupid changed to 103
Dec 28 19:27:03 Prometheus rsyslogd: rsyslogd's userid changed to 101
Dec 28 19:27:03 Prometheus kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 28 19:27:03 Prometheus kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 28 19:27:03 Prometheus kernel: [    0.000000] Linux version 2.6.35-23-generic (buildd@allspice) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 (Ubuntu 2.6.35-23.41-generic 2.6.35.7)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=69520329-3fe2-404d-a4a4-cc7af7fd1332 ro quiet splash
Dec 28 19:27:03 Prometheus kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 28 19:27:03 Prometheus kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Dec 28 19:27:03 Prometheus kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 28 19:27:03 Prometheus kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Dec 28 19:27:03 Prometheus kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fe6e000 (usable)
Dec 28 19:27:03 Prometheus kernel: [    0.000000]  BIOS-e820: 000000003fe6e000 - 000000003fee8000 (ACPI NVS)
Dec 28 19:27:03 Prometheus kernel: [    0.000000]  BIOS-e820: 000000003fee8000 - 000000003feec000 (usable)
Dec 28 19:27:03 Prometheus kernel: [    0.000000]  BIOS-e820: 000000003feec000 - 000000003feff000 (ACPI data)
Dec 28 19:27:03 Prometheus kernel: [    0.000000]  BIOS-e820: 000000003feff000 - 000000003ff00000 (usable)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 28 19:27:03 Prometheus kernel: [    0.000000] DMI 2.3 present.
Dec 28 19:27:03 Prometheus kernel: [    0.000000] No AGP bridge found
Dec 28 19:27:03 Prometheus kernel: [    0.000000] last_pfn = 0x3ff00 max_arch_pfn = 0x400000000
Dec 28 19:27:03 Prometheus kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 28 19:27:03 Prometheus kernel: [    0.000000] Scanning 1 areas for low memory corruption
Dec 28 19:27:03 Prometheus kernel: [    0.000000] modified physical RAM map:
Dec 28 19:27:03 Prometheus kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Dec 28 19:27:03 Prometheus kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Dec 28 19:27:03 Prometheus kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 28 19:27:03 Prometheus kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Dec 28 19:27:03 Prometheus kernel: [    0.000000]  modified: 0000000000100000 - 000000003fe6e000 (usable)
Dec 28 19:27:03 Prometheus kernel: [    0.000000]  modified: 000000003fe6e000 - 000000003fee8000 (ACPI NVS)
Dec 28 19:27:03 Prometheus kernel: [    0.000000]  modified: 000000003fee8000 - 000000003feec000 (usable)
Dec 28 19:27:03 Prometheus kernel: [    0.000000]  modified: 000000003feec000 - 000000003feff000 (ACPI data)
Dec 28 19:27:03 Prometheus kernel: [    0.000000]  modified: 000000003feff000 - 000000003ff00000 (usable)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] found SMP MP-table at [ffff8800000fe680] fe680
Dec 28 19:27:03 Prometheus kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000003ff00000
Dec 28 19:27:03 Prometheus kernel: [    0.000000] RAMDISK: 2f495000 - 2ff12000
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: RSDP 00000000000fe020 00014 (v00 INTEL )
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: RSDT 000000003fefde48 00054 (v01 INTEL  D945GTP  00000F9C MSFT 01000013)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: FACP 000000003fefcf10 00074 (v01 INTEL  D945GTP  00000F9C MSFT 01000013)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: DSDT 000000003fef7010 042BF (v01 INTEL  D945GTP  00000F9C MSFT 01000013)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: FACS 000000003fedcc40 00040
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: APIC 000000003fefce10 00078 (v01 INTEL  D945GTP  00000F9C MSFT 01000013)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: WDDT 000000003fef6f90 00040 (v01 INTEL  D945GTP  00000F9C MSFT 01000013)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: MCFG 000000003fef6f10 0003C (v01 INTEL  D945GTP  00000F9C MSFT 01000013)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: ASF! 000000003fefcd10 000A6 (v32 INTEL  D945GTP  00000F9C MSFT 01000013)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: SSDT 000000003fefdc10 001BC (v01 INTEL     CpuPm 00000F9C MSFT 01000013)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: SSDT 000000003fefda10 00175 (v01 INTEL   Cpu0Ist 00000F9C MSFT 01000013)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: SSDT 000000003fefd810 00175 (v01 INTEL   Cpu1Ist 00000F9C MSFT 01000013)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: SSDT 000000003fefd610 00175 (v01 INTEL   Cpu2Ist 00000F9C MSFT 01000013)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: SSDT 000000003fefd410 00175 (v01 INTEL   Cpu3Ist 00000F9C MSFT 01000013)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: SSDT 000000003fef6e90 0002F (v01 INTEL  SetupVar 00000F9C MSFT 01000013)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: TCPA 000000003fee3d90 00028 (v01 INTEL  TIANO    00000002 MSFT 01000013)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] No NUMA configuration found
Dec 28 19:27:03 Prometheus kernel: [    0.000000] Faking a node at 0000000000000000-000000003ff00000
Dec 28 19:27:03 Prometheus kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000003ff00000
Dec 28 19:27:03 Prometheus kernel: [    0.000000]   NODE_DATA [0000000001d18180 - 0000000001d1d17f]
Dec 28 19:27:03 Prometheus kernel: [    0.000000] Zone PFN ranges:
Dec 28 19:27:03 Prometheus kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Dec 28 19:27:03 Prometheus kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Dec 28 19:27:03 Prometheus kernel: [    0.000000]   Normal   empty
Dec 28 19:27:03 Prometheus kernel: [    0.000000] Movable zone start PFN for each node
Dec 28 19:27:03 Prometheus kernel: [    0.000000] early_node_map[4] active PFN ranges
Dec 28 19:27:03 Prometheus kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Dec 28 19:27:03 Prometheus kernel: [    0.000000]     0: 0x00000100 -> 0x0003fe6e
Dec 28 19:27:03 Prometheus kernel: [    0.000000]     0: 0x0003fee8 -> 0x0003feec
Dec 28 19:27:03 Prometheus kernel: [    0.000000]     0: 0x0003feff -> 0x0003ff00
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Dec 28 19:27:03 Prometheus kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
```

---

### Post by Favux on 2010-12-28
Hi Affrikka,

Right, the serial patchset was stuck in Lucid because the 0.10.6 xf86-input-wacom wouldn't compile in Maverick.  But then thorwil found out how to get it to compile in Maverick.  So you first patch 0.10.6 with the serial patches and follow with thorwils Maverick patch and ta da you can compile 0.10.6 xf86-input-wacom and get a serial tablet working in Maverick.

---

### Post by Affrikka on 2010-12-28
Alright, I understand what you're saying. Seems like a lot of work haha, I will see what I can do. Thanks for your help!

---

### Post by Favux on 2010-12-28
Good luck!

It is a fair amount of work.  I keep hoping someone with a serial tablet will post a HOW TO to help others.  Working with another serial tablet user right now who's thinking about doing it.

---

