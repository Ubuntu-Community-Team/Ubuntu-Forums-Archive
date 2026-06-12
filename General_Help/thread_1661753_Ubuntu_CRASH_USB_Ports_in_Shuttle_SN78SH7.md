---
title: "Ubuntu CRASH USB Ports in Shuttle SN78SH7/"
date: 2011-01-07
forum: General Help
---

### Post by lokidiabel on 2011-01-07
Can anyone tell me what this is and how to fix it ?! It happend with different USB devices !

[   12.384832] ------------[ cut here ]------------
[   12.384842] WARNING: at include/linux/netdevice.h:1557 rtl8187_usb_probe+0xee/0x12a [r8187l]()
[   12.384844] Hardware name: SN78S
[   12.384846] Modules linked in: snd_hda_codec_hdmi snd_hda_codec_realtek tda10023 snd_usb_audio snd_usbmidi_lib snd_rawmidi snd_seq_device r8187l(+) nvidia(P) budget_av snd_hda_intel saa7146_vv ppdev gspca_ov519 gspca_main parport_pc videobuf_dma_sg ftdi_sio snd_hda_codec usbserial videodev k10temp v4l1_compat video sunrpc videobuf_core budget_core dvb_core snd_hwdep output snd_pcm serio_raw shpchp snd_timer saa7146 ttpci_eeprom snd soundcore snd_page_alloc i2c_nforce2 lp parport usbhid hid ahci forcedeth pata_amd libahci floppy
[   12.384874] Pid: 863, comm: modprobe Tainted: P            2.6.37-11-generic #25~lucid1-Ubuntu
[   12.384876] Call Trace:
[   12.384882]  [<c014ce72>] warn_slowpath_common+0x72/0xa0
[   12.384890]  [<efb762f7>] ? rtl8187_usb_probe+0xee/0x12a [r8187l]
[   12.384896]  [<efb762f7>] ? rtl8187_usb_probe+0xee/0x12a [r8187l]
[   12.384899]  [<c014cec2>] warn_slowpath_null+0x22/0x30
[   12.384905]  [<efb762f7>] rtl8187_usb_probe+0xee/0x12a [r8187l]
[   12.384909]  [<c049851e>] usb_probe_interface+0xce/0x1b0
[   12.384912]  [<c0280d87>] ? sysfs_create_link+0x17/0x20
[   12.384916]  [<c04216dd>] really_probe+0x4d/0x150
[   12.384920]  [<c0429d34>] ? pm_runtime_barrier+0x54/0xb0
[   12.384923]  [<c042181c>] driver_probe_device+0x3c/0x60
[   12.384925]  [<c04218c1>] __driver_attach+0x81/0x90
[   12.384928]  [<c0420ce3>] bus_for_each_dev+0x53/0x80
[   12.384931]  [<c042158e>] driver_attach+0x1e/0x20
[   12.384933]  [<c0421840>] ? __driver_attach+0x0/0x90
[   12.384936]  [<c0420f81>] bus_add_driver+0xe1/0x260
[   12.384939]  [<c0421bba>] driver_register+0x6a/0x130
[   12.384942]  [<c027148a>] ? __proc_create+0xba/0x100
[   12.384945]  [<c0498251>] usb_register_driver+0x81/0x130
[   12.384947]  [<c02715d9>] ? create_proc_entry+0x59/0xa0
[   12.384953]  [<efa250f2>] rtl8187_usb_module_init+0xf2/0xfb [r8187l]
[   12.384956]  [<c0101135>] do_one_initcall+0x35/0x170
[   12.384960]  [<c0180daf>] ? set_page_attributes+0x1f/0x30
[   12.384966]  [<efa25000>] ? rtl8187_usb_module_init+0x0/0xfb [r8187l]
[   12.384969]  [<c018625b>] sys_init_module+0xdb/0x230
[   12.384972]  [<c05f5ce4>] syscall_call+0x7/0xb
[   12.384974] ---[ end trace 2fcdf5c094c01901 ]---
[   12.384975] netif_stop_queue() cannot be called b

Thank you for your help.
If this isnt the right section for this post can someone please move it ?!

Thanks

Loki

---

