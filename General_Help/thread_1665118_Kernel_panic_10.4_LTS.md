---
title: "Kernel panic 10.4 LTS"
date: 2011-01-11
forum: General Help
---

### Post by jeffrey.moncrieff on 2011-01-11
Hello

I seems to have a problem with my desktop It just starting to reboot. I am a programmer so this is a trouble some. It happens two times already. I do not think it is hardware because this is a pretty new system I had it built in may of 2010
- CPU=>AMD Althon X4 630
- Motherboard Asus M4A785A
- HD Hitchi Deskstat 1TB
 
Now I did log at the dmesg and I notice this error

  16.554427] Modules linked in: snd_hda_codec_atihdmi snd_hda_codec_via snd_hda_intel snd_hda_codec snd_pcm_oss snd_hwdep snd_mixer_oss snd_seq_dummy snd_pcm snd_seq_oss snd_seq_midi fbcon tileblit font bitblit snd_rawmidi softcursor fglrx(P) vga16fb vgastate edac_core edac_mce_amd snd_seq_midi_event asus_atk0110 snd_seq i2c_piix4 snd_timer snd_seq_device snd soundcore snd_page_alloc ppdev parport_pc shpchp lp parport usbhid hid usb_storage r8169 mii pata_atiixp ahci
[   16.554452] Pid: 1139, comm: Xorg Tainted: P           2.6.32-27-generic #49-Ubuntu
[   16.554454] Call Trace:
[   16.554460]  [<ffffffff8106604b>] warn_slowpath_common+0x7b/0xc0
[   16.554463]  [<ffffffff810660a4>] warn_slowpath_null+0x14/0x20
[   16.554465]  [<ffffffff810fa02b>] __alloc_pages_slowpath+0x44b/0x590
[   16.554468]  [<ffffffff810fa2ce>] __alloc_pages_nodemask+0x15e/0x1a0
[   16.554472]  [<ffffffff8112d257>] alloc_pages_current+0x87/0xd0
[   16.554475]  [<ffffffff810f91de>] __get_free_pages+0xe/0x50
[   16.554513]  [<ffffffffa01673d5>] KCL_MEM_AllocContiguousPageFrames+0x15/0x20 [fglrx]
[   16.554540]  [<ffffffffa016e5e3>] drm_alloc_pages+0xb3/0x230 [fglrx]
[   16.554568]  [<ffffffffa018271a>] ? MCIL_AllocateContiguousMemory+0x3a/0xe0 [fglrx]
[   16.554607]  [<ffffffffa020c028>] ? _ZN7GpsBase28GPS_AllocateContiguousMemoryEPvmjP15_ULARGE_INTEGERmmm+0x98/0xd0 [fglrx]
[   16.554644]  [<ffffffffa021b0b6>] ? _ZN23PageTableGartVmptSysMem4InitEv+0x66/0x160 [fglrx]
[   16.554681]  [<ffffffffa0218f42>] ? _ZN13GartVmptRS78015CreatePageTableEP9GpsConfig+0x52/0x200 [fglrx]
[   16.554718]  [<ffffffffa020cfdd>] ? _ZN10GPSContext18InitializeAsicGartEv+0x3d/0xf0 [fglrx]
[   16.554756]  [<ffffffffa0208a63>] ? Gps_GartInitialization+0x23/0x40 [fglrx]
[   16.554783]  [<ffffffffa01883db>] ? __gart_init+0x2eb/0x6f0 [fglrx]
[   16.554811]  [<ffffffffa0185da0>] ? gal_init+0xc0/0x160 [fglrx]
[   16.554838]  [<ffffffffa018bba2>] ? mc_heap_init+0xe2/0x200 [fglrx]
[   16.554864]  [<ffffffffa0179fea>] ? firegl_init_pcie+0x16a/0x3e0 [fglrx]
[   16.554867]  [<ffffffff810f5e7e>] ? generic_file_aio_write+0xbe/0xe0
[   16.554871]  [<ffffffff812520da>] ? security_capable+0x2a/0x30
[   16.554897]  [<ffffffffa0179e80>] ? firegl_init_pcie+0x0/0x3e0 [fglrx]
[   16.554922]  [<ffffffffa0175b5a>] ? firegl_ioctl+0x1ea/0x250 [fglrx]
[   16.554946]  [<ffffffffa016b8d6>] ? ip_firegl_ioctl+0x16/0x20 [fglrx]
[   16.554950]  [<ffffffff811534cc>] ? vfs_ioctl+0x7c/0xa0
[   16.554952]  [<ffffffff81153721>] ? do_vfs_ioctl+0x81/0x380
[   16.554955]  [<ffffffff811433a2>] ? vfs_write+0x132/0x1a0
[   16.554957]  [<ffffffff81153aa1>] ? sys_ioctl+0x81/0xa0
[   16.554961]  [<ffffffff815448fe>] ? do_device_not_available+0xe/0x10
[   16.554965]  [<ffffffff810121b2>] ? system_call_fastpath+0x16/0x1b
[   16.554967] ---[ end trace 80d000a8153ae0b8 ]---


I only thing I added to the kernel is the modules for vmware. 

Linux jeff-desktop 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux

---

### Post by dcstar on 2011-01-12
> **jeffrey.moncrieff said:**
> 
.......
**I only thing I added to the kernel is the modules for vmware.** 

Linux jeff-desktop 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux

What does "I added to the kernel" actually mean?

---

