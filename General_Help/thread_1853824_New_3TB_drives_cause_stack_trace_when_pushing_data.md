---
title: "New 3TB drives cause stack trace when pushing data"
date: 2011-10-03
forum: General Help
---

### Post by ryannelson on 2011-10-03
I was hoping that someone could help out with more info or point me in the right direction.  I get the following kernel stack trace with my new 3TB drives when data is pushed at a high rate.  I can reproduce it quickly by doing "dd if=/dev/sd[?] of=/dev/null" with in 2 minutes the issue will happen on any of the 3TB drives.


[  265.862519] BUG: unable to handle kernel paging request at 0000000020000008
[  265.862527] IP: [<ffffffff810f4909>] find_get_page+0x39/0xa0
[  265.862535] PGD 1f1e69067 PUD 216be1067 PMD 0
[  265.862540] Oops: 0000 [#1] SMP
[  265.862543] last sysfs file: /sys/devices/pci0000:00/0000:00:1e.0/0000:07:04.0/local_cpus
[  265.862547] CPU 2
[  265.862549] Modules linked in: ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 iptable_filter ip_tables x_tables binfmt_misc bc_cast(P) bc_rijn(P) bc_idea(P) bc_3des(P) bc_bf128(P) bc_bf448(P) bc_twofish(P) bc_gost(P) bc_des(P) bc_blowfish(P) bc(P) snd_hda_codec_analog snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss ppdev snd_pcm parport_pc snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device nvidia(P) snd sbp2 intel_agp fbcon tileblit font bitblit softcursor vga16fb vgastate soundcore snd_page_alloc arc4 asus_atk0110 rtl8187 mac80211 led_class lp cfg80211 eeprom_93cx6 parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov ohci1394 raid6_pq r8169 async_tx floppy ieee1394 mii raid1 sky2 usbhid hid pata_jmicron raid0 ahci multipath linear
[  265.862613] Pid: 2344, comm: dd Tainted: P           2.6.32-33-generic #72-Ubuntu P5K Premium
[  265.862615] RIP: 0010:[<ffffffff810f4909>]  [<ffffffff810f4909>] find_get_page+0x39/0xa0
[  265.862620] RSP: 0018:ffff880216bdfc88  EFLAGS: 00010203
[  265.862622] RAX: 000000001fffffff RBX: ffff880226e03940 RCX: ffff88009407b430
[  265.862624] RDX: 0000000000000000 RSI: 0000000000119439 RDI: 0000000020000000
[  265.862627] RBP: ffff880216bdfc98 R08: 0000000000000200 R09: 0000000000000001
[  265.862629] R10: ffff880216bdffd8 R11: 0000000000000246 R12: 0000000000119439
[  265.862631] R13: 0000000000119439 R14: ffff8801fde2b840 R15: 0000000000000000
[  265.862634] FS:  00007fd37249a700(0000) GS:ffff880028300000(0000) knlGS:0000000000000000
[  265.862637] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  265.862639] CR2: 0000000020000008 CR3: 0000000216b44000 CR4: 00000000000006e0
[  265.862641] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  265.862644] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  265.862647] Process dd (pid: 2344, threadinfo ffff880216bde000, task ffff8801fde3ade0)
[  265.862648] Stack:
[  265.862650]  0000000000000000 ffff880226e03938 ffff880216bdfd28 ffffffff810f5ac8
[  265.862654] <0> 0000000000119439 0000000000000200 ffff880216bdfe48 0000000016bdffd8
[  265.862658] <0> 000000000011943a 0000000000119438 ffff8801fde2b8b0 ffff880226e03818
[  265.862663] Call Trace:
[  265.862667]  [<ffffffff810f5ac8>] T.810+0x158/0x420
[  265.862671]  [<ffffffff810f5e46>] generic_file_aio_read+0xb6/0x1d0
[  265.862674]  [<ffffffff810f5d96>] ? generic_file_aio_read+0x6/0x1d0
[  265.862679]  [<ffffffff8114408a>] do_sync_read+0xfa/0x140
[  265.862682]  [<ffffffff8113f39b>] ? mem_cgroup_charge_common+0x7b/0xa0
[  265.862687]  [<ffffffff81084cc0>] ? autoremove_wake_function+0x0/0x40
[  265.862692]  [<ffffffff8101079c>] ? __switch_to+0x1ac/0x320
[  265.862697]  [<ffffffff81057d80>] ? finish_task_switch+0x50/0xe0
[  265.862702]  [<ffffffff81253796>] ? security_file_permission+0x16/0x20
[  265.862705]  [<ffffffff81144975>] vfs_read+0xb5/0x1a0
[  265.862708]  [<ffffffff81144b31>] sys_read+0x51/0x80
[  265.862712]  [<ffffffff810121b2>] system_call_fastpath+0x16/0x1b
[  265.862714] Code: 5f 08 49 89 f4 4c 89 e6 48 89 df e8 b2 3b 1c 00 48 85 c0 48 89 c1 74 42 48 8b 38 40 f6 c7 01 75 e4 48 8d 47 ff 48 83 f8 fd 77 da <8b> 57 08 85 d2 74 d3 8d 72 01 48 63 c2 4c 8d 47 08 48 63 f6 f0
[  265.862748] RIP  [<ffffffff810f4909>] find_get_page+0x39/0xa0
[  265.862751]  RSP <ffff880216bdfc88>
[  265.862753] CR2: 0000000020000008
[  265.862756] ---[ end trace 30762f5ec55a1dd8 ]---




