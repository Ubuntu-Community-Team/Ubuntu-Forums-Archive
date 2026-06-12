---
title: "Boot hangs while adding swap"
date: 2010-09-30
forum: General Help
---

### Post by fzaker on 2010-09-30
Boot process hangs after reaching the following line:
Adding 5853176k swap on /dev/mapper/mch-swap_1. Priority:-1 extents:1 across:5853176k

OS: Ubuntu Server 10.04 64bit
Machine: HP DL380

Any help is appreciated.

---

### Post by andrewthomas on 2010-09-30
I would check that the entries in /etc/fstab match the UUID's output by 

```
sudo blkid
```

---

### Post by fzaker on 2010-10-01
Using knoppix 6.2 as LiveCD, and mounting the partitions, I got the following:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/mch-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/cciss/c0d0p1 during installation
UUID=1ed04531-7af8-44bb-9f5f-37a2cd53c93c /boot           ext2    defaults     0        2
/dev/mapper/mch-swap_1 none            swap    sw              0       0

``````

root@Microknoppix:/dev/mapper# sudo blkid
/dev/cloop0: LABEL="KNOPPIX_FS" TYPE="iso9660" 
/dev/cciss/c0d0p1: UUID="1ed04531-7af8-44bb-9f5f-37a2cd53c93c" TYPE="ext2" 
/dev/cciss/c0d0p5: UUID="OU8xPs-wVaW-Tx5j-a9y1-DKvL-CNeY-iiikEg" TYPE="LVM2_member" 
/dev/mapper/mch-root: UUID="6f1e6a6a-3578-497e-b6de-ce63b5bb2bd5" TYPE="ext4" 
/dev/mapper/mch-swap_1: UUID="25f06ce3-c242-4e6e-b5e0-5ffc28aec059" TYPE="swap" 

```
Is there any problem in fstab?
Please help me. I could not reinstall the server.

---

### Post by luvshines on 2010-10-01
Aren't these the exactly same posts:
[http://ubuntuforums.org/showthread.php?t=1585268&highlight=possibly+due+swap](http://ubuntuforums.org/showthread.php?t=1585268&highlight=possibly+due+swap)

LOL!! **Marking this as duplicate** :D

---

### Post by fzaker on 2010-10-01
> **luvshines said:**
> Aren't these the exactly same posts:
[http://ubuntuforums.org/showthread.php?t=1585268&highlight=possibly+due+swap](http://ubuntuforums.org/showthread.php?t=1585268&highlight=possibly+due+swap)

LOL!! **Marking this as duplicate** :D

Yes, I did post that first and want to remove it (unsuccessfully!). I prefer this one to remain active.

---

### Post by luvshines on 2010-10-01
No issues. The important thing is that it shud be resolved.

Just saw that your fstab entry for 'swap' is shown as
/dev/mapper/mch-swap_1 none            swap    sw              0       0

Mine swap file entry is of the type
/myswap         swap            swap    defaults        0       0

---

### Post by fzaker on 2010-10-01
Thank you for your response. I am not familiar with fstab structure. I don't know what changes I should make into it. Can you give more advice?

---

### Post by luvshines on 2010-10-01
Try using the entry of the type:
/dev/mapper/mch-swap_1 swap            swap    defaults              0       0

---

### Post by fzaker on 2010-10-01
I found that if I remove the swap from fstab, "Adding swap" line does not appear and it hangs on previous line. So it is not related to swap creation.
I had already used workarounds in [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/) and none of them worked for me.
Please somebody help me or show me a reference for diagnosing my problem. I am totally confused. Is there a log or something anywhere?

---

### Post by luvshines on 2010-10-01
You can find the logs in /var/log/dmesg
Also, /var/log/boot.log, bootstrap.log etc

Maybe these can point to the actual problem creator

---

### Post by fzaker on 2010-10-01
Thank you luvshines. Going to take a look!

---

### Post by fzaker on 2010-10-01
final lines of dmesg:
```

