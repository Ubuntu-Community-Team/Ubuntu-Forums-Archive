---
title: "Hauppauge WinTV IR modules broken in Natty?  Previously working in 10.10."
date: 2011-08-07
forum: General Help
---

### Post by slycker on 2011-08-07
Similar to many out there, I am having problems with Natty AMD64 (Ubuntu 11.04) and LIRC/IR-Keytables.
 

 I have a Hauppauge WinTV card (Bt878)  (TV card and IR receiver/transmitter) that worked (for the first time) automatically with 10.10 and LIRC.  I recently moved over to 11.04, copied my LIRC config files over (hardware.conf, lircd.conf, lircmd.conf, etc), and received the error &#8220;couldn't find any node at /sys/class/rc/rc*&#8221;
 

 The modules I had previously been successful with were: lirc_dev & lirc_i2c, as is apropriate for my speific card.
 

 I then learned that Natty incorporated a lot of RC elements in to the kernel, and tried following:
 [http://forum.xbmc.org/showthread.php?t=101151](http://forum.xbmc.org/showthread.php?t=101151)
 Which suggested removing lirc.  At this point, ir-keytable also gives the same error about no node at /sys/class/rc/rc*
 

 I think that I am having a problem with the correct driver being loaded for my card.  When I look at a dmesg, the relevant section is:  (note: I'm not sure if this dmesg was from before or after I uninstalled LIRC and just tried keytables)
 

```
[    8.074866] bttv: driver version 0.9.18 loaded 
 [    8.074870] bttv: using 8 buffers with 2080k (520 pages) each for capture 
 [    8.075367] bttv: Bt8xx card found (0). 
 [    8.075398] bttv 0000:03:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21 
 [    8.075411] bttv0: Bt878 (rev 17) at 0000:03:06.0, irq: 21, latency: 64, mmio: 0xfdfff000 
 [    8.080077] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb 
 [    8.080082] bttv0: using: Hauppauge (bt878) [card=10,autodetected] 
 [    8.080133] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init] 
 [    8.082637] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5] 
 [    8.097937] lirc_dev: IR Remote Control driver registered, major 61  
 [    8.098847] ir_lirc_codec: Unknown symbol lirc_dev_fop_poll (err 0) 
 [    8.099097] ir_lirc_codec: Unknown symbol lirc_dev_fop_open (err 0) 
 [    8.099193] ir_lirc_codec: disagrees about version of symbol lirc_get_pdata 
 [    8.099195] ir_lirc_codec: Unknown symbol lirc_get_pdata (err -22) 
 [    8.099291] ir_lirc_codec: Unknown symbol lirc_dev_fop_close (err 0) 
 [    8.099373] ir_lirc_codec: Unknown symbol lirc_dev_fop_read (err 0) 
 [    8.099436] ir_lirc_codec: disagrees about version of symbol lirc_register_driver 
 [    8.099438] ir_lirc_codec: Unknown symbol lirc_register_driver (err -22) 
 [    8.099609] ir_lirc_codec: Unknown symbol lirc_dev_fop_ioctl (err 0) 
 [    8.110181] lp0: using parport0 (interrupt-driven). 
 [    8.118605] [drm] radeon defaulting to kernel modesetting. 
 [    8.118608] [drm] radeon kernel modesetting enabled. 
 [    8.121013] tveeprom 0-0050: Hauppauge model 44981, rev E1B2, serial# 10068694 
 [    8.121016] tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 50) 
 [    8.121019] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08) 
 [    8.121021] tveeprom 0-0050: audio processor is None (idx 0) 
 [    8.121023] tveeprom 0-0050: decoder processor is BT878 (idx 14) 
 [    8.121026] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter 
 [    8.121028] bttv0: Hauppauge eeprom indicates model#44981 
 [    8.121030] bttv0: tuner type=50 

```The 3rd last line makes it seem that the IR capabilities have been recognized &#8211; further confusing me as to why no /sys/class/rc/rc* has been registered.   
 I've attached an unedited copy of my proc/bus/pci/devices, and below is my lsmod.  I wouyld appreciate any direction any of you could provide with this, as I haven't been able to find a solution yet with my searches online.
 

```
Module                  Size  Used by 
 cx8800                 38634  0  
 cx88xx                 88785  1 cx8800 
 ivtv                  163601  0  
 cx2341x                28272  1 ivtv 
 lirc_i2c               13433  0  
 binfmt_misc            17565  1  
 snd_hda_codec_hdmi     28167  1  
 snd_hda_codec_via      62470  1  
 tuner_simple           18526  1  
 tuner_types            24211  1 tuner_simple 
 tuner                  27386  1  
 snd_hda_intel          33211  1  
 tvaudio                33471  0  
 snd_hda_codec         103768  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel 
 snd_hwdep              13604  1 snd_hda_codec 
 tda7432                13242  0  
 snd_seq_midi           13324  0  
 msp3400                36336  0  
 radeon                982152  3  
 snd_rawmidi            30386  1 snd_seq_midi 
 snd_seq_midi_event     14899  1 snd_seq_midi 
 lirc_dev               17852  1 lirc_i2c 
 ttm                    76664  1 radeon 
 snd_seq                61585  2 snd_seq_midi,snd_seq_midi_event 
 snd_bt87x              19128  1  
 drm_kms_helper         42136  1 radeon 
 bttv                  128715  0  
 snd_pcm                96297  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_bt87x 
 ir_sony_decoder        12549  0  
 v4l2_common            17647  9 cx8800,cx88xx,ivtv,cx2341x,tuner,tvaudio,tda7432,msp3400,bttv 
 snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq 
 videodev               82052  10 cx8800,cx88xx,ivtv,cx2341x,tuner,tvaudio,tda7432,msp3400,bttv,v4l2_common 
 v4l2_compat_ioctl32    17042  1 videodev 
 videobuf_dma_sg        19307  3 cx8800,cx88xx,bttv 
 videobuf_core          26134  4 cx8800,cx88xx,bttv,videobuf_dma_sg 
 btcx_risc              13640  3 cx8800,cx88xx,bttv 
 ir_jvc_decoder         12546  0  
 drm                   227459  5 radeon,ttm,drm_kms_helper 
 asus_atk0110           17976  0  
 i2c_algo_bit           13400  4 cx88xx,ivtv,radeon,bttv 
 ppdev                  17113  0  
 ir_rc6_decoder         12546  0  
 ir_rc5_decoder         12546  0  
 parport_pc             36959  1  
 ir_nec_decoder         12546  0  
 psmouse                73535  0  
 rc_core                26918  7 cx88xx,bttv,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder 
 tveeprom               21249  3 cx88xx,ivtv,bttv 
 snd_timer              29602  2 snd_seq,snd_pcm 
 snd                    67346  15 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_seq,snd_bt87x,snd_pcm,snd_seq_device,snd_timer 
 sp5100_tco             13744  0  
 edac_core              53845  0  
 edac_mce_amd           23464  0  
 k10temp                13119  0  
 i2c_piix4              13303  0  
 joydev                 17606  0  
 soundcore              12680  1 snd 
 snd_page_alloc         18529  3 snd_hda_intel,snd_bt87x,snd_pcm 
 lp                     17789  0  
 serio_raw              13166  0  
 parport                46458  3 ppdev,parport_pc,lp 
 shpchp                 37297  0  
 hid_logitech           17693  0  
 ff_memless             13097  1 hid_logitech 
 usb_storage            53538  1  
 usbhid                 46956  1 hid_logitech 
 hid                    91020  2 hid_logitech,usbhid 
 uas                    17996  0  
 ahci                   25951  4  
 r8169                  48022  0  
 pata_atiixp            13165  0  
 libahci                26642  1 ahci 

```UDEV - relevant section for the whole WinTV Card
```

P: /devices/pci0000:00/0000:00:14.4
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:14.4
E: PCI_CLASS=60401
E: PCI_ID=1002:4384
E: PCI_SUBSYS_ID=0000:0000
E: PCI_SLOT_NAME=0000:00:14.4
E: MODALIAS=pci:v00001002d00004384sv00000000sd00000000bc06sc04i01
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:14.4/0000:03:06.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:14.4/0000:03:06.0
E: DRIVER=bttv
E: PCI_CLASS=40000
E: PCI_ID=109E:036E
E: PCI_SUBSYS_ID=0070:13EB
E: PCI_SLOT_NAME=0000:03:06.0
E: MODALIAS=pci:v0000109Ed0000036Esv00000070sd000013EBbc04sc00i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:14.4/0000:03:06.0/i2c-0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:14.4/0000:03:06.0/i2c-0
E: SUBSYSTEM=i2c

P: /devices/pci0000:00/0000:00:14.4/0000:03:06.0/i2c-0/0-0061
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:14.4/0000:03:06.0/i2c-0/0-0061
E: DRIVER=tuner
E: MODALIAS=i2c:tuner
E: SUBSYSTEM=i2c

P: /devices/pci0000:00/0000:00:14.4/0000:03:06.0/i2c-0/0-0071
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:14.4/0000:03:06.0/i2c-0/0-0071
E: DRIVER=i2c ir driver
E: MODALIAS=i2c:ir_video
E: SUBSYSTEM=i2c

P: /devices/pci0000:00/0000:00:14.4/0000:03:06.0/i2c-0/0-0071/lirc/lirc0
N: lirc0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:14.4/0000:03:06.0/i2c-0/0-0071/lirc/lirc0
E: MAJOR=61
E: MINOR=0
E: DEVNAME=/dev/lirc0
E: SUBSYSTEM=lirc

P: /devices/pci0000:00/0000:00:14.4/0000:03:06.0/video4linux/vbi0
N: vbi0
S: v4l/by-path/pci-0000:03:06.0-video-index1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:14.4/0000:03:06.0/video4linux/vbi0
E: MAJOR=81
E: MINOR=1
E: DEVNAME=/dev/vbi0
E: SUBSYSTEM=video4linux
E: ID_V4L_VERSION=2
E: ID_V4L_PRODUCT=BT878 video (Hauppauge (bt878))
E: ID_V4L_CAPABILITIES=:capture:video_overlay:tuner:
E: ID_PATH=pci-0000:03:06.0
E: DEVLINKS=/dev/v4l/by-path/pci-0000:03:06.0-video-index1
E: TAGS=:udev-acl:

P: /devices/pci0000:00/0000:00:14.4/0000:03:06.0/video4linux/video0
N: video0
S: v4l/by-path/pci-0000:03:06.0-video-index0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:14.4/0000:03:06.0/video4linux/video0
E: MAJOR=81
E: MINOR=0
E: DEVNAME=/dev/video0
E: SUBSYSTEM=video4linux
E: ID_V4L_VERSION=2
E: ID_V4L_PRODUCT=BT878 video (Hauppauge (bt878))
E: ID_V4L_CAPABILITIES=:capture:video_overlay:tuner:
E: ID_PATH=pci-0000:03:06.0
E: DEVLINKS=/dev/v4l/by-path/pci-0000:03:06.0-video-index0
E: TAGS=:udev-acl:

P: /devices/pci0000:00/0000:00:14.4/0000:03:06.1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:14.4/0000:03:06.1
E: DRIVER=Bt87x
E: PCI_CLASS=48000
E: PCI_ID=109E:0878
E: PCI_SUBSYS_ID=0070:13EB
E: PCI_SLOT_NAME=0000:03:06.1
E: MODALIAS=pci:v0000109Ed00000878sv00000070sd000013EBbc04sc80i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:14.4/0000:03:06.1/sound/card1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:14.4/0000:03:06.1/sound/card1
E: SUBSYSTEM=sound
E: SOUND_INITIALIZED=1
E: ID_VENDOR_FROM_DATABASE=Brooktree Corporation
E: ID_MODEL_FROM_DATABASE=Bt878 Audio Capture
E: ID_BUS=pci
E: ID_VENDOR_ID=0x109e
E: ID_MODEL_ID=0x0878
E: ID_PATH=pci-0000:03:06.1

P: /devices/pci0000:00/0000:00:14.4/0000:03:06.1/sound/card1/pcmC1D0c
N: snd/pcmC1D0c
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:14.4/0000:03:06.1/sound/card1/pcmC1D0c
E: MAJOR=116
E: MINOR=3
E: DEVNAME=/dev/snd/pcmC1D0c
E: SUBSYSTEM=sound
E: TAGS=:udev-acl:

P: /devices/pci0000:00/0000:00:14.4/0000:03:06.1/sound/card1/pcmC1D1c
N: snd/pcmC1D1c
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:14.4/0000:03:06.1/sound/card1/pcmC1D1c
E: MAJOR=116
E: MINOR=2
E: DEVNAME=/dev/snd/pcmC1D1c
E: SUBSYSTEM=sound
E: TAGS=:udev-acl:

P: /devices/pci0000:00/0000:00:14.4/0000:03:06.1/sound/card1/controlC1
N: snd/controlC1
S: snd/by-path/pci-0000:03:06.1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:14.4/0000:03:06.1/sound/card1/controlC1
E: MAJOR=116
E: MINOR=4
E: DEVNAME=/dev/snd/controlC1
E: SUBSYSTEM=sound
E: ID_PATH=pci-0000:03:06.1
E: DEVLINKS=/dev/snd/by-path/pci-0000:03:06.1
E: TAGS=:udev-acl:

P: /devices/pci0000:00/0000:00:14.4/pci_bus/0000:03
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:14.4/pci_bus/0000:03
E: SUBSYSTEM=pci_bus

```cat proc/bus/pci/devices:
```

0000    10229601    0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0    
0008    10439602    0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0    
0050    10229609    28                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0    pcieport
0088    10024390    16                c001                b001                a001                9001                8001            fe8ffc00                   0                   8                   4                   8                   4                  10                 400                   0    ahci
0090    10024397    10            fe8fe000                   0                   0                   0                   0                   0                   0                1000                   0                   0                   0                   0                   0                   0    ohci_hcd
0091    10024398    10            fe8fd000                   0                   0                   0                   0                   0                   0                1000                   0                   0                   0                   0                   0                   0    ohci_hcd
0092    10024396    11            fe8ff800                   0                   0                   0                   0                   0                   0                 100                   0                   0                   0                   0                   0                   0    ehci_hcd
0098    10024397    12            fe8fc000                   0                   0                   0                   0                   0                   0                1000                   0                   0                   0                   0                   0                   0    ohci_hcd
0099    10024398    12            fe8fb000                   0                   0                   0                   0                   0                   0                1000                   0                   0                   0                   0                   0                   0    ohci_hcd
009a    10024396    13            fe8ff400                   0                   0                   0                   0                   0                   0                 100                   0                   0                   0                   0                   0                   0    ehci_hcd
00a0    10024385    0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0    
00a1    1002439c    10                 1f0                 3f6                 170                 376                ff01                   0                   0                   8                   0                   8                   0                  10                   0                   0    pata_atiixp
00a2    10024383    10            fe8f4004                   0                   0                   0                   0                   0                   0                4000                   0                   0                   0                   0                   0                   0    HDA Intel
00a3    1002439d    0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0    
00a4    10024384    0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0    
00a5    10024399    12            fe8fa000                   0                   0                   0                   0                   0                   0                1000                   0                   0                   0                   0                   0                   0    ohci_hcd
00c0    10221200    0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0    
00c1    10221201    0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0    
00c2    10221202    0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0    
00c3    10221203    0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0    
00c4    10221204    0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0                   0    
0128    10029710    12            d0000008                d001            feaf0000                   0                   0            fe900000                   2            10000000                 100               10000                   0                   0              100000                   0    radeon
0129    1002970f    13            feae8000                   0                   0                   0                   0                   0                   0                4000                   0                   0                   0                   0                   0                   0    HDA Intel
0200    10ec8168    29                e801                   0            fdeff00c                   0            fdef800c                   0            febf0000                 100                   0                1000                   0                4000                   0               10000    r8169
0330    109e036e    15            fdfff008                   0                   0                   0                   0                   0                   0                1000                   0                   0                   0                   0                   0                   0    bttv
0331    109e0878    15            fdffe008                   0                   0                   0                   0                   0                   0                1000                   0                   0                   0                   0                   0                   0    Bt87x



```<update... It looks like this post addresses some of what has happened behind the scenes>
> ...
 First up, and I&#8217;ve seen multiple users baffled by this already, there were i2c changes in 2.6.33 (iirc) that necessitated some major changes in core device drivers exporting i2c interface ids, as well as in device drivers looking to bind to those exported i2c interfaces. Historically, lirc_i2c would bind to just about anything that was listening at the right i2c address. Now the i2c subsystem enforces only allowing the driver to bind to an interface that actually advertises an exported id the driver claims to support. So certain Hauppauge WinTV PVR-150 cards that have a Zilog z8 IR chip on them used to work with lirc_i2c stopped working, as the lirc_i2c driver doesn&#8217;t claim to support an i2c device id of ir_rx_z8f0811_haup. However, the lirc_zilog driver *does* claim to support ir_rx_z8f0811_haup. So the answer to this problem is for people to use lirc_zilog instead (after acquiring the requisite &#8220;firmware&#8221; blob that it needs &#8212; google knows where to find it, its also covered somewhere on this site in a blog posting on the hdpvr&#8217;s IR part). Note that lirc_i2c is likely to disappear entirely in the relatively near future, supplanted entirely by ir-kbd-i2c, which is now ported to ir-core, and its input layer event device can be snarfed for keypress data. It even works with ir_rx_z8f0811_haup devices (lirc_i2c *could* be made to support them as well, but I see no point in it, when its going away anyway)
 ...
 [[http://wilsonet.com/?page_id=95](http://wilsonet.com/?page_id=95)]

I've never been directed to google a firmware blob, and haven't yet found anything specific to my card.  Does anyone have some direction as to an approach to this?  Would it be easier (or possible) to try disable ubuntu's ir-core elements and try stick to my old friendly lirc with working lirc_i2c components?
 

 Thanks!

---

### Post by slycker on 2011-08-16
Well, I bailed from this remote.  I figured my time was worth more than the $25 and that small bit of pride that likes to squeeze more use out of old cards.

I ended up getting the Adesso ARC-1100, which worked out of the box with all my applications, including XBMC, right out of the box.

Instead of using LIRC, it seems that it registers itself both as a keyboard and a mouse (it has a small d-pad, including a 'right-click' and 'left-click' button.

[http://www.mythtv.org/wiki/Adesso_ARC-1100](http://www.mythtv.org/wiki/Adesso_ARC-1100)

All that is left is sorting out a few of the keymaps (getting the green windows media centre button to launch xbmc, then within xbmc getting it to go home, and using all of the 'extra buttons' for example).

I'm happy, and would highly recommend this remote, as it lets me exit xbmc, do a given task, and pop back into it without having to break-out my keyboard and mouse.

---

