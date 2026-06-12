---
title: "Kernel updated to 2.6.38-11, refuses to boot."
date: 2011-08-22
forum: General Help
---

### Post by pjd99 on 2011-08-22
Computer updated itself to latest kernel this morning, and sits at the "Ubuntu" loading screen (with the dots below). No keyboard response, have to kill it with the power button.

Still boots in recovery mode, so I'm thinking it's maybe something to do with nVidia drivers?
Currently posting from 2.6.38-10, which is still working fine. Ran Synaptic to see if there have been any more updates, but none so far.

Specs: Dell Vostro 1710, nVidia 8600GS, Ubuntu 11.04 Natty Narwhal.

Any ideas? Or should I just wait till the next kernel update?

---

### Post by fdrake on 2011-08-22
> **pjd99 said:**
> Computer updated itself to latest kernel this morning, and sits at the "Ubuntu" loading screen (with the dots below). No keyboard response, have to kill it with the power button.

Still boots in recovery mode, so I'm thinking it's maybe something to do with nVidia drivers?
Currently posting from 2.6.38-10, which is still working fine. Ran Synaptic to see if there have been any more updates, but none so far.

Specs: Dell Vostro 1710, nVidia 8600GS, Ubuntu 11.04 Natty Narwhal.

Any ideas? Or should I just wait till the next kernel update?

```
dmesg | less
```

---

### Post by hawthornso23 on 2011-08-22
I would guess you are right. So boot into the older kernel and reinstall your nvidea drivers.

---

### Post by pjd99 on 2011-08-22
Checked the logs, found something from a bad boot. Here it is from a little before the trouble begins.