[    2.769964] cciss 0000:04:00.0: irq 63 for MSI/MSI-X
[    2.775729] IRQ 62/cciss0: IRQF_DISABLED is not guaranteed on shared IRQs
[    2.775751] cciss0: <0x323a> at PCI 0000:04:00.0 IRQ 62 using DAC
[    2.779500]  cciss/c0d0: p1 p2 < p5 >
[    2.786643] usbcore: registered new interface driver hiddev
[    2.801083] input: Plus More Enterprise LTD. USB-compliant keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input2
[    2.801155] generic-usb 0003:0518:0001.0001: input,hidraw0: USB HID v1.10 Keyboard [Plus More Enterprise LTD. USB-compliant keyboard] on usb-0000:00:1d.2-2/input0
[    2.814621] usb 6-1: configuration #1 chosen from 1 choice
[    2.820061] input: Plus More Enterprise LTD. USB-compliant keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input3
[    2.820144] generic-usb 0003:0518:0001.0002: input,hidraw1: USB HID v1.10 Mouse [Plus More Enterprise LTD. USB-compliant keyboard] on usb-0000:00:1d.2-2/input1
[    2.827832] input: HP Virtual Keyboard as /devices/pci0000:00/0000:00:1e.0/0000:01:04.4/usb6/6-1/6-1:1.0/input/input4
[    2.827896] generic-usb 0003:03F0:1027.0003: input,hidraw2: USB HID v1.01 Keyboard [HP Virtual Keyboard] on usb-0000:01:04.4-1/input0
[    2.834334] input: HP Virtual Keyboard as /devices/pci0000:00/0000:00:1e.0/0000:01:04.4/usb6/6-1/6-1:1.1/input/input5
[    2.834412] generic-usb 0003:03F0:1027.0004: input,hidraw3: USB HID v1.01 Mouse [HP Virtual Keyboard] on usb-0000:01:04.4-1/input1
[    2.834432] usbcore: registered new interface driver usbhid
[    2.834435] usbhid: v2.6:USB HID core driver
[    2.937516] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
[    2.937521] EXT4-fs (dm-0): write access will be enabled during recovery
[    3.207004] EXT4-fs (dm-0): recovery complete
[    3.221928] EXT4-fs (dm-0): mounted filesystem with ordered data mode
[    8.381738] Adding 5853176k swap on /dev/mapper/afc-swap_1.  Priority:-1 extents:1 across:5853176k 
[    8.384694] udev: starting version 151
[    8.400074] lp: driver loaded but no devices found
[    8.414174] power_meter ACPI000D:00: Found ACPI power meter.
[    8.414240] power_meter ACPI000D:00: Ignoring unsafe software power cap!
[    8.432517] Broadcom NetXtreme II Gigabit Ethernet Driver bnx2 v2.0.2 (Aug 21, 2009)
[    8.432541] bnx2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.432552] bnx2 0000:02:00.0: setting latency timer to 64
[    8.432802] bnx2 0000:02:00.0: firmware: requesting bnx2/bnx2-mips-09-5.0.0.j3.fw
[    8.441110] ipmi message handler version 39.2
[    8.478876] bnx2 0000:02:00.0: firmware: requesting bnx2/bnx2-rv2p-09-5.0.0.j3.fw
[    8.480900] [drm] Initialized drm 1.1.0 20060810
[    8.481279] eth0: Broadcom NetXtreme II BCM5709 1000Base-T (C0) PCI Express found at mem f4000000, IRQ 16, node addr d8:d3:85:aa:bd:ba
[    8.481314] bnx2 0000:02:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    8.481323] bnx2 0000:02:00.1: setting latency timer to 64
[    8.481507] bnx2 0000:02:00.1: firmware: requesting bnx2/bnx2-mips-09-5.0.0.j3.fw
[    8.483356] hpilo 0000:01:04.2: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    8.483688] bnx2 0000:02:00.1: firmware: requesting bnx2/bnx2-rv2p-09-5.0.0.j3.fw
[    8.487119] eth1: Broadcom NetXtreme II BCM5709 1000Base-T (C0) PCI Express found at mem f2000000, IRQ 17, node addr d8:d3:85:aa:bd:bc
[    8.487154]   alloc irq_desc for 18 on node -1
[    8.487158]   alloc kstat_irqs on node -1
[    8.487167] bnx2 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.487177] bnx2 0000:03:00.0: setting latency timer to 64
[    8.487356] bnx2 0000:03:00.0: firmware: requesting bnx2/bnx2-mips-09-5.0.0.j3.fw
[    8.487513] IPMI System Interface driver.
[    8.487520] ipmi_si: Trying SMBIOS-specified kcs state machine at i/o address 0xca2, slave address 0x20, irq 0
[    8.489425] bnx2 0000:03:00.0: firmware: requesting bnx2/bnx2-rv2p-09-5.0.0.j3.fw
[    8.491867] eth2: Broadcom NetXtreme II BCM5709 1000Base-T (C0) PCI Express found at mem f8000000, IRQ 18, node addr d8:d3:85:aa:bd:be
[    8.491898]   alloc irq_desc for 19 on node -1
[    8.491900]   alloc kstat_irqs on node -1
[    8.491906] bnx2 0000:03:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    8.491913] bnx2 0000:03:00.1: setting latency timer to 64
[    8.492096] bnx2 0000:03:00.1: firmware: requesting bnx2/bnx2-mips-09-5.0.0.j3.fw
[    8.497372] bnx2 0000:03:00.1: firmware: requesting bnx2/bnx2-rv2p-09-5.0.0.j3.fw
[    8.501433] eth3: Broadcom NetXtreme II BCM5709 1000Base-T (C0) PCI Express found at mem f6000000, IRQ 19, node addr d8:d3:85:aa:bd:c0
[    8.515558] type=1505 audit(1281858606.212:2):  operation="profile_load" pid=729 name="/sbin/dhclient3"
[    8.516088] type=1505 audit(1281858606.222:3):  operation="profile_load" pid=729 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    8.516384] type=1505 audit(1281858606.222:4):  operation="profile_load" pid=729 name="/usr/lib/connman/scripts/dhclient-script"
[    8.524603] [drm] radeon disabling kernel modesetting for known bad device.
[    8.524802] pci 0000:01:03.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    8.524936] [drm] Initialized radeon 1.32.0 20080528 for 0000:01:03.0 on minor 0
[    8.525854]   alloc irq_desc for 64 on node -1
[    8.525858]   alloc kstat_irqs on node -1
[    8.525864] bnx2 0000:02:00.1: irq 64 for MSI/MSI-X
[    8.525866]   alloc irq_desc for 65 on node -1
[    8.525868]   alloc kstat_irqs on node -1
[    8.525871] bnx2 0000:02:00.1: irq 65 for MSI/MSI-X
[    8.525874]   alloc irq_desc for 66 on node -1
[    8.525876]   alloc kstat_irqs on node -1
[    8.525879] bnx2 0000:02:00.1: irq 66 for MSI/MSI-X
[    8.525881]   alloc irq_desc for 67 on node -1
[    8.525883]   alloc kstat_irqs on node -1
[    8.525886] bnx2 0000:02:00.1: irq 67 for MSI/MSI-X
[    8.525888]   alloc irq_desc for 68 on node -1
[    8.525890]   alloc kstat_irqs on node -1
[    8.525894] bnx2 0000:02:00.1: irq 68 for MSI/MSI-X
[    8.525896]   alloc irq_desc for 69 on node -1
[    8.525898]   alloc kstat_irqs on node -1
[    8.525901] bnx2 0000:02:00.1: irq 69 for MSI/MSI-X
[    8.525903]   alloc irq_desc for 70 on node -1
[    8.525905]   alloc kstat_irqs on node -1
[    8.525908] bnx2 0000:02:00.1: irq 70 for MSI/MSI-X
[    8.525910]   alloc irq_desc for 71 on node -1
[    8.525912]   alloc kstat_irqs on node -1
[    8.525915] bnx2 0000:02:00.1: irq 71 for MSI/MSI-X
[    8.525918]   alloc irq_desc for 72 on node -1
[    8.525919]   alloc kstat_irqs on node -1
[    8.525923] bnx2 0000:02:00.1: irq 72 for MSI/MSI-X
[    8.527015] vga16fb: initializing
[    8.527018] vga16fb: mapped to 0xffff8800000a0000
[    8.527065] fb0: VGA16 VGA frame buffer device
[    8.606456] bnx2: eth1: using MSIX
[    8.607118] ADDRCONF(NETDEV_UP): eth1: link is not ready
[    8.728036] Console: switching to colour frame buffer device 80x30
[    8.829101] type=1505 audit(1281858606.532:5):  operation="profile_replace" pid=879 name="/sbin/dhclient3"
[    8.829754] type=1505 audit(1281858606.532:6):  operation="profile_replace" pid=879 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    8.830109] type=1505 audit(1281858606.532:7):  operation="profile_replace" pid=879 name="/usr/lib/connman/scripts/dhclient-script"
[    8.838089] type=1505 audit(1281858606.542:8):  operation="profile_load" pid=880 name="/usr/sbin/mysqld"
[    8.840008] type=1505 audit(1281858606.542:9):  operation="profile_load" pid=888 name="/usr/sbin/tcpdump"
[    8.857564] type=1505 audit(1281858606.562:10):  operation="profile_replace" pid=901 name="/usr/sbin/mysqld"
[    8.879342] ipmi: Found new BMC (man_id: 0x00000b,  prod_id: 0x0000, dev_id: 0x11)
[    8.879351] IPMI kcs interface initialized
[    8.879363] ipmi_si: Trying ACPI-specified kcs state machine at i/o address 0xca2, slave address 0x0, irq 0
[    8.879365] ipmi_si: duplicate interface
[    8.914899]   alloc irq_desc for 21 on node -1
[    8.914902]   alloc kstat_irqs on node -1
[    8.914910] ipmi_si 0000:01:04.6: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    8.914913] ipmi_si: Trying PCI-specified kcs state machine at mem address 0xf1ef0000, slave address 0x0, irq 21

