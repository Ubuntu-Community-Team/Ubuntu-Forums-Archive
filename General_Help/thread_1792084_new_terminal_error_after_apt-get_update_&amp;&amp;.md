---
title: "new terminal error after apt-get update &amp;&amp; sudo apt-get upgrade"
date: 2011-06-27
forum: General Help
---

### Post by maizuddin35 on 2011-06-27
Hello guys, everyone, anyone.. :)

I updated and upgraded my ubuntu like always, sudo apt-get update && sudo apt-get upgrade, and this time I think , they updated the kernel or something, I really don't understand, what is the problem just by looking the text/command error in the terminal . 

can anyone look at my output error ? and tell me what is wrong with it. by the way, im using Elementary OS that based on Ubuntu . and I also update my graphic driver manually by downloading the driver from the nvidia website. 



```
Current status: 5 updates [+1], 100 new [+1].
Resolving dependencies...                
The following NEW packages will be installed:
  linux-headers-2.6.35-30{a} linux-headers-2.6.35-30-generic{a} 
  linux-image-2.6.35-30-generic{a} 
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic linux-libc-dev 
  wingpanel 
5 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 45.9MB of archives. After unpacking 198MB will be used.
Do you want to continue? [Y/n/?] y
Get:1 http://ppa.launchpad.net/elementaryart/elementary-dev/ubuntu/ maverick/main wingpanel i386 0.0.1+r68-0~maverick1 [18.9kB]
Get:2 http://archive.ubuntu.com/ubuntu/ maverick-updates/main linux-image-2.6.35-30-generic i386 2.6.35-30.54 [33.9MB]
Get:3 http://archive.ubuntu.com/ubuntu/ maverick-updates/main linux-generic i386 2.6.35.30.38 [5,546B]
Get:4 http://archive.ubuntu.com/ubuntu/ maverick-updates/main linux-image-generic i386 2.6.35.30.38 [5,552B]
Get:5 http://archive.ubuntu.com/ubuntu/ maverick-updates/main linux-headers-2.6.35-30 all 2.6.35-30.54 [10.3MB]
Get:6 http://archive.ubuntu.com/ubuntu/ maverick-updates/main linux-headers-2.6.35-30-generic i386 2.6.35-30.54 [802kB]
Get:7 http://archive.ubuntu.com/ubuntu/ maverick-updates/main linux-headers-generic i386 2.6.35.30.38 [5,542B]
Get:8 http://archive.ubuntu.com/ubuntu/ maverick-updates/main linux-libc-dev i386 2.6.35-1030.54 [826kB]
Fetched 45.9MB in 15min 20s (49.9kB/s)                                          
Selecting previously deselected package linux-image-2.6.35-30-generic.
(Reading database ... 145870 files and directories currently installed.)
Unpacking linux-image-2.6.35-30-generic (from .../linux-image-2.6.35-30-generic_2.6.35-30.54_i386.deb) ...
Done.
Preparing to replace linux-generic 2.6.35.28.36 (using .../linux-generic_2.6.35.30.38_i386.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 2.6.35.28.36 (using .../linux-image-generic_2.6.35.30.38_i386.deb) ...
Unpacking replacement linux-image-generic ...
Selecting previously deselected package linux-headers-2.6.35-30.
Unpacking linux-headers-2.6.35-30 (from .../linux-headers-2.6.35-30_2.6.35-30.54_all.deb) ...
Selecting previously deselected package linux-headers-2.6.35-30-generic.
Unpacking linux-headers-2.6.35-30-generic (from .../linux-headers-2.6.35-30-generic_2.6.35-30.54_i386.deb) ...
Preparing to replace linux-headers-generic 2.6.35.28.36 (using .../linux-headers-generic_2.6.35.30.38_i386.deb) ...
Unpacking replacement linux-headers-generic ...
Preparing to replace linux-libc-dev 2.6.35-1028.50 (using .../linux-libc-dev_2.6.35-1030.54_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace wingpanel 0.0.1+r67-0~maverick1 (using .../wingpanel_0.0.1+r68-0~maverick1_i386.deb) ...
Unpacking replacement wingpanel ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up linux-image-2.6.35-30-generic (2.6.35-30.54) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-30-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
 * dkms: running auto installation service for kernel 2.6.35-30-generic         
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
 *       nvidia-current (260.19.06)...                                   [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-30-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-30-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-30-generic; however:
  Package linux-image-2.6.35-30-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.30.38); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.35-30 (2.6.35-30.54) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Setting up linux-headers-2.6.35-30-generic (2.6.35-30.54) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
 * dkms: running auto installation service for kernel 2.6.35-30-generic         
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
 *       nvidia-current (260.19.06)...                                   [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
Setting up linux-headers-generic (2.6.35.30.38) ...
Setting up linux-libc-dev (2.6.35-1030.54) ...
Setting up wingpanel (0.0.1+r68-0~maverick1) ...
Errors were encountered while processing:
 linux-image-2.6.35-30-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.35-30-generic (2.6.35-30.54) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-30-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
 * dkms: running auto installation service for kernel 2.6.35-30-generic         
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
 *       nvidia-current (260.19.06)...                                   [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-30-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-30-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-30-generic; however:
  Package linux-image-2.6.35-30-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.30.38); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.35-30-generic
 linux-image-generic
 linux-generic

```

Your help is greatly appreciated :)

---

### Post by doas777 on 2011-06-27
looks like it thinks somthing is wrong with your /etc/default/grub file on line 23. it wants it to end on a newline.
then run:
```
sudo update-grub
```