I'm not sure what to make of it or where the problem is coming from but I would like to know if I should return the drives.  This issue doesn't happen with other drives on the same box.

Here is more background info:

I have 6 x 500GB drives attached to the motherboard I'm trying to replace with the new 3 x 3TB drives.  I also have a system drive installed.  The 3TB drives are attached to 2 SIIG SATA PCI-E controller cards (Marvell chip set).  I've ruled them out as the issue as I've attached them straight to the motherboard while the cards are remove and still get the same issue.

root@canyon:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:        10.04
Codename:       lucid
root@canyon:~# uname -a
Linux canyon 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:07:13 UTC 2011 x86_64 GNU/Linux
root@canyon:~# lsscsi
[0:0:0:0]    disk    ATA      WDC WD5000AAKS-0 12.0  /dev/sda
[0:0:1:0]    disk    ATA      WDC WD5000AAKS-0 12.0  /dev/sdb
[1:0:0:0]    disk    ATA      WDC WD5000AAKS-0 12.0  /dev/sdc
[1:0:1:0]    disk    ATA      WDC WD5000AAKS-0 12.0  /dev/sdd
[2:0:0:0]    disk    ATA      WDC WD5000AAKS-0 12.0  /dev/sde
[3:0:0:0]    disk    ATA      WDC WD5000AAKS-0 01.0  /dev/sdf
[4:0:0:0]    disk    ATA      ST380021A        3.10  /dev/sdg
[6:0:0:0]    disk    ATA      Hitachi HDS72303 MKAO  /dev/sdh
[7:0:0:0]    disk    ATA      Hitachi HDS72303 MKAO  /dev/sdi
[13:0:0:0]   process Marvell  91xx Config      1.01  -
[14:0:0:0]   disk    ATA      Hitachi HDS72303 MKAO  /dev/sdj
[21:0:0:0]   process Marvell  91xx Config      1.01  -
root@canyon:~# lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
04:00.0 SATA controller: Device 1b4b:9123 (rev 11)
04:00.1 IDE interface: Device 1b4b:91a4 (rev 11)
05:00.0 SATA controller: Device 1b4b:9123 (rev 11)
05:00.1 IDE interface: Device 1b4b:91a4 (rev 11)
07:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
07:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

---

### Post by dcstar on 2011-10-03
> **ryannelson said:**
> I was hoping that someone could help out with more info or point me in the right direction.  I get the following kernel stack trace with my new 3TB drives when data is pushed at a high rate.  I can reproduce it quickly by doing "dd if=/dev/sd[?] of=/dev/null" with in 2 minutes the issue will happen on any of the 3TB drives.
.......

These seem to be SATA-3 drives, I'm not sure the 10.04 kernel supports SATA-3 hardware.

---

