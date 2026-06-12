---
title: "USB flash drive not in /dev"
date: 2011-11-24
forum: General Help
---

### Post by bart.vanaudenhove on 2011-11-24
Hello,

I am sorry to post another thread here about USB flash drives not working. I _have_ searched around and tried various things but nothing works.

I use 10.04 LTS on an (older) Acer desktop. USB works for printer, keyboard and mouse. But nothing happens when inserting an USB flash drive - it doesn't appeard in /dev either so it's not just a problem of mounting.

Here's what I tried from other posts:
[LIST]
[*]Nautilus media_automount and such are checked. (see [Mount/USB - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Mount/USB"))
[*]BIOS doesn't have anything related to Legacy (as I see it) and I disabled the floppy modprobe (see [Fix USB Devices Automount Not Working In Ubuntu 10.04 Lucid Lynx]("http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html"))
[*]I tried different flash drives, none work.
[/LIST]

Here is some code:

```
bart@bart-desktop:~$ sudo fdisk -l
[sudo] password for bart: 

Schijf /dev/sda: 80.0 GB, 80026361856 bytes
255 koppen, 63 sectoren/spoor, 9729 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes
in-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijf-ID: 0x000a9962

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Uitgebreid
/dev/sda5            9328        9730     3227648   82  Linux wisselgeheugen

```
(this is with the flash drive inserted)

```
bart@bart-desktop:~$ lsusb
Bus 004 Device 003: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 004 Device 002: ID 046d:c05b Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

And output (last lines) from dmesg just after inserting flash drive:
```
[   15.103714] type=1505 audit(1322128571.478:7):  operation="profile_replace" pid=618 name="/usr/lib/connman/scripts/dhclient-script"
[   15.241245] [drm] radeon defaulting to kernel modesetting.
[   15.241256] [drm] radeon kernel modesetting enabled.
[   15.241383] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.244761] [drm] radeon: Initializing kernel modesetting.
[   15.253683] [drm] register mmio base: 0xFF4F0000
[   15.253688] [drm] register mmio size: 65536
[   15.256460] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   15.256488] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[   15.256581] [drm] Generation 2 PCI interface, using max accessible memory
[   15.256586] [drm] radeon: VRAM 32M
[   15.256590] [drm] radeon: VRAM from 0x7E000000 to 0x7FFFFFFF
[   15.256594] [drm] radeon: GTT 32M
[   15.256597] [drm] radeon: GTT from 0x80000000 to 0x81FFFFFF
[   15.256630] [drm] radeon: irq initialized.
[   15.257064] [drm] Detected VRAM RAM=32M, BAR=128M
[   15.257071] [drm] RAM width 128bits DDR
[   15.257229] [TTM] Zone  kernel: Available graphics memory: 437072 kiB.
[   15.257234] [TTM] Zone highmem: Available graphics memory: 1014516 kiB.
[   15.257260] [drm] radeon: 32M of VRAM memory ready
[   15.257265] [drm] radeon: 32M of GTT memory ready.
[   15.257291] [drm] GART: num cpu pages 8192, num gpu pages 8192
[   15.257999] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   15.258021] [drm] radeon: cp idle (0x10000C03)
[   15.258096] [drm] Loading R300 Microcode
[   15.258104] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   15.266624] [drm] radeon: ring at 0x0000000080000000
[   15.266656] [drm] ring test succeeded in 1 usecs
[   15.266961] [drm] radeon: ib pool ready.
[   15.267091] [drm] ib test succeeded in 0 usecs
[   15.267144] [drm] Default TV standard: NTSC
[   15.267148] [drm] 14.318180000 MHz TV ref clk
[   15.267310] [drm] Default TV standard: NTSC
[   15.267314] [drm] 14.318180000 MHz TV ref clk
[   15.267374] [drm] Radeon Display Connectors
[   15.267379] [drm] Connector 0:
[   15.267382] [drm]   VGA
[   15.267387] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   15.267390] [drm]   Encoders:
[   15.267394] [drm]     CRT1: INTERNAL_DAC2
[   15.267397] [drm] Connector 1:
[   15.267400] [drm]   S-video
[   15.267403] [drm]   Encoders:
[   15.267406] [drm]     TV1: INTERNAL_DAC2
[   15.288741] [drm] fb mappable at 0xD0040000
[   15.288749] [drm] vram apper at 0xD0000000
[   15.288753] [drm] size 786432
[   15.288756] [drm] fb depth is 8
[   15.288760] [drm]    pitch is 1024
[   15.288948] fb0: radeondrmfb frame buffer device
[   15.288953] registered panic notifier
[   15.288964] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   15.297788] vga16fb: initializing
[   15.297797] vga16fb: mapped to 0xc00a0000
[   15.297805] vga16fb: not registering due to another framebuffer present
[   15.384470] Console: switching to colour frame buffer device 128x48
[   15.424108]   alloc irq_desc for 22 on node -1
[   15.424115]   alloc kstat_irqs on node -1
[   15.424128] HDA Intel 0000:00:1d.0: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   15.547263] hda_codec: ALC880: BIOS auto-probing.
[   15.548950] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1d.0/input/input6
[   15.700467] type=1505 audit(1322128572.074:8):  operation="profile_replace" pid=780 name="/sbin/dhclient3"
[   15.705929] type=1505 audit(1322128572.082:9):  operation="profile_replace" pid=780 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.706422] type=1505 audit(1322128572.082:10):  operation="profile_replace" pid=780 name="/usr/lib/connman/scripts/dhclient-script"
[   15.724786] type=1505 audit(1322128572.102:11):  operation="profile_load" pid=779 name="/usr/share/gdm/guest-session/Xsession"
[   15.806003] skge eth0: enabling interface
[   15.820586] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.272727] vboxdrv: Found 2 processor cores.
[   16.273402] vboxdrv: fAsync=1 offMin=0x3ded1475 offMax=0x3ded1475
[   16.273518] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   16.273523] vboxdrv: Successfully loaded version 4.1.6 (interface 0x00190000).
[   16.512676] vboxpci: IOMMU not found (not compiled)
[   17.131181] CPU0 attaching NULL sched-domain.
[   17.131192] CPU1 attaching NULL sched-domain.
[   17.160689] CPU0 attaching sched-domain:
[   17.160698]  domain 0: span 0-1 level SIBLING
[   17.160704]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   17.160717]   domain 1: span 0-1 level MC
[   17.160722]    groups: 0-1 (cpu_power = 1178)
[   17.160734] CPU1 attaching sched-domain:
[   17.160739]  domain 0: span 0-1 level SIBLING
[   17.160745]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   17.160755]   domain 1: span 0-1 level MC
[   17.160760]    groups: 0-1 (cpu_power = 1178)
[   17.694869] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[   17.695123] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   18.863788] CPU0 attaching NULL sched-domain.
[   18.863802] CPU1 attaching NULL sched-domain.
[   18.881355] CPU0 attaching sched-domain:
[   18.881363]  domain 0: span 0-1 level SIBLING
[   18.881369]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   18.881381]   domain 1: span 0-1 level MC
[   18.881386]    groups: 0-1 (cpu_power = 1178)
[   18.881398] CPU1 attaching sched-domain:
[   18.881402]  domain 0: span 0-1 level SIBLING
[   18.881406]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   18.881417]   domain 1: span 0-1 level MC
[   18.881421]    groups: 0-1 (cpu_power = 1178)
[   27.912020] eth0: no IPv6 routers present
```

Can anyone help please? Thanks in advance...

(I can type stuff in command line and such and have a basic working knowledge of linux but no IT skills whatsoever).

---

### Post by Arachan on 2011-12-19
Hello,

I dunno if you solved this, but I have the same issue. Is your flash drive faulty maybe?

arachan.

---

### Post by Synoc on 2011-12-20
+1 
First instinct is yes, faulty flash drive. Try it on another PC. If the problem persists, it is most likely a bad drive. If not, try a known good drive in the offending computer, but since you say it works wtth other usb devices, I do not think that is the trouble

---

### Post by bart.vanaudenhove on 2011-12-20
No, it's not the flash drive (usb stick) itself.  I tried another flash drive, that worked on another computer, and it didn't work on mine.
It really is the computer.

I upgraded to latest Ubuntu in the meanwhile (11 something, I'm at another computer now), same problem.

---

### Post by dcstar on 2011-12-21
> **bart.vanaudenhove said:**
> No, it's not the flash drive (usb stick) itself.  I tried another flash drive, that worked on another computer, and it didn't work on mine.
It really is the computer.

I upgraded to latest Ubuntu in the meanwhile (11 something, I'm at another computer now), same problem.

If the flash drive requires USB 2 ports and your old hardware only has USB 1 ports then it may not provide enough power to run the USB stick. Printers and other devices provide their own power.

Try it with an external powered USB hub.

---

### Post by bart.vanaudenhove on 2011-12-21
> **dcstar said:**
> If the flash drive requires USB 2 ports and your old hardware only has USB 1 ports then it may not provide enough power to run the USB stick. Printers and other devices provide their own power.

Try it with an external powered USB hub.

Interesting, that might be it, thanks. Is there an easy way to know if it's USB 1 or 2 on that computer?

---

### Post by Synoc on 2011-12-23
easiest way would be to check the specs for your motherboard or USB PCI card (if added. otherwise, do as suggested and plug the drive into an externally powered USB 2 Hub. 14 bucks at some computer stores.

---