I would open that file, and on the last line, hit enter. then save and try the udate/upgrade again.
if it still doesn't work, check this out:
[http://ubuntuforums.org/archive/index.php/t-1601558.html](http://ubuntuforums.org/archive/index.php/t-1601558.html)
seems to be the same issue.

---

### Post by maizuddin35 on 2011-06-27
do you mean , open the "grub" file, and enter at the last line? I do that already , and I see , like its nothing there, that act as a problem. I'm not that sure....by the way ..thank you ;)

---

### Post by doas777 on 2011-06-27
are you saying that if you enter:
```
sudo nano /etc/default/grub
```there is nothing in the file?

---

### Post by maizuddin35 on 2011-06-27
it seems that , it want to update from 

```
linux-image-2.6.35-
linux-image-2.6.35-28-generic_2.6.35-28
``` to 

```
linux-image-2.6.35-30-generic_2.6.35-30
```

---

### Post by maizuddin35 on 2011-06-27
I don't actually know, where to Enter the new line...
can you show me how, and where, thanks..

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=>>1440x900-24<<,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=>>1440x900-24<<

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

here is , in the grub file. where should I do it?

---

### Post by doas777 on 2011-06-27
ok good, I think I see the problem.

change this line:
```
GRUB_GFXMODE=>>1024x768-24<<
```
to
```
GRUB_GFXMODE=1024x768x24
```
then save your file (if you are using nano, hit ctrl+x ) and run:
```
sudo update-grub
```

then try your upgrade again.

---

### Post by maizuddin35 on 2011-06-27
ahhhh, I think , the problem fix now. I run apt-get update and upgrade again , and it look just fine, thank you for helping me out. 

just curious , how in the hell , that , That line, become like that , eyh...?haha,

---

### Post by doas777 on 2011-06-27
no idea. this guys seen it before too:[http://ubuntuforums.org/archive/index.php/t-1601558.html](http://ubuntuforums.org/archive/index.php/t-1601558.html)

---

### Post by maizuddin35 on 2011-06-27
yeah , seem to be that way. still, the problem is fix and thank you very much :)

---

### Post by maizuddin35 on 2011-06-28
this aint finish yet! After I reboot the computer, in the grub loader , there is only (recovery mode) and there are TWO recovery mode one is

linux-image-2.6.35-30-generic_2.6.35-30
and another one , is this one...

linux-image-2.6.35-28-generic_2.6.35-28
now I can't get into my desktop computer....:((

---

### Post by doas777 on 2011-06-28
> **maizuddin35 said:**
> this aint finish yet! After I reboot the computer, in the grub loader , there is only (recovery mode) and there are TWO recovery mode one is

linux-image-2.6.35-30-generic_2.6.35-30
and another one , is this one...

linux-image-2.6.35-28-generic_2.6.35-28
now I can't get into my desktop computer....:((
boot in recovery mode, and look at /var/log/dmesg.0.log. it contians info about your last boot, and hopefully will give us hints as to what the problem was.

---

### Post by maizuddin35 on 2011-06-28
hello again, thank you for helping me out...

okey...there is no dmesg.0.log file.
here is the output from cd /var/log/

```
ubuntu@ubuntu:/var/log$ ls
alternatives.log  cups            installer         speech-dispatcher
apparmor          dist-upgrade    jockey.log        syslog
apt               dmesg           kern.log          udev
auth.log          dmesg.0         lastlog           ufw.log
boot              dmesg.1.gz      mail.err          unattended-upgrades
boot.log          dpkg.log        mail.log          wtmp
bootstrap.log     faillog         news              Xorg.0.log
btmp              fontconfig.log  pm-powersave.log  Xorg.0.log.old
casper.log        fsck            pycentral.log
ConsoleKit        gdm             samba

```

but there is [B]dmesg.0

[/B]and here is what inside that **dmesg.0**

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dff90000 (usable)
[    0.000000]  BIOS-e820: 00000000dff90000 - 00000000dff9e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dff9e000 - 00000000dffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dffd0000 - 00000000dffde000 (reserved)
[    0.000000]  BIOS-e820: 00000000dffe0000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: System manufacturer System Product Name/P5KPL/EPU, BIOS 0403    06/17/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xdff90 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-protect
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FE0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 7f33b000 - 80000000
[    0.000000] Allocated new RAMDISK: 36b39000 - 377fd9b3
[    0.000000] Move RAMDISK from 000000007f33b000 - 000000007ffff9b2 to 36b39000 - 377fd9b2
[    0.000000] ACPI: RSDP 000fb810 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT dff90100 0004C (v01 061709 XSDT1538 20090617 MSFT 00000097)
[    0.000000] ACPI: FACP dff90290 000F4 (v03 061709 FACP1538 20090617 MSFT 00000097)
[    0.000000] ACPI: DSDT dff905c0 06611 (v01  A1189 A1189000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS dff9e000 00040
[    0.000000] ACPI: APIC dff90390 0006C (v01 061709 APIC1538 20090617 MSFT 00000097)
[    0.000000] ACPI: MCFG dff90400 0003C (v01 061709 OEMMCFG  20090617 MSFT 00000097)
[    0.000000] ACPI: OEMB dff9e040 00061 (v01 061709 OEMB1538 20090617 MSFT 00000097)
[    0.000000] ACPI: HPET dff96be0 00038 (v01 061709 OEMHPET  20090617 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2695MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000dff90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000dff90
[    0.000000] On node 0 totalpages: 917279
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f4f38200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 5392 pages used for memmap
[    0.000000]   HighMem zone: 684674 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:1ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f4800000 s28800 r0 d24448 u1048576
[    0.000000] pcpu-alloc: s28800 r0 d24448 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 910111
[    0.000000] Kernel command line: noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 18347520 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000dff90)
[    0.000000] Memory: 3599004k/3669568k available (5188k kernel code, 70112k reserved, 2540k data, 700k init, 2760264k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f3008000 soft=f300a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2000.046 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4000.09 BogoMIPS (lpj=8000184)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004034] Security Framework initialized
[    0.004049] AppArmor: AppArmor initialized
[    0.004051] Yama: becoming mindful.
[    0.004111] Mount-cache hash table entries: 512
[    0.004254] Initializing cgroup subsys ns
[    0.004259] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004262] Initializing cgroup subsys cpuacct
[    0.004268] Initializing cgroup subsys memory
[    0.004277] Initializing cgroup subsys devices
[    0.004280] Initializing cgroup subsys freezer
[    0.004282] Initializing cgroup subsys net_cls
[    0.004284] Initializing cgroup subsys blkio
[    0.004323] CPU: Physical Processor ID: 0
[    0.004325] CPU: Processor Core ID: 0
[    0.004328] mce: CPU supports 6 MCE banks
[    0.004336] CPU0: Thermal monitoring enabled (TM2)
[    0.004340] using mwait in idle threads.
[    0.009304] ACPI: Core revision 20110112
[    0.016013] ftrace: allocating 23640 entries in 47 pages
[    0.020061] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.020370] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.067695] CPU0: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz stepping 0d
[    0.068003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.068003] PEBS disabled due to CPU errata.
[    0.068003] ... version:                2
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] CPU 1 irqstacks, hard=f30b2000 soft=f30b4000
[    0.068003] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.156028] Brought up 2 CPUs
[    0.156032] Total of 2 processors activated (8000.07 BogoMIPS).
[    0.156469] devtmpfs: initialized
[    0.157288] print_constraints: dummy: 
[    0.157314] Time: 20:05:54  Date: 06/28/11
[    0.157359] NET: Registered protocol family 16
[    0.157399] Trying to unpack rootfs image as initramfs...
[    0.157506] EISA bus registered
[    0.157517] ACPI: bus type pci registered
[    0.157598] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.157601] PCI: not using MMCONFIG
[    0.157762] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.157764] PCI: Using configuration type 1 for base access
[    1.156208] bio: create slab <bio-0> at 0
[    1.157829] ACPI: EC: Look up EC in DSDT
[    1.159517] ACPI: Executed 1 blocks of module-level executable AML code
[    1.162986] ACPI: SSDT dff9e0b0 00214 (v01    AMI   CPU1PM 00000001 INTL 20060113)
[    1.163363] ACPI: Dynamic OEM Table Load:
[    1.163367] ACPI: SSDT   (null) 00214 (v01    AMI   CPU1PM 00000001 INTL 20060113)
[    1.163595] ACPI: SSDT dff9e2d0 00143 (v01    AMI   CPU2PM 00000001 INTL 20060113)
[    1.163964] ACPI: Dynamic OEM Table Load:
[    1.163968] ACPI: SSDT   (null) 00143 (v01    AMI   CPU2PM 00000001 INTL 20060113)
[    1.164301] ACPI: Interpreter enabled
[    1.164311] ACPI: (supports S0 S1 S3 S4 S5)
[    1.164338] ACPI: Using IOAPIC for interrupt routing
[    1.164366] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    1.165776] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in ACPI motherboard resources
[    1.165778] PCI: Using MMCONFIG for extended config space
[    1.172680] ACPI: No dock devices found.
[    1.172682] HEST: Table not found.
[    1.172688] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.172767] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    1.172938] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.172942] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.172945] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.172947] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    1.172950] pci_root PNP0A08:00: host bridge window [mem 0xe0000000-0xffffffff]
[    1.172966] pci 0000:00:00.0: [8086:29c0] type 0 class 0x000600
[    1.173019] pci 0000:00:01.0: [8086:29c1] type 1 class 0x000604
[    1.173059] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.173063] pci 0000:00:01.0: PME# disabled
[    1.173111] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    1.173129] pci 0000:00:1b.0: reg 10: [mem 0xf9ffc000-0xf9ffffff 64bit]
[    1.173189] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.173193] pci 0000:00:1b.0: PME# disabled
[    1.173214] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    1.173275] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.173279] pci 0000:00:1c.0: PME# disabled
[    1.173304] pci 0000:00:1c.3: [8086:27d6] type 1 class 0x000604
[    1.173365] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.173369] pci 0000:00:1c.3: PME# disabled
[    1.173393] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    1.173437] pci 0000:00:1d.0: reg 20: [io  0xc480-0xc49f]
[    1.173469] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    1.173513] pci 0000:00:1d.1: reg 20: [io  0xc800-0xc81f]
[    1.173544] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    1.173588] pci 0000:00:1d.2: reg 20: [io  0xc880-0xc89f]
[    1.173619] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    1.173663] pci 0000:00:1d.3: reg 20: [io  0xcc00-0xcc1f]
[    1.173704] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    1.173725] pci 0000:00:1d.7: reg 10: [mem 0xf9ffbc00-0xf9ffbfff]
[    1.173799] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.173804] pci 0000:00:1d.7: PME# disabled
[    1.173823] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    1.173885] pci 0000:00:1f.0: [8086:27b8] type 0 class 0x000601
[    1.173972] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
[    1.174008] pci 0000:00:1f.1: [8086:27df] type 0 class 0x000101
[    1.174023] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    1.174033] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    1.174043] pci 0000:00:1f.1: reg 18: [io  0x08f0-0x08f7]
[    1.174053] pci 0000:00:1f.1: reg 1c: [io  0x08f8-0x08fb]
[    1.174064] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
[    1.174100] pci 0000:00:1f.2: [8086:27c0] type 0 class 0x000101
[    1.174115] pci 0000:00:1f.2: reg 10: [io  0xc400-0xc407]
[    1.174124] pci 0000:00:1f.2: reg 14: [io  0xc080-0xc083]
[    1.174133] pci 0000:00:1f.2: reg 18: [io  0xc000-0xc007]
[    1.174142] pci 0000:00:1f.2: reg 1c: [io  0xbc00-0xbc03]
[    1.174151] pci 0000:00:1f.2: reg 20: [io  0xb880-0xb88f]
[    1.174183] pci 0000:00:1f.2: PME# supported from D3hot
[    1.174187] pci 0000:00:1f.2: PME# disabled
[    1.174203] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    1.174258] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    1.174336] pci 0000:01:00.0: [10de:0640] type 0 class 0x000300
[    1.174348] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    1.174361] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    1.174374] pci 0000:01:00.0: reg 1c: [mem 0xfa000000-0xfbffffff 64bit]
[    1.174383] pci 0000:01:00.0: reg 24: [io  0xdc00-0xdc7f]
[    1.174392] pci 0000:01:00.0: reg 30: [mem 0xfea80000-0xfeafffff pref]
[    1.174445] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.174449] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    1.174453] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfeafffff]
[    1.174459] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    1.174502] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
[    1.174507] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.174512] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.174519] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.174580] pci 0000:02:00.0: [10ec:8168] type 0 class 0x000200
[    1.174599] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
[    1.174629] pci 0000:02:00.0: reg 18: [mem 0xf8fff000-0xf8ffffff 64bit pref]
[    1.174649] pci 0000:02:00.0: reg 20: [mem 0xf8fe0000-0xf8feffff 64bit pref]
[    1.174663] pci 0000:02:00.0: reg 30: [mem 0xfebf0000-0xfebfffff pref]
[    1.174705] pci 0000:02:00.0: supports D1 D2
[    1.174707] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.174713] pci 0000:02:00.0: PME# disabled
[    1.180090] pci 0000:00:1c.3: PCI bridge to [bus 02-02]
[    1.180095] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    1.180099] pci 0000:00:1c.3:   bridge window [mem 0xfeb00000-0xfebfffff]
[    1.180106] pci 0000:00:1c.3:   bridge window [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    1.180174] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    1.180179] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.180184] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.180191] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.180194] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.180197] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.180200] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.180203] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    1.180206] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xffffffff] (subtractive decode)
[    1.180224] pci_bus 0000:00: on NUMA node 0
[    1.180228] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.180378] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.180521] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    1.180574] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    1.180625]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.187070] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    1.187130] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.187188] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    1.187248] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    1.187305] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.187363] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.187424] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.187482] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    1.187620] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.187624] vgaarb: loaded
[    1.187865] SCSI subsystem initialized
[    1.187935] libata version 3.00 loaded.
[    1.187994] usbcore: registered new interface driver usbfs
[    1.188008] usbcore: registered new interface driver hub
[    1.188040] usbcore: registered new device driver usb
[    1.188186] wmi: Mapper loaded
[    1.188189] PCI: Using ACPI for IRQ routing
[    1.188194] PCI: pci_cache_line_size set to 64 bytes
[    1.188269] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    1.188272] reserve RAM buffer: 00000000dff90000 - 00000000dfffffff 
[    1.188395] NetLabel: Initializing
[    1.188398] NetLabel:  domain hash size = 128
[    1.188399] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.188412] NetLabel:  unlabeled traffic allowed by default
[    1.188456] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    1.188461] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.188467] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    2.572242] Switching to clocksource hpet
[    2.576019] Switched to NOHz mode on CPU #0
[    2.576033] Switched to NOHz mode on CPU #1
[    2.583003] AppArmor: AppArmor Filesystem Enabled
[    2.583057] pnp: PnP ACPI init
[    2.583093] ACPI: bus type pnp registered
[    2.583240] pnp 00:00: [bus 00-ff]
[    2.583244] pnp 00:00: [io  0x0cf8-0x0cff]
[    2.583247] pnp 00:00: [io  0x0000-0x0cf7 window]
[    2.583250] pnp 00:00: [io  0x0d00-0xffff window]
[    2.583253] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    2.583256] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    2.583259] pnp 00:00: [mem 0xe0000000-0xffffffff window]
[    2.583368] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    2.583382] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    2.583454] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    2.583459] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    2.583508] pnp 00:02: [dma 4]
[    2.583510] pnp 00:02: [io  0x0000-0x000f]
[    2.583513] pnp 00:02: [io  0x0081-0x0083]
[    2.583515] pnp 00:02: [io  0x0087]
[    2.583517] pnp 00:02: [io  0x0089-0x008b]
[    2.583520] pnp 00:02: [io  0x008f]
[    2.583522] pnp 00:02: [io  0x00c0-0x00df]
[    2.583570] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    2.583584] pnp 00:03: [io  0x0070-0x0071]
[    2.583602] pnp 00:03: [irq 8]
[    2.583650] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    2.583662] pnp 00:04: [io  0x0061]
[    2.583698] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    2.583709] pnp 00:05: [io  0x00f0-0x00ff]
[    2.583717] pnp 00:05: [irq 13]
[    2.583753] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    2.584322] pnp 00:06: [irq 7]
[    2.584327] pnp 00:06: [dma 3]
[    2.584330] pnp 00:06: [io  0x0378-0x037f]
[    2.584332] pnp 00:06: [io  0x0778-0x077f]
[    2.584586] pnp 00:06: Plug and Play ACPI device, IDs PNP0401 (active)
[    2.584649] pnp 00:07: [io  0x0000-0xffffffff disabled]
[    2.584652] pnp 00:07: [io  0x0000-0xffffffff disabled]
[    2.584655] pnp 00:07: [io  0x0290-0x0297]
[    2.584742] system 00:07: [io  0x0290-0x0297] has been reserved
[    2.584747] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.584849] pnp 00:08: [io  0x0010-0x001f]
[    2.584852] pnp 00:08: [io  0x0022-0x003f]
[    2.584855] pnp 00:08: [io  0x0044-0x005f]
[    2.584857] pnp 00:08: [io  0x0062-0x0063]
[    2.584860] pnp 00:08: [io  0x0065-0x006f]
[    2.584862] pnp 00:08: [io  0x0072-0x007f]
[    2.584864] pnp 00:08: [io  0x0080]
[    2.584867] pnp 00:08: [io  0x0084-0x0086]
[    2.584869] pnp 00:08: [io  0x0088]
[    2.584871] pnp 00:08: [io  0x008c-0x008e]
[    2.584874] pnp 00:08: [io  0x0090-0x009f]
[    2.584876] pnp 00:08: [io  0x00a2-0x00bf]
[    2.584878] pnp 00:08: [io  0x00e0-0x00ef]
[    2.584881] pnp 00:08: [io  0x04d0-0x04d1]
[    2.584883] pnp 00:08: [io  0x0800-0x087f]
[    2.584886] pnp 00:08: [io  0x0000-0xffffffff disabled]
[    2.584888] pnp 00:08: [io  0x0480-0x04bf]
[    2.584891] pnp 00:08: [mem 0xfed1c000-0xfed1ffff]
[    2.584893] pnp 00:08: [mem 0xfed20000-0xfed8ffff]
[    2.584984] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    2.584988] system 00:08: [io  0x0800-0x087f] has been reserved
[    2.584991] system 00:08: [io  0x0480-0x04bf] has been reserved
[    2.584995] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    2.584999] system 00:08: [mem 0xfed20000-0xfed8ffff] has been reserved
[    2.585003] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.585110] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    2.585166] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    2.585236] pnp 00:0a: [mem 0xffb00000-0xffbfffff]
[    2.585240] pnp 00:0a: [mem 0xfff00000-0xffffffff]
[    2.585286] pnp 00:0a: Plug and Play ACPI device, IDs INT0800 (active)
[    2.585339] pnp 00:0b: [mem 0xffc00000-0xffefffff]
[    2.585406] system 00:0b: [mem 0xffc00000-0xffefffff] has been reserved
[    2.585410] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.585472] pnp 00:0c: [mem 0xfec00000-0xfec00fff]
[    2.585475] pnp 00:0c: [mem 0xfee00000-0xfee00fff]
[    2.585539] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    2.585543] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    2.585546] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.585589] pnp 00:0d: [io  0x0060]
[    2.585591] pnp 00:0d: [io  0x0064]
[    2.585605] pnp 00:0d: [irq 1]
[    2.585652] pnp 00:0d: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    2.586015] pnp 00:0e: [irq 4]
[    2.586019] pnp 00:0e: [dma 0 disabled]
[    2.586022] pnp 00:0e: [io  0x03f8-0x03ff]
[    2.586134] pnp 00:0e: Plug and Play ACPI device, IDs PNP0501 (active)
[    2.586183] pnp 00:0f: [mem 0xf0000000-0xf3ffffff]
[    2.586260] system 00:0f: [mem 0xf0000000-0xf3ffffff] has been reserved
[    2.586264] system 00:0f: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.586483] pnp 00:10: [mem 0x00000000-0x0009ffff]
[    2.586487] pnp 00:10: [mem 0x000c0000-0x000cffff]
[    2.586489] pnp 00:10: [mem 0x000e0000-0x000fffff]
[    2.586492] pnp 00:10: [mem 0x00100000-0xdfffffff]
[    2.586495] pnp 00:10: [mem 0x00000000-0xffffffff disabled]
[    2.586586] system 00:10: [mem 0x00000000-0x0009ffff] could not be reserved
[    2.586590] system 00:10: [mem 0x000c0000-0x000cffff] could not be reserved
[    2.586593] system 00:10: [mem 0x000e0000-0x000fffff] could not be reserved
[    2.586596] system 00:10: [mem 0x00100000-0xdfffffff] could not be reserved
[    2.586600] system 00:10: Plug and Play ACPI device, IDs PNP0c01 (active)
[    2.586769] pnp: PnP ACPI: found 17 devices
[    2.586772] ACPI: ACPI bus type pnp unregistered
[    2.586778] PnPBIOS: Disabled by ACPI PNP
[    2.623794] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf4000000-0xf41fffff]
[    2.623800] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf4200000-0xf43fffff 64bit pref]
[    2.623805] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    2.623808] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    2.623811] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    2.623816] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfeafffff]
[    2.623820] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    2.623826] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
[    2.623829] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    2.623834] pci 0000:00:1c.0:   bridge window [mem 0xf4000000-0xf41fffff]
[    2.623839] pci 0000:00:1c.0:   bridge window [mem 0xf4200000-0xf43fffff 64bit pref]
[    2.623846] pci 0000:00:1c.3: PCI bridge to [bus 02-02]
[    2.623850] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    2.623855] pci 0000:00:1c.3:   bridge window [mem 0xfeb00000-0xfebfffff]
[    2.623860] pci 0000:00:1c.3:   bridge window [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    2.623867] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    2.623869] pci 0000:00:1e.0:   bridge window [io  disabled]
[    2.623874] pci 0000:00:1e.0:   bridge window [mem disabled]
[    2.623878] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    2.623907] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.623912] pci 0000:00:01.0: setting latency timer to 64
[    2.623919] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    2.623924] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.623928] pci 0000:00:1c.0: setting latency timer to 64
[    2.623939] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.623944] pci 0000:00:1c.3: setting latency timer to 64
[    2.623951] pci 0000:00:1e.0: setting latency timer to 64
[    2.623955] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    2.623958] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    2.623961] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.623963] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    2.623966] pci_bus 0000:00: resource 8 [mem 0xe0000000-0xffffffff]
[    2.623969] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    2.623972] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfeafffff]
[    2.623975] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    2.623977] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    2.623980] pci_bus 0000:03: resource 1 [mem 0xf4000000-0xf41fffff]
[    2.623983] pci_bus 0000:03: resource 2 [mem 0xf4200000-0xf43fffff 64bit pref]
[    2.623986] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    2.623989] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    2.623992] pci_bus 0000:02: resource 2 [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    2.624022] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    2.624025] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    2.624027] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    2.624030] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    2.624033] pci_bus 0000:04: resource 8 [mem 0xe0000000-0xffffffff]
[    2.624086] NET: Registered protocol family 2
[    2.624175] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    2.624450] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.624862] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    2.625178] TCP: Hash tables configured (established 131072 bind 65536)
[    2.625181] TCP reno registered
[    2.625185] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    2.625196] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    2.625336] NET: Registered protocol family 1
[    2.625483] pci 0000:01:00.0: Boot video device
[    2.625491] PCI: CLS 32 bytes, default 64
[    2.625768] cpufreq-nforce2: No nForce2 chipset.
[    2.625921] audit: initializing netlink socket (disabled)
[    2.625934] type=2000 audit(1309291555.620:1): initialized
[    3.180148] highmem bounce pool size: 64 pages
[    3.180157] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    3.182546] VFS: Disk quotas dquot_6.5.2
[    3.182650] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.183582] fuse init (API version 7.16)
[    3.183726] msgmni has been set to 1638
[    3.184142] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    3.184187] io scheduler noop registered
[    3.184190] io scheduler deadline registered
[    3.184215] io scheduler cfq registered (default)
[    3.184377] pcieport 0000:00:01.0: setting latency timer to 64
[    3.184423] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    3.184509] pcieport 0000:00:1c.0: setting latency timer to 64
[    3.184559] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    3.184641] pcieport 0000:00:1c.3: setting latency timer to 64
[    3.184690] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    3.184801] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.184838] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.184926] intel_idle: MWAIT substates: 0x220
[    3.184929] intel_idle: does not run on family 6 model 15
[    3.185054] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    3.185060] ACPI: Power Button [PWRB]
[    3.185123] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    3.185127] ACPI: Power Button [PWRF]
[    3.185321] ACPI: acpi_idle registered with cpuidle
[    3.187616] ERST: Table is not found!
[    3.187746] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    3.208136] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.208228] Freeing initrd memory: 13076k freed
[    3.208284] isapnp: Scanning for PnP cards...
[    3.561285] isapnp: No Plug & Play device found
[    3.586350] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.586710] Linux agpgart interface v0.103
[    3.588409] brd: module loaded
[    3.589128] loop: module loaded
[    3.589236] i2c-core: driver [adp5520] using legacy suspend method
[    3.589239] i2c-core: driver [adp5520] using legacy resume method
[    3.589360] ata_piix 0000:00:1f.1: version 2.13
[    3.589387] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.589427] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.589831] scsi0 : ata_piix
[    3.589945] scsi1 : ata_piix
[    3.591474] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    3.591478] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    3.591503] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.591508] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    3.591549] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.591928] scsi2 : ata_piix
[    3.592023] scsi3 : ata_piix
[    3.593658] ata3: SATA max UDMA/133 cmd 0xc400 ctl 0xc080 bmdma 0xb880 irq 18
[    3.593662] ata4: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb888 irq 18
[    3.594117] Fixed MDIO Bus: probed
[    3.594162] PPP generic driver version 2.4.2
[    3.594233] tun: Universal TUN/TAP device driver, 1.6
[    3.594235] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.594344] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.594377] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.594394] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.594398] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.594442] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.594496] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    3.594508] ehci_hcd 0000:00:1d.7: debug port 1
[    3.598381] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.598400] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9ffbc00
[    3.612029] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.612227] hub 1-0:1.0: USB hub found
[    3.612233] hub 1-0:1.0: 8 ports detected
[    3.612331] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.612348] uhci_hcd: USB Universal Host Controller Interface driver
[    3.612385] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.612392] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.612395] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.612441] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.612485] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c480
[    3.612630] hub 2-0:1.0: USB hub found
[    3.612635] hub 2-0:1.0: 2 ports detected
[    3.612713] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.612719] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.612723] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.612769] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.612824] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c800
[    3.612968] hub 3-0:1.0: USB hub found
[    3.612973] hub 3-0:1.0: 2 ports detected
[    3.613052] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.613058] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.613062] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.613106] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.616063] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c880
[    3.616258] hub 4-0:1.0: USB hub found
[    3.616263] hub 4-0:1.0: 2 ports detected
[    3.616341] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.616348] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.616351] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.616394] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    3.616445] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000cc00
[    3.616586] hub 5-0:1.0: USB hub found
[    3.616590] hub 5-0:1.0: 2 ports detected
[    3.616774] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    3.616776] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    3.617558] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.617679] mousedev: PS/2 mouse device common for all mice
[    3.617830] rtc_cmos 00:03: RTC can wake from S4
[    3.617903] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.617928] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    3.618034] device-mapper: uevent: version 1.0.3
[    3.618127] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    3.618212] device-mapper: multipath: version 1.2.0 loaded
[    3.618215] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.618303] EISA: Probing bus 0 at eisa.0
[    3.618305] EISA: Cannot allocate resource for mainboard
[    3.618308] Cannot allocate resource for EISA slot 1
[    3.618310] Cannot allocate resource for EISA slot 2
[    3.618312] Cannot allocate resource for EISA slot 3
[    3.618314] Cannot allocate resource for EISA slot 4
[    3.618316] Cannot allocate resource for EISA slot 5
[    3.618318] Cannot allocate resource for EISA slot 6
[    3.618320] Cannot allocate resource for EISA slot 7
[    3.618322] Cannot allocate resource for EISA slot 8
[    3.618324] EISA: Detected 0 cards.
[    3.618381] cpuidle: using governor ladder
[    3.618384] cpuidle: using governor menu
[    3.618723] TCP cubic registered
[    3.618875] NET: Registered protocol family 10
[    3.619563] NET: Registered protocol family 17
[    3.619583] Registering the dns_resolver key type
[    3.620192] Using IPI No-Shortcut mode
[    3.620319] PM: Hibernation image not present or could not be loaded.
[    3.620336] registered taskstats version 1
[    3.620584]   Magic number: 15:738:94
[    3.620670] rtc_cmos 00:03: setting system clock to 2011-06-28 20:05:57 UTC (1309291557)
[    3.620674] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.620675] EDD information not available.
[    3.624112] Refined TSC clocksource calibration: 1999.999 MHz.
[    3.624118] Switching to clocksource tsc
[    3.645368] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    3.772208] ata4.01: ATAPI: PIONEER DVD-RW  DVR-217, 1.05, max UDMA/66
[    3.773198] ata3.00: ATA-8: WDC WD5000AAKX-001CA0, 15.01H15, max UDMA/133
[    3.773203] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.781188] ata3.00: configured for UDMA/133
[    3.787501] ata1.00: ATA-7: ST380215A, 3.AAD, max UDMA/100
[    3.787506] ata1.00: 156301488 sectors, multi 16: LBA48 
[    3.788150] ata4.01: configured for UDMA/66
[    3.854098] ata1.00: configured for UDMA/100
[    3.854272] scsi 0:0:0:0: Direct-Access     ATA      ST380215A        3.AA PQ: 0 ANSI: 5
[    3.854458] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    3.854469] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.854518] sd 0:0:0:0: [sda] Write Protect is off
[    3.854522] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.854593] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.854626] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAKX-0 15.0 PQ: 0 ANSI: 5
[    3.854801] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    3.854977] sd 2:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    3.855046] sd 2:0:0:0: [sdb] Write Protect is off
[    3.855050] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.855079] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.886530] scsi 3:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-217  1.05 PQ: 0 ANSI: 5
[    3.902143]  sda: sda1 sda2
[    3.902447] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.916262]  sdb: sdb1 sdb2 < sdb5 sdb6 > sdb3 sdb4
[    3.916751] sd 2:0:0:0: [sdb] Attached SCSI disk
[    3.917872] sr0: scsi3-mmc drive: 16x/16x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.917877] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.918056] sr 3:0:1:0: Attached scsi CD-ROM sr0
[    3.918132] sr 3:0:1:0: Attached scsi generic sg2 type 5
[    3.918251] Freeing unused kernel memory: 700k freed
[    3.918501] Write protecting the kernel text: 5192k
[    3.918553] Write protecting the kernel read-only data: 2148k
[    3.952533] <30>udev[77]: starting version 167
[    3.980089] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    4.094206] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.094232] r8169 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.094273] r8169 0000:02:00.0: setting latency timer to 64
[    4.094335] r8169 0000:02:00.0: irq 43 for MSI/MSI-X
[    4.094972] r8169 0000:02:00.0: eth0: RTL8168c/8111c at 0xf8006000, 00:26:18:f0:63:1d, XID 1c4000c0 IRQ 43
[    4.124143] [drm] Initialized drm 1.1.0 20060810
[    4.171017] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.171025] nouveau 0000:01:00.0: setting latency timer to 64
[    4.173724] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x096000a1)
[    4.177010] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[    4.225568] [drm] nouveau 0000:01:00.0: ... appears to be valid
[    4.225574] [drm] nouveau 0000:01:00.0: BIT BIOS found
[    4.225578] [drm] nouveau 0000:01:00.0: Bios version 62.94.4b.00
[    4.225582] [drm] nouveau 0000:01:00.0: TMDS table version 2.0
[    4.225585] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
[    4.225589] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 02000300 00000028
[    4.225592] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02000302 00020030
[    4.225594] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 04011310 00000028
[    4.225597] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 01022332 00020010
[    4.225600] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
[    4.225603] [drm] nouveau 0000:01:00.0:   0: 0x00002030: type 0x30 idx 0 tag 0x08
[    4.225607] [drm] nouveau 0000:01:00.0:   1: 0x00000100: type 0x00 idx 1 tag 0xff
[    4.225610] [drm] nouveau 0000:01:00.0:   2: 0x00001261: type 0x61 idx 2 tag 0x07
[    4.225612] [drm] nouveau 0000:01:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff
[    4.225615] [drm] nouveau 0000:01:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff
[    4.225620] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xD20A
[    4.272038] usb 1-5: new high speed USB device using ehci_hcd and address 4
[    4.276156] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xD657
[    4.292028] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xE6A7
[    4.292043] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xE7F0
[    4.300151] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xEA5C
[    4.300156] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xEAC1
[    4.324047] [drm] nouveau 0000:01:00.0: 0xEAC1: Condition still not met after 20ms, skipping following opcodes
[    4.342951] [drm] nouveau 0000:01:00.0: 2 available performance level(s)
[    4.342957] [drm] nouveau 0000:01:00.0: 0: memory 100MHz core 200MHz shader 400MHz voltage 900mV fanspeed 100%
[    4.342962] [drm] nouveau 0000:01:00.0: 3: memory 500MHz core 550MHz shader 1375MHz voltage 1000mV fanspeed 100%
[    4.342978] [drm] nouveau 0000:01:00.0: c: memory 504MHz core 400MHz shader 800MHz voltage 1000mV
[    4.343105] [TTM] Zone  kernel: Available graphics memory: 426258 kiB.
[    4.343107] [TTM] Zone highmem: Available graphics memory: 1806390 kiB.
[    4.343110] [TTM] Initializing pool allocator.
[    4.343125] [drm] nouveau 0000:01:00.0: Detected 512MiB VRAM
[    4.358455] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[    4.383427] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    4.383431] [drm] No driver support for vblank timestamp query.
[    4.412415] usbcore: registered new interface driver uas
[    4.418227] Initializing USB Mass Storage driver...
[    4.422738] scsi4 : usb-storage 1-5:1.0
[    4.423415] usbcore: registered new interface driver usb-storage
[    4.423419] USB Mass Storage support registered.
[    4.516021] usb 1-8: new high speed USB device using ehci_hcd and address 5
[    4.545932] [drm] nouveau 0000:01:00.0: allocated 1440x900 fb: 0x60000000, bo f2971c00
[    4.548315] Console: switching to colour frame buffer device 180x56
[    4.549925] fb0: nouveaufb frame buffer device
[    4.549927] drm: registered panic notifier
[    4.549935] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[    4.650317] scsi5 : usb-storage 1-8:1.0
[    4.888048] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    5.072142] input: HID 04b4:0033 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input3
[    5.072311] generic-usb 0003:04B4:0033.0001: input,hidraw0: USB HID v1.00 Mouse [HID 04b4:0033] on usb-0000:00:1d.0-2/input0
[    5.072332] usbcore: registered new interface driver usbhid
[    5.072334] usbhid: USB HID core driver
[    5.424863] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    5.425496] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    5.426116] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    5.426740] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    5.427313] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    5.427669] sd 4:0:0:1: Attached scsi generic sg4 type 0
[    5.427953] sd 4:0:0:2: Attached scsi generic sg5 type 0
[    5.428242] sd 4:0:0:3: Attached scsi generic sg6 type 0
[    5.433592] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[    5.435006] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[    5.435595] sd 4:0:0:2: [sde] Attached SCSI removable disk
[    5.436223] sd 4:0:0:3: [sdf] Attached SCSI removable disk
[    5.648993] scsi 5:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
[    5.650628] sd 5:0:0:0: Attached scsi generic sg7 type 0
[    5.651724] sd 5:0:0:0: [sdg] 3913728 512-byte logical blocks: (2.00 GB/1.86 GiB)
[    5.652347] sd 5:0:0:0: [sdg] Write Protect is off
[    5.652351] sd 5:0:0:0: [sdg] Mode Sense: 23 00 00 00
[    5.653841] sd 5:0:0:0: [sdg] No Caching mode page present
[    5.653845] sd 5:0:0:0: [sdg] Assuming drive cache: write through
[    5.657828] sd 5:0:0:0: [sdg] No Caching mode page present
[    5.657832] sd 5:0:0:0: [sdg] Assuming drive cache: write through
[    5.658524]  sdg: sdg1
[    5.660839] sd 5:0:0:0: [sdg] No Caching mode page present
[    5.660843] sd 5:0:0:0: [sdg] Assuming drive cache: write through
[    5.660847] sd 5:0:0:0: [sdg] Attached SCSI removable disk
[    5.751341] Btrfs loaded
[    5.758850] xor: automatically using best checksumming function: pIII_sse
[    5.776006]    pIII_sse  :  7336.000 MB/sec
[    5.776009] xor: using function: pIII_sse (7336.000 MB/sec)
[    5.778925] device-mapper: dm-raid45: initialized v0.2594b
[    8.021493] aufs 2.1-standalone.tree-38-rcN-20110207
[    8.042546] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   11.476874] EXT3-fs: barriers not enabled
[   11.478645] kjournald starting.  Commit interval 5 seconds
[   11.479367] EXT3-fs (loop1): using internal journal
[   11.479371] EXT3-fs (loop1): mounted filesystem with ordered data mode
[   11.490763] aufs test_add:261:exe[860]: uid/gid/perm //filesystem.squashfs 0/0/0755, 1000/1000/0755
[   31.221491] <30>udev[3156]: starting version 167
[   31.787626] intel_rng: FWH not detected
[   31.809258] r8169 0000:02:00.0: eth0: link down
[   31.809491] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.947369] leds_ss4200: no LED devices found
[   32.183018] cfg80211: Calling CRDA to update world regulatory domain
[   32.595763] parport_pc 00:06: reported by Plug and Play ACPI
[   32.595875] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
```

there are lots of line. I am really gratefull and thankfull enough if you can help me out with this one..

---

### Post by maizuddin35 on 2011-06-28
is there any chance if I download the latest .deb kernel and install it ?

---

### Post by doas777 on 2011-06-28
> **maizuddin35 said:**
> is there any chance if I download the latest .deb kernel and install it ?
its possiible i suppose, but it seems to me that a manual kernel install would be hard. never tried it myself.

is that the bottom of your dmesg.0 file? the events we are looking for are likely to be at the bottom of the list. 

also running this script and posting back RESULT.txt may help us track down the issue:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by maizuddin35 on 2011-06-28
Here are the output from the bootscript. I hope it is useful enough to get me fix this thing. 

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for (,msdos3)/boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for (,msdos3)/boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdg.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb3: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdg1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.......pY.....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1408976 of /dev/sdg1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdg1 starts at sector 
                       0. But according to the info from fdisk, sdg1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   154,253,311   154,046,464   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    90,529,791    90,527,744  83 Linux
/dev/sdb2         879,118,334   976,771,071    97,652,738   5 Extended
/dev/sdb5         879,118,336   967,006,207    87,887,872   b W95 FAT32
/dev/sdb6         967,008,256   976,771,071     9,762,816  82 Linux swap / Solaris
/dev/sdb3          90,529,792   879,116,287   788,586,496  83 Linux
/dev/sdb4         976,771,072   976,773,119         2,048  82 Linux swap / Solaris


Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 2003 MB, 2003828736 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1    *             62     3,913,191     3,913,130   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       f3d53f1a-0540-48af-9bfd-599db553c24b   ext3       
/dev/sda1        E400C42400C3FF92                       ntfs       System Reserved
/dev/sda2        CCF4D290F4D27C60                       ntfs       
/dev/sdb3        9934b0eb-d3bb-4cfd-bfed-a9ca461d4058   ext2       
/dev/sdb5        0B9F-6BCE                              vfat       
/dev/sdg1        69C8-E24A                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/loop1       /media/f3d53f1a-0540-48af-9bfd-599db553c24b ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/CCF4D290F4D27C60  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb3        /media/9934b0eb-d3bb-4cfd-bfed-a9ca461d4058 ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb5        /media/0B9F-6BCE         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdg1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set 9934b0eb-d3bb-4cfd-bfed-a9ca461d4058
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1440x900-24
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set 9934b0eb-d3bb-4cfd-bfed-a9ca461d4058
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'elementary-jupiter, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 9934b0eb-d3bb-4cfd-bfed-a9ca461d4058
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=9934b0eb-d3bb-4cfd-bfed-a9ca461d4058 ro   quiet splash nomodeset video=uvesafb:mode_option=>>1440x900-24<<,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 9934b0eb-d3bb-4cfd-bfed-a9ca461d4058
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=9934b0eb-d3bb-4cfd-bfed-a9ca461d4058 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 9934b0eb-d3bb-4cfd-bfed-a9ca461d4058
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=9934b0eb-d3bb-4cfd-bfed-a9ca461d4058 ro   quiet splash nomodeset video=uvesafb:mode_option=>>1440x900-24<<,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 9934b0eb-d3bb-4cfd-bfed-a9ca461d4058
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=9934b0eb-d3bb-4cfd-bfed-a9ca461d4058 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set E400C42400C3FF92
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=9934b0eb-d3bb-4cfd-bfed-a9ca461d4058 /               ext2    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=a0dd71cf-c4c4-4bb2-8b56-ad4cdc7ab80d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 212.897018433 = 228.596432896  boot/grub/core.img                             2
 212.879016876 = 228.577103872  boot/grub/grub.cfg                             1
 212.775547028 = 228.466003968  boot/initrd.img-2.6.35-28-generic              9
 212.734748840 = 228.422197248  boot/initrd.img-2.6.35-30-generic              8
 212.754364014 = 228.443258880  boot/vmlinuz-2.6.35-28-generic                 3
 212.766460419 = 228.456247296  boot/vmlinuz-2.6.35-30-generic                 3
 212.734748840 = 228.422197248  initrd.img                                     8
 212.734748840 = 228.422197248  initrd.img.old                                 8
 212.766460419 = 228.456247296  vmlinuz                                        3
 212.766460419 = 228.456247296  vmlinuz.old                                    3

========================= sdg1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdg1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdg1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  a4 81 00 00 5d 01 00 00  57 0f f4 4d 57 0f f4 4d  |....]...W..MW..M|
00000010  57 0f f4 4d 00 00 00 00  00 00 01 00 08 00 00 00  |W..M............|
00000020  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  01 00 00 00 50 91 a0 00  |............P...|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 f7 d4 05 cc  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  1c 00 00 00 68 5a 4c c6  68 5a 4c c6 68 5a 4c c6  |....hZL.hZL.hZL.|
00000090  57 0f f4 4d 68 5a 4c c6  00 00 00 00 00 00 00 00  |W..MhZL.........|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  a4 81 00 00 ac 09 00 00  65 0f f4 4d 65 0f f4 4d  |........e..Me..M|
00000110  65 0f f4 4d 00 00 00 00  00 00 01 00 08 00 00 00  |e..M............|
00000120  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  01 00 00 00 ca 91 a0 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 89 d5 05 cc  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  1c 00 00 00 38 aa da ba  38 aa da ba 38 aa da ba  |....8...8...8...|
00000190  65 0f f4 4d 38 aa da ba  00 00 00 00 00 00 00 00  |e..M8...........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by maizuddin35 on 2011-06-28
what I know is...

sdb1 is one of the damage partition , it is , before, linux, but then , end up , everything gone in it, and I try to recover some of the files back, but I still did not manage to do it yet.

if im not mistaken , I installed the boot loader in sda1 that is where my windows is.

---

### Post by doas777 on 2011-06-29
> **maizuddin35 said:**
> what I know is...

sdb1 is one of the damage partition , it is , before, linux, but then , end up , everything gone in it, and I try to recover some of the files back, but I still did not manage to do it yet.

if im not mistaken , I installed the boot loader in sda1 that is where my windows is.

I see a number of things that are don;t look quite right, but I feel like my suggestions are shots in the dark. The best advice I can give you is to post a new topic specific to your boot issue (since the apt-get problem was addressed), with title like "Won't boot -- Bootinfoscript output", and post the output above.

I would suggest running fsck on sdb1, if it is in fact an ext3 partition. is the problem just with the filesystem or is sdb starting to fail?!?

---

### Post by maizuddin35 on 2011-06-29
thank you for suggesting me that, I will post a thread for this one and hoping that everyone here will help out:) thank you again !

---

### Post by maizuddin35 on 2011-06-29
[http://ubuntuforums.org/showthread.php?p=10993057#post10993057](http://ubuntuforums.org/showthread.php?p=10993057#post10993057)

---

