---
title: "Proprietary NVIDIA driver abruptly stopped working"
date: 2011-01-06
forum: General Help
---

### Post by naitsab on 2011-01-06
Hello,
Two days ago I updated my pc to 10.10. Because I was using kde before and wanted to change to gnome i did a fresh install keeping my /home partition.
I'm using a rather old sony vaio laptop with an NVIDIA GeForce FX5600 Go graphic card. It seems that the nouveau driver is not supporting my graphic card so i had to disable it in order to run the live cd. After that I installed the proprietary nvidia driver using jockey. That worked fine until I did some upgrades and rebooted (i dont remember wich packages were updated[i have backports enabled in software sources]). After the restart i ended up with a black screen but gdm seemed to have started. booting into text mode an running
```
apt purge nvidia* xserver-xorg-video-nouveau
apt reinstall xserver-xorg-video-nv
rm /etc/X11/xorg.conf
```
gave me the access to my system back. But I like the compositing features and need the 3D support for games and want to use the proprietary drivers. when I reinstall them i end up with a black screen again and this appears in the bootlogs
```
[   15.895589] Modules linked in: nvidia(P+) snd_intel8x0(+) snd_ac97_codec ac97_bus snd_pcm snd_seq_midi ath5k snd_rawmidi snd_seq_midi_event mac80211 snd_seq joydev ath ppdev pcmcia snd_timer snd_seq_device cfg80211 sony_laptop parport_pc psmouse yenta_socket serio_raw pcmcia_rsrc snd led_class pcmcia_core soundcore lp snd_page_alloc shpchp i2c_sis96x parport dm_raid45 xor btrfs zlib_deflate crc32c libcrc32c usbhid hid sis_agp firewire_ohci usb_storage video firewire_core output sis900 crc_itu_t mii agpgart ramzswap(C) lzo_compress
[   15.896020] 
[   15.896020] Pid: 449, comm: modprobe Tainted: P         C  2.6.35-24-generic #42-Ubuntu /PCG-GRT915M(DE)
[   15.896020] EIP: 0060:[<c020ccf0>] EFLAGS: 00210006 CPU: 0
[   15.896020] EIP is at kmem_cache_alloc+0x50/0x110
[   15.896020] EAX: c1c05b1c EBX: c07c6aa8 ECX: f92cb32d EDX: 00000000
[   15.896020] ESI: 00001ff0 EDI: 000000d0 EBP: f5c8dd7c ESP: f5c8dd50
[   15.896020]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   15.896020] Process modprobe (pid: 449, ti=f5c8c000 task=f5c9bf70 task.ti=f5c8c000)
[   15.896020] Stack:
[   15.896020]  f67f2b00 f5c8dd68 c0270f11 f92cb32d f5c8dde0 f5c8dde0 000000d0 00200246
[   15.896020] <0> f70f1800 f957d880 f957d8b0 f5c8ddec f92cb32d 00000001 f9371238 000010de
[   15.896020] <0> 0000031a 00030000 f5c8dda8 c05c8599 f5c8dde0 f5c8dde0 f5e658d0 f70d8600
[   15.896020] Call Trace:
[   15.896020]  [<c0270f11>] ? sysfs_find_dirent+0x31/0x50
[   15.896020]  [<f92cb32d>] ? nv_kern_probe+0x4d/0x710 [nvidia]
[   15.896020]  [<f92cb32d>] ? nv_kern_probe+0x4d/0x710 [nvidia]
[   15.896020]  [<c05c8599>] ? mutex_lock+0x19/0x40
[   15.896020]  [<c0272307>] ? sysfs_do_create_link+0xb7/0x1d0
[   15.896020]  [<c0271187>] ? sysfs_new_dirent+0x67/0x100
[   15.896020]  [<c027158a>] ? sysfs_addrm_finish+0x1a/0xb0
[   15.896020]  [<c036c14e>] ? pci_match_device+0xbe/0xd0
[   15.896020]  [<c036bfe3>] ? local_pci_probe+0x13/0x20
[   15.896020]  [<c036cf98>] ? pci_device_probe+0x68/0x90
[   15.896020]  [<c0400be0>] ? really_probe+0x50/0x150
[   15.896020]  [<c0408267>] ? pm_runtime_barrier+0x57/0xb0
[   15.896020]  [<c0400d1c>] ? driver_probe_device+0x3c/0x60
[   15.896020]  [<c0400dc1>] ? __driver_attach+0x81/0x90
[   15.896020]  [<c04001e3>] ? bus_for_each_dev+0x53/0x80
[   15.896020]  [<c0400aae>] ? driver_attach+0x1e/0x20
[   15.896020]  [<c0400d40>] ? __driver_attach+0x0/0x90
[   15.896020]  [<c0400475>] ? bus_add_driver+0xd5/0x280
[   15.896020]  [<c036ced0>] ? pci_device_remove+0x0/0x40
[   15.896020]  [<c04010ba>] ? driver_register+0x6a/0x130
[   15.896020]  [<f922062f>] ? _nv004037rm+0x9/0xd [nvidia]
[   15.896020]  [<f91ff178>] ? _nv002984rm+0x7d/0xa2 [nvidia]
[   15.896020]  [<c036d1d5>] ? __pci_register_driver+0x45/0xb0
[   15.896020]  [<f95f81f2>] ? nvidia_init_module+0x1f2/0x80b [nvidia]
[   15.896020]  [<c01b0787>] ? tracepoint_module_notify+0x27/0x30
[   15.896020]  [<c05cd2d3>] ? notifier_call_chain+0x43/0x60
[   15.896020]  [<c0101132>] ? do_one_initcall+0x32/0x1a0
[   15.896020]  [<f95f8000>] ? nvidia_init_module+0x0/0x80b [nvidia]
[   15.896020]  [<c0180d1b>] ? sys_init_module+0x9b/0x1e0
[   15.896020]  [<c0219412>] ? sys_write+0x42/0x70
[   15.896020]  [<c05c9cc4>] ? syscall_call+0x7/0xb
[   15.896020] Code: 00 00 89 55 ec 75 5c 9c 58 8d 74 26 00 89 45 f0 fa 90 8d 74 26 00 64 8b 15 54 f0 8b c0 8b 03 8d 04 02 8b 30 85 f6 74 5e 8b 53 10 <8b> 14 16 89 10 8b 45 f0 50 9d 8d 74 26 00 85 f6 75 36 a1 84 31 
[   15.896020] EIP: [<c020ccf0>] kmem_cache_alloc+0x50/0x110 SS:ESP 0068:f5c8dd50
[   15.896020] CR2: 0000000000001ff0
[   15.896020] ---[ end trace 2da4a9eb940b8043 ]---
```
I have
kernel: 2.6.35.24.28
xserver: 2:1.9
and used
nvidia: 173.14.28

so is there anyone who can help my with this?

---

