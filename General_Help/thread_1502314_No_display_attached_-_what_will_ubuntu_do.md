---
title: "No display attached - what will ubuntu do?"
date: 2010-06-05
forum: General Help
---

### Post by Valentini on 2010-06-05
Hi

I think my laptop's nvidia card have been fried (all i get when i boot is a greyish screen and some hdd activity).
Does anyone know how grub2/ubuntu will react to this? Is it possible to boot fully into ubuntu?
I've installed ssh and made sure the port was open before my computer crashed.
I've managed to log into my dual boot windows (when i "log on" it registers at y wifi router), but thats not of much use.
I've tried with normal gdm login (enter>password>enter) and terminal login (username>enter>password>enter), but without any success (my wifi router doesn't register anything).

Thanks for any help with this :)

---

### Post by Bradj47 on 2010-06-05
> **Valentini said:**
> Hi

I think my laptop's nvidia card have been fried (all i get when i boot is a greyish screen and some hdd activity).
Does anyone know how grub2/ubuntu will react to this? Is it possible to boot fully into ubuntu?
I've installed ssh and made sure the port was open before my computer crashed.
I've managed to log into my dual boot windows (when i "log on" it registers at y wifi router), but thats not of much use.
I've tried with normal gdm login (enter>password>enter) and terminal login (username>enter>password>enter), but without any success (my wifi router doesn't register anything).

Thanks for any help with this :)

If you have another Ubuntu computer you could try some Remote Desktop viewer application. I remember previous versions of Ubuntu had one but I don't see one in any of the 10.04 menus.

---

### Post by nemilar on 2010-06-05
After you boot up, can you ping the machine?

---

### Post by Valentini on 2010-06-05
I've now logged in on my ubuntu machine. It was booting up in terminal mode, and network manager was of course not starting, hence no wifi authentication.
I've started internet sharing on the mac (to get a dhcp server) and connected directly with a ethernet cable.
It is obviosly the nvidia card which is roasted; from dmesg:

```
[   14.408093] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.15  Fri Mar 12 00:29:13 PST 2010
[   14.411957] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[   14.413502] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   14.413504] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   14.413590] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.413617] iwlagn 0000:0c:00.0: setting latency timer to 64
[   14.415369] iwlagn 0000:0c:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   14.436250] cfg80211: World regulatory domain updated:
[   14.436253] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.436256] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.436258] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.436260] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.436262] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.436264] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.467867] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
[   14.468216]   alloc irq_desc for 32 on node -1
[   14.468219]   alloc kstat_irqs on node -1
[   14.468241] iwlagn 0000:0c:00.0: irq 32 for MSI/MSI-X
[   14.479115] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.877347] elantech.c: assuming hardware version 1, firmware version 2.4
[   14.970204] elantech.c: Synaptics capabilities query result 0x10, 0x02, 0x64.
[   15.191547] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   15.336597] EXT4-fs (sda7): mounted filesystem with ordered data mode
[   15.520011] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x023b8000
[   15.678761] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input8
[   16.872084] type=1505 audit(1275759088.789:5):  operation="profile_load" pid=986 name="/usr/share/gdm/guest-session/Xsession"
[   16.873425] type=1505 audit(1275759088.789:6):  operation="profile_replace" pid=987 name="/sbin/dhclient3"
[   16.875703]   alloc irq_desc for 33 on node -1
[   16.875706]   alloc kstat_irqs on node -1
[   16.875736] tg3 0000:04:00.0: irq 33 for MSI/MSI-X
[   16.880208] type=1505 audit(1275759088.799:7):  operation="profile_replace" pid=987 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.880516] type=1505 audit(1275759088.799:8):  operation="profile_replace" pid=987 name="/usr/lib/connman/scripts/dhclient-script"
[   16.883231] type=1505 audit(1275759088.799:9):  operation="profile_load" pid=988 name="/usr/bin/evince"
[   16.890338] type=1505 audit(1275759088.809:10):  operation="profile_load" pid=988 name="/usr/bin/evince-previewer"
[   16.895052] type=1505 audit(1275759088.809:11):  operation="profile_load" pid=988 name="/usr/bin/evince-thumbnailer"
[   16.905124] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.932095] iwlagn 0000:0c:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   16.950812] iwlagn 0000:0c:00.0: loaded firmware version 228.61.2.24
[   17.166698] Registered led device: iwl-phy0::radio
[   17.167021] Registered led device: iwl-phy0::assoc
[   17.167344] Registered led device: iwl-phy0::RX
[   17.167663] Registered led device: iwl-phy0::TX
[   17.371997] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.604028] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1076)
[   17.604035] NVRM: rm_init_adapter(0) failed
[   17.734653] Bluetooth: L2CAP ver 2.14
[   17.734655] Bluetooth: L2CAP socket layer initialized
[   17.740299] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.740301] Bluetooth: BNEP filters: protocol multicast
[   17.747474] Bridge firewalling registered
[   17.754169] Bluetooth: SCO (Voice Link) ver 0.6
[   17.754172] Bluetooth: SCO socket layer initialized
[   17.798731] ppdev: user-space parallel port driver
[   17.859978] Bluetooth: RFCOMM TTY layer initialized
[   17.859982] Bluetooth: RFCOMM socket layer initialized
[   17.859983] Bluetooth: RFCOMM ver 1.11
[   17.923969] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1076)
[   17.923977] NVRM: rm_init_adapter(0) failed
[   18.193578] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   18.207040] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1076)
[   18.207047] NVRM: rm_init_adapter(0) failed
[   18.218069] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[   18.481709] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1076)
[   18.481716] NVRM: rm_init_adapter(0) failed
[   20.130241] tg3: eth0: Link is up at 1000 Mbps, full duplex.
[   20.130244] tg3: eth0: Flow control is on for TX and on for RX.
[   21.316988] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.889208] NVRM: Xid (0001:00): 54, CMDre 00000000 00000088 0100cb05 00000007 00000000
[   24.889586] NVRM: Xid (0001:00): 54, CMDre 00000000 0000008c 00000000 00000005 00000008
[   28.932633] NVRM: Xid (0001:00): 54, CMDre 00000000 00000088 0100cb0c 00000007 00000000
[   28.932835] NVRM: Xid (0001:00): 54, CMDre 00000000 0000008c 00000000 00000005 00000008
[   31.632536] eth0: no IPv6 routers present
[   31.934403] NVRM: Xid (0001:00): 54, CMDre 00000000 00000080 00000000 00000005 00000008
[   33.813412] divide error: 0000 [#1] SMP 
[   33.813417] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.1/0000:04:00.0/irq
[   33.813419] CPU 1 
[   33.813421] Modules linked in: binfmt_misc rfcomm ppdev sco bridge stp bnep l2cap joydev arc4 snd_hda_codec_si3054 iwlagn snd_hda_codec_realtek iwlcore sdhci_pci mac80211 iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 iptable_mangle iptable_filter ip_tables x_tables uvcvideo videodev v4l1_compat v4l2_compat_ioctl32 btusb bluetooth tpm_infineon tpm tpm_bios compal_laptop cfg80211 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd psmouse sdhci serio_raw led_class ricoh_mmc nvidia(P) soundcore snd_page_alloc lp parport vga16fb ohci1394 video ieee1394 output vgastate fbcon tileblit font bitblit softcursor tg3 intel_agp ahci
[   33.813465] Pid: 1349, comm: Xorg Tainted: P           2.6.32-22-generic #36-Ubuntu N/A                                            
[   33.813468] RIP: 0010:[<ffffffffa013cf15>]  [<ffffffffa013cf15>] _nv022220rm+0x28a/0x4f6 [nvidia]
[   33.813678] RSP: 0018:ffff880138721938  EFLAGS: 00010296
[   33.813680] RAX: 00000000000927c0 RBX: 0000000000000000 RCX: 0000000000000000
[   33.813682] RDX: 0000000000000000 RSI: 0000000000000000 RDI: ffff88013846c000
[   33.813683] RBP: ffff8801380ada00 R08: 0000000000000000 R09: 0000000000000000
[   33.813685] R10: 0000000000000200 R11: 0000000000000000 R12: ffff8801380adbe0
[   33.813687] R13: 0000000000000000 R14: ffff88013846c000 R15: ffff880129320000
[   33.813689] FS:  00007f5c3dbee700(0000) GS:ffff880028300000(0000) knlGS:0000000000000000
[   33.813691] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   33.813693] CR2: 00007f263825ee9c CR3: 0000000001001000 CR4: 00000000000006e0
[   33.813695] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   33.813697] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   33.813699] Process Xorg (pid: 1349, threadinfo ffff880138720000, task ffff88013870c4d0)
[   33.813700] Stack:
[   33.813701]  ffff88013846c000 00000000dff3d113 ffff88012df11400 ffff880129320000
[   33.813704] <0> 0000000000000040 ffffffffa0413361 0000000000000011 ffff88013846c000
[   33.813707] <0> ffff8801298dc000 ffff88013aa8e000 000000000000007f ffffffffa0302a48
[   33.813711] Call Trace:
[   33.813861]  [<ffffffffa0413361>] ? _nv010017rm+0x319/0x4aa [nvidia]
[   33.813997]  [<ffffffffa0302a48>] ? _nv016183rm+0x1c8/0x33b [nvidia]
[   33.814134]  [<ffffffffa04faa95>] ? _nv005061rm+0x743/0x7e0 [nvidia]
[   33.814268]  [<ffffffffa04fbf0b>] ? _nv005059rm+0x139/0x1f2 [nvidia]
[   33.814402]  [<ffffffffa04fc192>] ? _nv004984rm+0x1ce/0x330 [nvidia]
[   33.814536]  [<ffffffffa04fc16d>] ? _nv004984rm+0x1a9/0x330 [nvidia]
[   33.814677]  [<ffffffffa04377f1>] ? _nv004575rm+0x182/0x7b1 [nvidia]
[   33.814818]  [<ffffffffa04367b6>] ? _nv004577rm+0x39/0x46 [nvidia]
[   33.814960]  [<ffffffffa0436b3c>] ? _nv004568rm+0xe5/0x4c7 [nvidia]
[   33.815101]  [<ffffffffa04367b6>] ? _nv004577rm+0x39/0x46 [nvidia]
[   33.815243]  [<ffffffffa04368dd>] ? _nv004572rm+0x11a/0x294 [nvidia]
[   33.815385]  [<ffffffffa04367b6>] ? _nv004577rm+0x39/0x46 [nvidia]
[   33.815526]  [<ffffffffa04c1233>] ? _nv004536rm+0xcb/0x10c [nvidia]
[   33.815668]  [<ffffffffa04c2eac>] ? rm_free_unused_clients+0x69/0xb7 [nvidia]
[   33.815787]  [<ffffffffa05af534>] ? nv_kern_ctl_close+0x74/0x100 [nvidia]
[   33.815905]  [<ffffffffa05b0293>] ? nv_kern_close+0x393/0x3f0 [nvidia]
[   33.815911]  [<ffffffff81144305>] ? __fput+0xf5/0x210
[   33.815913]  [<ffffffff81144445>] ? fput+0x25/0x30
[   33.815916]  [<ffffffff8114053d>] ? filp_close+0x5d/0x90
[   33.815920]  [<ffffffff81068d8f>] ? put_files_struct+0x7f/0xf0
[   33.815922]  [<ffffffff81068e54>] ? exit_files+0x54/0x70
[   33.815925]  [<ffffffff8106b3ab>] ? do_exit+0x14b/0x380
[   33.815927]  [<ffffffff8106b635>] ? do_group_exit+0x55/0xd0
[   33.815930]  [<ffffffff8107bf77>] ? get_signal_to_deliver+0x1d7/0x3d0
[   33.815934]  [<ffffffff81012a35>] ? do_signal+0x75/0x1c0
[   33.815938]  [<ffffffff81040537>] ? is_prefetch+0xb7/0x250
[   33.815940]  [<ffffffff8107a252>] ? send_signal+0x42/0x80
[   33.815944]  [<ffffffff810397a9>] ? default_spin_lock_flags+0x9/0x10
[   33.815947]  [<ffffffff8107b412>] ? force_sig_info+0xa2/0x110
[   33.815949]  [<ffffffff81012bdd>] ? do_notify_resume+0x5d/0x80
[   33.815952]  [<ffffffff81013c1c>] ? retint_signal+0x48/0x8c
[   33.815953] Code: 84 d6 00 00 00 48 8d 8d 60 01 00 00 44 89 ea 48 8b 75 50 4c 89 f7 ff 96 a8 1d 00 00 8b b5 6c 01 00 00 48 8b 45 10 ba 00 00 00 00 <48> f7 f6 48 89 c7 ff c7 48 8b 45 08 ba 00 00 00 00 48 f7 f6 8d 
[   33.815979] RIP  [<ffffffffa013cf15>] _nv022220rm+0x28a/0x4f6 [nvidia]
[   33.816070]  RSP <ffff880138721938>
[   33.816073] ---[ end trace 96669503a50128cb ]---
[   33.816075] Fixing recursive fault but reboot is needed!

```
At least i can potentially use it as a server of some kind..

---

