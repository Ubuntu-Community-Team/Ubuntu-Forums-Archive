---
title: "ksoftirqd using 100% CPU"
date: 2011-06-12
forum: General Help
---

### Post by okhowaboutthisusername on 2011-06-12
Ubuntu 11.04
Linux version 2.6.38-10-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #44-Ubuntu SMP Thu Jun 2 21:32:22 UTC 2011

Whenever I resume from suspend a process, ksoftirqd, starts hogging CPU. I can't seem to even kill the process (and don't know if that's a good idea). Otherwise, a reboot seems to be the only solution.

Google returns lots of matches on this, going back several years, but I've yet to see a definitive answer to the problem. Any ideas?

```
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+ COMMAND                           
3 root      20   0     0    0    0 R 94.2  0.0   8:26.45 ksoftirqd/0
```

dmesg shows:

[22385.910021] sr 1:0:1:0: timing out command, waited 120s
[22440.280147] INFO: task udisks-daemon:1951 blocked for more than 120 seconds.
[22440.280153] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[22440.280157] udisks-daemon   D 0000000000000000     0  1951   1950 0x00000000
[22440.280163]  ffff880057d758d8 0000000000000086 ffff880057d75fd8 ffff880057d74000
[22440.280167]  0000000000013d00 ffff880056dadf38 ffff880057d75fd8 0000000000013d00
[22440.280171]  ffff88002da996e0 ffff880056dadb80 ffff880057d758d8 7fffffffffffffff
[22440.280175] Call Trace:
[22440.280189]  [<ffffffff815c14ed>] schedule_timeout+0x26d/0x2e0
[22440.280196]  [<ffffffff81057613>] ? update_curr+0x103/0x210
[22440.280200]  [<ffffffff815c312e>] ? _raw_spin_lock+0xe/0x20
[22440.280203]  [<ffffffff81054c7d>] ? task_rq_lock+0x5d/0xa0
[22440.280208]  [<ffffffff815c0fa9>] wait_for_common+0xd9/0x180
[22440.280212]  [<ffffffff8105f600>] ? default_wake_function+0x0/0x20
[22440.280218]  [<ffffffff810807c2>] ? insert_work+0x72/0x80
[22440.280222]  [<ffffffff815c112d>] wait_for_completion+0x1d/0x20
[22440.280226]  [<ffffffff81083745>] flush_work+0x35/0x40
[22440.280230]  [<ffffffff81080030>] ? wq_barrier_func+0x0/0x20
[22440.280233]  [<ffffffff8108379b>] flush_delayed_work+0x4b/0x60
[22440.280239]  [<ffffffff812cc3ee>] disk_clear_events+0x8e/0x130
[22440.280244]  [<ffffffff81198537>] check_disk_change+0x37/0x80
[22440.280248]  [<ffffffff8142f25a>] cdrom_open+0x3a/0x1f0
[22440.280254]  [<ffffffff812dccca>] ? kobject_get+0x1a/0x30
[22440.280258]  [<ffffffff813b6b39>] ? get_device+0x19/0x20
[22440.280264]  [<ffffffff813dd37c>] ? scsi_device_get+0x4c/0xc0
[22440.280269]  [<ffffffff813f5c39>] sr_block_open+0x89/0xf0
[22440.280273]  [<ffffffff81199749>] __blkdev_get+0xa9/0x3b0
[22440.280276]  [<ffffffff81199b7d>] blkdev_get+0x12d/0x2a0
[22440.280280]  [<ffffffff81199cf0>] ? blkdev_open+0x0/0x80
[22440.280283]  [<ffffffff81199d55>] blkdev_open+0x65/0x80
[22440.280288]  [<ffffffff81162d0e>] __dentry_open+0xce/0x2f0
[22440.280292]  [<ffffffff8116ef53>] ? generic_permission+0x23/0xc0
[22440.280296]  [<ffffffff81164201>] nameidata_to_filp+0x71/0x80
[22440.280300]  [<ffffffff81173408>] finish_open+0xc8/0x1b0
[22440.280303]  [<ffffffff811725f7>] ? do_path_lookup+0x87/0x160
[22440.280307]  [<ffffffff81173bc8>] do_filp_open+0x2c8/0x7c0
[22440.280310]  [<ffffffff813b6b77>] ? put_device+0x17/0x20
[22440.280313]  [<ffffffff813dd314>] ? scsi_device_put+0x44/0x60
[22440.280318]  [<ffffffff812e6b67>] ? __strncpy_from_user+0x27/0x60
[22440.280324]  [<ffffffff81180ee7>] ? alloc_fd+0xf7/0x150
[22440.280327]  [<ffffffff8116427a>] do_sys_open+0x6a/0x150
[22440.280330]  [<ffffffff81164380>] sys_open+0x20/0x30
[22440.280335]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
[22505.920018] sr 1:0:1:0: timing out command, waited 120s