Start of what is not normally in the logs: [   17.237303] general protection fault: 0000 [#1] SMP

```

[   15.458513] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   15.485709] vesafb: framebuffer at 0xc9000000, mapped to 0xffffc90012080000, using 9024k, total 9024k
[   15.485713] vesafb: mode is 1920x1200x32, linelength=7680, pages=0
[   15.485714] vesafb: scrolling: redraw
[   15.485716] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   15.485920] Console: switching to colour frame buffer device 240x75
[   15.485956] fb0: VESA VGA frame buffer device
[   16.881696] EXT4-fs (sdb): mounted filesystem with ordered data mode. Opts: (null)
[   16.939803] RPC: Registered udp transport module.
[   16.939806] RPC: Registered tcp transport module.
[   16.939808] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   17.018300] FS-Cache: Loaded
[   17.028589] ppdev: user-space parallel port driver
[   17.057312] type=1400 audit(1313978985.421:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1044 comm="apparmor_parser"
[   17.058627] type=1400 audit(1313978985.421:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1046 comm="apparmor_parser"
[   17.063749] FS-Cache: Netfs 'nfs' registered for caching
[   17.113409] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   17.237303] general protection fault: 0000 [#1] SMP 
[   17.237308] last sysfs file: /sys/module/apparmor/parameters/enabled
[   17.237310] CPU 0 
[   17.237311] Modules linked in: nfsd exportfs nfs parport_pc lockd fscache nfs_acl ppdev auth_rpcgss sunrpc vesafb snd_hda_codec_realtek snd_hda_intel snd_hda_codec arc4 joydev snd_hwdep snd_pcm nvidia(P) iwlagn snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq iwlcore btusb mac80211 dell_wmi snd_timer sparse_keymap dell_laptop snd_seq_device dcdbas bluetooth uvcvideo videodev psmouse serio_raw v4l2_compat_ioctl32 cfg80211 snd soundcore snd_page_alloc video coretemp lp parport mmc_block firewire_ohci ahci firewire_core sdhci_pci sdhci crc_itu_t r8169 libahci
[   17.237346] 
[   17.237348] Pid: 1125, comm: Xorg Tainted: P            2.6.38-11-generic #48-Ubuntu Dell Inc. Vostro1710/0X805C
[   17.237353] RIP: 0010:[<ffffffffa074c3a8>]  [<ffffffffa074c3a8>] nv_acpi_add+0x218/0x360 [nvidia]
[   17.237710] RSP: 0018:ffff8801129e5988  EFLAGS: 00010293
[   17.237712] RAX: ffff88011a2596e0 RBX: ffff88013598b028 RCX: 0000000000000001
[   17.237714] RDX: ffff88013f804368 RSI: 0000000000000282 RDI: 0000000000000282
[   17.237716] RBP: ffff8801129e5a08 R08: 0000000000000000 R09: ffff880134c51d80
[   17.237718] R10: 0000000000000002 R11: ffff8801129e58f8 R12: ffff88013598a800
[   17.237720] R13: 0000000000000000 R14: ffff88013598a018 R15: ffff8801129e59c8
[   17.237722] FS:  00007fc39fb068a0(0000) GS:ffff8800bfc00000(0000) knlGS:0000000000000000
[   17.237725] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   17.237726] CR2: 00007fc39fb36000 CR3: 0000000113cd4000 CR4: 00000000000006f0
[   17.237728] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   17.237730] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   17.237733] Process Xorg (pid: 1125, threadinfo ffff8801129e4000, task ffff88011294c4a0)
[   17.237734] Stack:
[   17.237735]  ffff880113e8e300 ffff88013598a000 0000000000000001 0000000000000000
[   17.237739]  0000000000000000 0000000000000000 ffff880100000001 ffff8801129e5998
[   17.237742]  0000000000000001 ffff880113e8e3c0 ffff880100000000 ffff88013598a350
[   17.237746] Call Trace:
[   17.237752]  [<ffffffff8133ab17>] acpi_device_probe+0x50/0x122
[   17.237756]  [<ffffffff813bada8>] really_probe+0x68/0x190
[   17.237759]  [<ffffffff813bb0b5>] driver_probe_device+0x45/0x70
[   17.237762]  [<ffffffff813bb18b>] __driver_attach+0xab/0xb0
[   17.237764]  [<ffffffff813bb0e0>] ? __driver_attach+0x0/0xb0
[   17.237767]  [<ffffffff813b9f2e>] bus_for_each_dev+0x5e/0x90
[   17.237770]  [<ffffffff813babfe>] driver_attach+0x1e/0x20
[   17.237772]  [<ffffffff813ba765>] bus_add_driver+0xc5/0x280
[   17.237775]  [<ffffffff813bb426>] driver_register+0x76/0x140
[   17.237777]  [<ffffffff8133b3d0>] acpi_bus_register_driver+0x43/0x45
[   17.237917]  [<ffffffffa074c00f>] nv_acpi_init+0x14f/0x190 [nvidia]
[   17.238056]  [<ffffffffa0743dbf>] nv_kern_ctl_open+0x7f/0xb0 [nvidia]
[   17.238195]  [<ffffffffa074506b>] nv_kern_open+0x49b/0x6c0 [nvidia]
[   17.238199]  [<ffffffff81168f9a>] chrdev_open+0xda/0x1f0
[   17.238202]  [<ffffffff81168ec0>] ? chrdev_open+0x0/0x1f0
[   17.238205]  [<ffffffff81162d3e>] __dentry_open+0xce/0x2f0
[   17.238208]  [<ffffffff8116ef83>] ? generic_permission+0x23/0xc0
[   17.238211]  [<ffffffff81164231>] nameidata_to_filp+0x71/0x80
[   17.238214]  [<ffffffff81173438>] finish_open+0xc8/0x1b0
[   17.238216]  [<ffffffff81172627>] ? do_path_lookup+0x87/0x160
[   17.238219]  [<ffffffff81173bf8>] do_filp_open+0x2c8/0x7c0
[   17.238223]  [<ffffffff812e6c77>] ? __strncpy_from_user+0x27/0x60
[   17.238228]  [<ffffffff81180f27>] ? alloc_fd+0xf7/0x150
[   17.238230]  [<ffffffff811642aa>] do_sys_open+0x6a/0x150
[   17.238233]  [<ffffffff8116f042>] ? path_put+0x22/0x30
[   17.238235]  [<ffffffff811643b0>] sys_open+0x20/0x30
[   17.238238]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
[   17.238240] Code: 00 00 00 48 8b 7a 08 48 c7 c2 10 bb 74 a0 e8 82 be bf e0 85 c0 0f 85 88 00 00 00 83 3d 41 6a 3c 00 02 74 1a 48 8b 05 90 6c 3c 00 <65> ff 00 44 8b 0d 76 d2 35 e1 45 85 c9 0f 85 ee 00 00 00 48 8b 
[   17.238267] RIP  [<ffffffffa074c3a8>] nv_acpi_add+0x218/0x360 [nvidia]
[   17.238406]  RSP <ffff8801129e5988>
[   17.238409] ---[ end trace bcb1866f08343ca3 ]---

```With all the nv_ lines near the bottom, it looks like it is due to some xorg conflict, but i'm not good with kernel voodoo. I'll try reinstalling the drivers.

Syslog:
```

Aug 17 09:25:58 pjd99-work NetworkManager[962]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Aug 17 09:28:59 pjd99-work zmdc[2601]: INF [Starting pending process, zmc -d /dev/video0]
Aug 17 09:28:59 pjd99-work zmdc[2601]: INF ['zmc -d /dev/video0' starting at 11/08/17 09:28:59, pid = 5111]
Aug 17 09:28:59 pjd99-work zmdc[5111]: INF ['zmc -d /dev/video0' started at 11/08/17 09:28:59]
Aug 17 09:28:59 pjd99-work zmc_dvideo0[5111]: INF [Debug Level = 0, Debug Log = <none>]
Aug 17 09:28:59 pjd99-work zmc_dvideo0[5111]: INF [Starting Capture]
Aug 17 09:28:59 pjd99-work zmc_dvideo0[5111]: FAT [Failed to open video device /dev/video0: Permission denied]
Aug 17 09:28:59 pjd99-work zmc_dvideo0[5111]: INF [Got signal 6 (Aborted), exiting and forcing backtrace]
Aug 17 09:28:59 pjd99-work zmdc[2601]: ERR ['zmc -d /dev/video0' exited abnormally, exit status 6]

```

---

### Post by psynoxious on 2011-08-22
I have same problem. I've updated kernel on version 2.6.38-11. In normal mode it freezes at loading screen. In recovery mode i've got a lot of "errors". Something like this: 
ata8: exception Emask 0x0 SErr 0x4060000 action 0xe frozen :confused:
please help me, i'm sick of it :cry:
P.S.: i'm sorry for my bad english and linux knowledge - i'm newbie

---

### Post by pjd99 on 2011-08-27
So, finally got some time and reinstalled nv-common, 2.8.38-11 and the nVidia driver (270.something, in windows atm), and now the previous versions that were working are now displaying the same symptoms. Can only boot in recovery mode. It's gone from bad to worse. 

Back to google to see if this problem is happening to anyone else.... 11.04 just keeps giving me reasons to drop Ubuntu altogether. :(

EDIT: Search revealed that it might be due to linking gcc to the older version on my machine. Does the nVidia driver supplied by Ubuntu require any compilation against the kernel headers? I thought they were just binaries.

---

### Post by el_koraco on 2011-08-27
You should boot into the working kernel, remove the Nvidia driver, boot into the new kernel, and install the driver there.

---

### Post by pjd99 on 2011-08-27
> **el_koraco said:**
> You should boot into the working kernel, remove the Nvidia driver, boot into the new kernel, and install the driver there.

That's what I tried and now none of them will boot with the nvidia driver. I've mostly given up now, and am using the nv driver which is at least giving me a usable system... Tried reinstalling the drivers after linking gcc back to 4.5, but no help.

Hmm, may not be quite usable after all, minimise firefox takes a few seconds, and no other processes are running except 2 conky scripts...

---

### Post by VOT Productions on 2011-08-27
I know this applies to ATI, but may apply to Mvidia as well.
Have you got the linux-headers-2.6.38-11?

---

### Post by pjd99 on 2011-08-30
Fixed it, but not quite sure how. Purged nvidia-current and reinstalled, blacklisted nouveau, and now its booting fine again. nVidia logo appeared briefly at gdm start.

Thanks for the suggestions, won't mark it as solved yet as I'm not quite sure what solved it...

---

### Post by fig_wright on 2011-09-18
I have this exact problem. For me booting back into 2.6.38-10 works. Definitely seems to be Nvidia driver related. I have an old 6200. I've spent far too long bashing my head against walls with Ubuntu 11.04 to bother spending any more time trying to fix this, so I'll uninstall 2.6.38-11 and just wait for the next kernel. I have to say that I've seen more update breakages with Ubuntu recently than ever before. This is seriously starting to become problematic.

---

### Post by fig_wright on 2011-09-18
So I'm an idiot and spent more time on this... in the hope that it might help someone here. The following are log errors that might be related to this:

```
messages.log

Sep 18 16:26:19 hostname kernel: [   10.160064] uvesafb: Getting VBE info block fai
led (eax=0x4f00, err=1)
Sep 18 16:26:19 hostname kernel: [   10.160187] uvesafb: vbe_init() failed with -22
Sep 18 16:26:19 hostname kernel: [   10.160306] uvesafb: probe of uvesafb.0 failed 
with error -22

Sep 18 16:26:28 hostname gdm-session-worker[2668]: GLib-GObject-CRITICAL:
 g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

```

---

### Post by pjd99 on 2011-10-16
Ok. I was able to reproduce the problem when trying to patch my iwlagn drivers to use the aircrack-ng suite.

After installing the patched wireless drivers I wasn't able to load them. While trying to restore functionality I deleted the entire "updates" directory, including the dkms modules for the nVidia driver.

Trying to re-install the video driver resulted in the same problem as before, hang during boot. Eventually traced the problem back to the gcc version that was being used to build the dkms module. Kernel was compiled with gcc-4.5, and I had linked to gcc-4.4 so I could run Xilinx System Generator (Simulink) models.

Long story short, ensure the correct version of gcc is being used to build the nVidia dkms modules. I've modified my Xilinx sysgen launcher to modify the path before and after running, as it doesn't support the CC env variable. i.e. "export CC=/usr/bin/gcc-4.4". 

Thread marked as solved.

---

