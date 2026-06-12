---
title: "TV Signal degrades"
date: 2010-04-12
forum: General Help
---

### Post by Gorlist on 2010-04-12
Hi, ive got a slight tv card/signal problem where for some reason that between 5 to 20 minutes of watching the TV signal degrades, may cut out completely then after about a minute returns to normal. 

Doesn't occur in Windows. 

Ive tried a number of programs and it appears to be non specific (MythTV, MeTV, Kaffiene). 

Freeview UK. Ive checked all of the obvious, and its not a TV card/aerial problem. Ubuntu 9.04/9.10. 

Best Regards,

---

### Post by dannyboy79 on 2010-04-12
can't help without knowing what tv card you're using, what drivers you're using for the tv card (shows in either modprobe or dmesg outputs). what kernel, what ubuntu version. please provide info about system. also, kern.log, syslog, and other related log files, mythtv-backend.log etc etc

---

### Post by Gorlist on 2010-04-12
sorry that was bit daft :) HVR-1200, Ubuntu 9.10.

```
grep -i dvb /var/log/messages
Apr 11 10:09:11 james-desktop kernel: [ 1389.320060] Modules linked in: binfmt_misc ppdev snd_hda_codec_atihdmi snd_hda_codec_analog tda18271 tda8290 tda10048 snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event wacom snd_hda_intel snd_hda_codec joydev snd_hwdep snd_seq snd_pcm_oss lirc_mceusb snd_mixer_oss lirc_dev cx23885 cx2341x videobuf_dma_sg v4l2_common videodev iptable_filter v4l1_compat ip_tables x_tables fglrx(P) snd_pcm asus_atk0110 snd_timer v4l2_compat_ioctl32 snd_seq_device videobuf_dvb dvb_core snd videobuf_core btcx_risc tveeprom soundcore snd_page_alloc amd64_edac_mod psmouse edac_core serio_raw i2c_piix4 lp parport hid_logitech ff_memless usbhid ohci1394 ieee1394 r8169 mii
Apr 11 10:11:44 james-desktop kernel: [   19.386757] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
Apr 11 10:11:44 james-desktop kernel: [   19.386765] cx23885_dvb_register() allocating 1 frontend(s)
Apr 11 10:11:44 james-desktop kernel: [   19.386767] cx23885[0]: cx23885 based dvb card
Apr 11 10:11:45 james-desktop kernel: [   21.021998] DVB: registering new adapter (cx23885[0])
Apr 11 10:11:45 james-desktop kernel: [   21.022002] DVB: registering adapter 0 frontend 0 (NXP TDA10048HN DVB-T)...
Apr 11 11:06:21 james-desktop kernel: [   19.454003] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
Apr 11 11:06:21 james-desktop kernel: [   19.454011] cx23885_dvb_register() allocating 1 frontend(s)
Apr 11 11:06:21 james-desktop kernel: [   19.454093] cx23885[0]: cx23885 based dvb card
Apr 11 11:06:22 james-desktop kernel: [   21.112016] DVB: registering new adapter (cx23885[0])
Apr 11 11:06:22 james-desktop kernel: [   21.112020] DVB: registering adapter 0 frontend 0 (NXP TDA10048HN DVB-T)...
Apr 11 12:54:23 james-desktop kernel: [ 3925.560062] Modules linked in: binfmt_misc ppdev snd_hda_codec_atihdmi snd_hda_codec_analog tda18271 tda8290 tda10048 asus_atk0110 psmouse serio_raw wacom snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer lirc_mceusb snd_seq_device lirc_dev iptable_filter i2c_piix4 snd ip_tables x_tables soundcore snd_page_alloc amd64_edac_mod fglrx(P) edac_core joydev cx23885 cx2341x videobuf_dma_sg v4l2_common videodev v4l1_compat v4l2_compat_ioctl32 videobuf_dvb dvb_core videobuf_core btcx_risc tveeprom lp parport hid_logitech ff_memless usbhid ohci1394 ieee1394 r8169 mii
Apr 11 14:43:17 james-desktop kernel: [ 4790.818171] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
Apr 11 14:43:17 james-desktop kernel: [ 4790.818185] cx23885 0000:03:00.0: firmware: requesting dvb-fe-tda10048-1.0.fw
Apr 11 14:43:17 james-desktop firmware.sh[6693]: Cannot find  firmware file 'dvb-fe-tda10048-1.0.fw'
Apr 11 17:29:34 james-desktop kernel: [   19.581293] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
Apr 11 17:29:34 james-desktop kernel: [   19.581300] cx23885_dvb_register() allocating 1 frontend(s)
Apr 11 17:29:34 james-desktop kernel: [   19.581438] cx23885[0]: cx23885 based dvb card
Apr 11 17:29:35 james-desktop kernel: [   21.152007] DVB: registering new adapter (cx23885[0])
Apr 11 17:29:35 james-desktop kernel: [   21.152011] DVB: registering adapter 0 frontend 0 (NXP TDA10048HN DVB-T)...
Apr 11 19:52:57 james-desktop kernel: [   19.503991] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
Apr 11 19:52:57 james-desktop kernel: [   19.503999] cx23885_dvb_register() allocating 1 frontend(s)
Apr 11 19:52:57 james-desktop kernel: [   19.504001] cx23885[0]: cx23885 based dvb card
Apr 11 19:52:58 james-desktop kernel: [   21.072015] DVB: registering new adapter (cx23885[0])
Apr 11 19:52:58 james-desktop kernel: [   21.072018] DVB: registering adapter 0 frontend 0 (NXP TDA10048HN DVB-T)...
Apr 12 07:46:09 james-desktop kernel: [   19.783797] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
Apr 12 07:46:09 james-desktop kernel: [   19.783804] cx23885_dvb_register() allocating 1 frontend(s)
Apr 12 07:46:09 james-desktop kernel: [   19.783806] cx23885[0]: cx23885 based dvb card
Apr 12 07:46:11 james-desktop kernel: [   21.382019] DVB: registering new adapter (cx23885[0])
Apr 12 07:46:11 james-desktop kernel: [   21.382024] DVB: registering adapter 0 frontend 0 (NXP TDA10048HN DVB-T)...
Apr 12 08:30:55 james-desktop kernel: [ 2491.050058] Modules linked in: binfmt_misc ppdev snd_hda_codec_atihdmi snd_hda_codec_analog tda18271 tda8290 tda10048 cx23885 snd_hda_intel cx2341x snd_hda_codec snd_hwdep videobuf_dma_sg snd_pcm_oss v4l2_common snd_mixer_oss videodev v4l1_compat v4l2_compat_ioctl32 snd_pcm asus_atk0110 snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi videobuf_dvb snd_seq_midi_event dvb_core videobuf_core snd_seq btcx_risc tveeprom snd_timer snd_seq_device psmouse serio_raw iptable_filter wacom i2c_piix4 ip_tables lirc_mceusb joydev lirc_dev fglrx(P) x_tables snd soundcore snd_page_alloc amd64_edac_mod edac_core lp parport hid_logitech ff_memless usbhid ohci1394 ieee1394 r8169 mii
Apr 12 14:33:25 james-desktop kernel: [13046.836016] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
Apr 12 14:33:25 james-desktop kernel: [13046.836030] cx23885 0000:03:00.0: firmware: requesting dvb-fe-tda10048-1.0.fw
Apr 12 14:33:25 james-desktop firmware.sh[11838]: Cannot find  firmware file 'dvb-fe-tda10048-1.0.fw'

```

MythTV is no longer installed.

---

### Post by dannyboy79 on 2010-04-12
you still didn't tell me what tv card you're using, what kernel you're using and basically from my post you only answered or provided the log frmo one file. if you want help, then you haev to help to get help. i could be a real jerk and not provide you the link i found by merely googling your error but I am not like that. I jsut find it disturbing that when someone posts a response and asks for information about your system, adn you post back and dont even provide the information that I wanted, how do expect to help from people?

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/942269.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/942269.html)

---

