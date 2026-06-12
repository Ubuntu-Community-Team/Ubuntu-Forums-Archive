---
title: "Random reboot"
date: 2011-04-19
forum: General Help
---

### Post by brantleyr on 2011-04-19
My computer is randomly rebooting. There is no pattern to it at all. It could happen after a minute or days and its not relative to load that I know of yet. I monitored CPU Proc temps as well as GPU temps and those seem to be normal or stay around the same value, no oscillations etc so I dont think its overheating. What are normal operating temps for procs and gpus? Just as well here is some output I got from my last reboot.

> richard@Richard:~$ tail -n 50 /var/log/messages
Apr 19 12:25:57 Richard kernel: [    7.981614] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Apr 19 12:25:57 Richard kernel: [   26.884200] Adding 3068924k swap on /dev/sda5.  Priority:-1 extents:1 across:3068924k 
Apr 19 12:25:57 Richard kernel: [   26.941811] udev[330]: starting version 163
Apr 19 12:25:57 Richard kernel: [   27.053069] lp: driver loaded but no devices found
Apr 19 12:25:57 Richard kernel: [   27.366703] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Apr 19 12:25:57 Richard kernel: [   27.391469] intel_rng: FWH not detected
Apr 19 12:25:57 Richard kernel: [   27.443721] Linux agpgart interface v0.103
Apr 19 12:25:57 Richard kernel: [   27.498946] parport_pc 00:08: reported by Plug and Play ACPI
Apr 19 12:25:57 Richard kernel: [   27.498997] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Apr 19 12:25:57 Richard kernel: [   27.566465] udev[449]: renamed network interface eth0 to eth0-eth1
Apr 19 12:25:57 Richard kernel: [   27.582691] udev[378]: renamed network interface eth1 to eth0
Apr 19 12:25:57 Richard kernel: [   27.617229] udev[449]: renamed network interface eth0-eth1 to eth1
Apr 19 12:25:57 Richard kernel: [   27.694240] lp0: using parport0 (interrupt-driven).
Apr 19 12:25:57 Richard kernel: [   27.851164] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5C11
Apr 19 12:25:57 Richard kernel: [   27.851205] usbcore: registered new interface driver usblp
Apr 19 12:25:57 Richard kernel: [   28.143262] ppdev: user-space parallel port driver
Apr 19 12:25:57 Richard kernel: [   28.217105] nvidia: module license 'NVIDIA' taints kernel.
Apr 19 12:25:57 Richard kernel: [   28.217111] Disabling lock debugging due to kernel taint
Apr 19 12:25:57 Richard kernel: [   28.235428] type=1400 audit(1303230355.658:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=638 comm="apparmor_parser"
Apr 19 12:25:57 Richard kernel: [   29.335281] type=1400 audit(1303230356.758:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=651 comm="apparmor_parser"
Apr 19 12:25:57 Richard kernel: [   29.336247] type=1400 audit(1303230356.762:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=638 comm="apparmor_parser"
Apr 19 12:25:57 Richard kernel: [   29.336670] type=1400 audit(1303230356.762:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=638 comm="apparmor_parser"
Apr 19 12:25:57 Richard kernel: [   29.354868] type=1400 audit(1303230356.778:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=651 comm="apparmor_parser"
Apr 19 12:25:57 Richard kernel: [   29.355486] type=1400 audit(1303230356.778:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=651 comm="apparmor_parser"
Apr 19 12:25:57 Richard kernel: [   29.880607] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 19 12:25:57 Richard kernel: [   29.880627] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Apr 19 12:25:57 Richard kernel: [   29.881735] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
Apr 19 12:25:57 Richard kernel: [   30.033084] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr 19 12:25:57 Richard kernel: [   30.038375] usbcore: registered new interface driver snd-usb-audio
Apr 19 12:25:57 Richard kernel: [   30.250619] type=1400 audit(1303230357.674:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=829 comm="apparmor_parser"
Apr 19 12:25:57 Richard kernel: [   30.276122] type=1400 audit(1303230357.702:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=832 comm="apparmor_parser"
Apr 19 12:25:57 Richard kernel: [   30.276897] type=1400 audit(1303230357.702:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=832 comm="apparmor_parser"
Apr 19 12:25:57 Richard kernel: [   30.277318] type=1400 audit(1303230357.702:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=832 comm="apparmor_parser"
Apr 19 12:25:57 Richard kernel: [   30.320773] eth0: Link speed = 100Mbps.
Apr 19 12:25:57 Richard kernel: [   30.320780] eth0: setting full duplex, TX flow control, RX flow control.
Apr 19 12:25:57 Richard kernel: [   30.320792] eth0: Link speed = 100Mbps.
Apr 19 12:25:57 Richard kernel: [   30.320795] eth0: setting full duplex, TX flow control, RX flow control.
Apr 19 12:25:57 Richard kernel: [   30.345695] eth1: link down
Apr 19 12:25:57 Richard kernel: [   30.352362] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 19 12:25:57 Richard kernel: [   30.392089] intel8x0_measure_ac97_clock: measured 56000 usecs (2698 samples)
Apr 19 12:25:57 Richard kernel: [   30.392094] intel8x0: clocking to 48000
Apr 19 12:26:03 Richard kernel: [   36.476405] usb 1-3: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Apr 19 12:28:58 Richard kernel: [   38.856525] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Apr 19 12:28:59 Richard pulseaudio[1435]: lock-autospawn.c: Cannot access autospawn lock.
Apr 19 12:29:01 Richard kernel: [   41.889417] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Apr 19 12:29:05 Richard pulseaudio[1430]: ratelimit.c: 4 events suppressed
Apr 19 12:29:14 Richard pulseaudio[1620]: ratelimit.c: 20 events suppressed
Apr 19 12:30:32 Richard kernel: [  132.980220] ptrace of non-child pid 2003 was attempted by: firefox-bin (pid 2002)
Apr 19 12:30:32 Richard kernel: [  132.980228] ptrace of non-child pid 2004 was attempted by: firefox-bin (pid 2002)
Apr 19 12:30:32 Richard kernel: [  132.980233] ptrace of non-child pid 2008 was attempted by: firefox-bin (pid 2002)
richard@Richard:~$> richard@Richard:~$ uname -a
Linux Richard 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux
> serichard@Richard:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +126.0°C)                  


> richard@Richard:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 4
model name    : Intel(R) Celeron(R) CPU 2.93GHz
stepping    : 1
cpu MHz        : 2933.606
cache size    : 256 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr
bogomips    : 5867.21
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

richard@Richard:~$ 


---

### Post by brantleyr on 2011-04-19
My guess right now is its either audio related and/or related to firefox. Either of which is causing my system to crash and/or reboot.

---