repeat ...

Here's some system info:

$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 12
model name    : AMD Athlon(tm) 64 Processor 3000+
stepping    : 0
cpu MHz        : 2000.000
cache size    : 512 KB
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow up rep_good nopl
bogomips    : 3991.40
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

$ cat /proc/interrupts
           CPU0       
  0:         26   IO-APIC-edge      timer
  1:      12452   IO-APIC-edge      i8042
  5:          1   IO-APIC-edge      MPU401 UART
  6:          4   IO-APIC-edge      floppy
  7:          1   IO-APIC-edge      parport0
  8:          0   IO-APIC-edge      rtc0
  9:          0   IO-APIC-fasteoi   acpi
 14:      90211   IO-APIC-edge      pata_sis
 15:      84447   IO-APIC-edge      pata_sis
 17:          0   IO-APIC-fasteoi   sata_sis
 18:        197   IO-APIC-fasteoi   SiS SI7012
 19:      58735   IO-APIC-fasteoi   eth0
 20:          0   IO-APIC-fasteoi   ohci_hcd:usb2
 21:          0   IO-APIC-fasteoi   ohci_hcd:usb3
 22:      51522   IO-APIC-fasteoi   ohci_hcd:usb4
 23:          2   IO-APIC-fasteoi   ehci_hcd:usb1
NMI:          0   Non-maskable interrupts
LOC:    5965272   Local timer interrupts
SPU:          0   Spurious interrupts
PMI:          0   Performance monitoring interrupts
IWI:          0   IRQ work interrupts
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:         76   Machine check polls
ERR:          1
MIS:          0

$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
vesafb                 13761  1 
ipt_REJECT             12576  1 
ipt_LOG                17016  5 
xt_limit               12711  7 
xt_tcpudp              12603  9 
ipt_addrtype           12599  4 
xt_state               12578  7 
snd_intel8x0           38272  2 
snd_ac97_codec        134270  1 snd_intel8x0
ip6table_filter        12815  1 
ac97_bus               12730  1 snd_ac97_codec
ip6_tables             27845  1 ip6table_filter
snd_pcm                96391  2 snd_intel8x0,snd_ac97_codec
snd_mpu401             14184  0 
nf_nat_irc             12643  0 
snd_mpu401_uart        14169  1 snd_mpu401
snd_seq_midi           13324  0 
nf_conntrack_irc       13383  1 nf_nat_irc
edac_core              53845  0 
nf_nat_ftp             12649  0 
snd_rawmidi            30486  2 snd_mpu401_uart,snd_seq_midi
nf_nat                 25736  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      19640  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_ftp       13359  1 nf_nat_ftp
snd_seq_midi_event     14899  1 snd_seq_midi
nf_conntrack           81956  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
iptable_filter         12810  1 
ip_tables              27456  1 iptable_filter
ppdev                  17113  0 
snd_timer              29602  2 snd_pcm,snd_seq
ns558                  12706  0 
w83627hf               32239  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
edac_mce_amd           23464  0 
hwmon_vid              12746  1 w83627hf
snd                    67382  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             36959  1 
gameport               19652  2 ns558
shpchp                 37297  0 
x_tables               29581  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
k8temp                 13016  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_intel8x0,snd_pcm
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
floppy                 74120  0 
sata_sis               12816  0 
sis900                 27160  0

$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