```

---

### Post by fzaker on 2010-10-01
Still having the same problem. I could not enable boot logging by setting BOOTLOGD_ENABLE to yes in /etc/default/bootlogd. /var/log/boot is always empty.
In addition, contents of files in /var/log/ folder in several boots are identical, with no change!
I don't know how to trace the problem. really confused, somebody please help me.

---

### Post by andrewthomas on 2010-10-01
> **fzaker said:**
> Still having the same problem. I could not enable boot logging by setting BOOTLOGD_ENABLE to yes in /etc/default/bootlogd.** /var/log/boot is always empty**.
In addition, contents of files in /var/log/ folder in several boots are identical, with no change!
I don't know how to trace the problem. really confused, somebody please help me.
**bootlogd will send the log to /var/log/boot.log**

---

### Post by 666f6f on 2010-10-03
> **andrewthomas said:**
> **bootlogd will send the log to /var/log/boot.log**

This is a little inaccurate.

**bootlogd by default logs to /var/log/boot. Usually that file either it does not exist or it is empty.** Why? Because, even if you set BOOTLOGD_ENABLED in /etc/default/bootlogd, **bootlogd is never started at boot**. 

[This bug report]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/125710") (which is invalid) proves the above claim to be correct. But why the bug report is invalid?

Because boot messages are logged in /var/log/boot.log. Who writes it? Well, in some Linux distributions (not sure about previous versions of Ubuntu) it was syslog/ryslogd that logged boot messages there. In Ubuntu Lucid Lynx 10.04 it is Plymouth that logs boot messages there.

Ninja geeks can find out themselves with basic command line fu.```
apt-get source plymouth sysvinit-utils rsyslog && grep -r /var/log/boot plymouth* sysvinit* rsyslog*
```.

**UPDATE**: You can however enable bootlogd by doing ```
ln -s /etc/init.d/bootlogd /etc/rcS.d/S03bootlogd
ln -s /etc/init.d/stop-bootlogd /etc/rc2.d/S99stop-bootlogd
```, and setting BOOTLOGD_ENABLE=yes [like this thread]("http://ubuntuforums.org/showthread.php?t=811005") suggests.

Also, you can change VERBOSE variable from no to yes in /etc/default/rcS to have more messages during the boot process, or less if you enter no.

---

### Post by fzaker on 2010-10-04
> **666f6f said:**
> 
**UPDATE**: You can however enable bootlogd by doing ```
ln -s /etc/init.d/bootlogd /etc/rcS.d/S03bootlogd
ln -s /etc/init.d/stop-bootlogd /etc/rc2.d/S99stop-bootlogd
```, and setting BOOTLOGD_ENABLE=yes [like this thread]("http://ubuntuforums.org/showthread.php?t=811005") suggests.

Also, you can change VERBOSE variable from no to yes in /etc/default/rcS to have more messages during the boot process, or less if you enter no.

as a newbie, I need to know when a computer does not boot up, how could I run those commands?

---

### Post by andrewthomas on 2010-10-04
> **fzaker said:**
> as a newbie, I need to know when a computer does not boot up, how could I run those commands?
preface the commands with sudo

---

### Post by ravenpi on 2011-11-08
Boy, that was just a less-than-useful reply, there.  If he's hanging, he wants to be able to figure out how to even get to a command-line prompt.  Sadly, this is almost certainly too late for the original poster, but here goes:

1) You can boot off of external media (e.g., an Ubuntu live CD), or
2) Cheat: <alt><sysrq><k> -- this will kill whatever process is currently in the foreground.  (The SysRq key is the one up by printscreen.)  What this will likely do is then dump you to a prompt.  More than likely, your filesystem may be read-only at this point; you can make it read-write by doing a
mount -o remount,rw /
From there, you'll be able to use the stock command-line tools (vi, emacs, bash commands, etc.) to implement the suggestions already mentioned.

Note that you will also almost certainly be unable to do a stock "reboot," as various necessary elements are missing.  Instead, <alt><sysrq> to the rescue again:
<alt><sysrq><s>  -- Sync the unwritten data to disk
<alt><sysrq><u>  -- Do an emergency Unmount to read-only
<alt><sysrq><b>  -- Pull the power (via ACPI), and do a Boot


Good luck!

-Ken

---

