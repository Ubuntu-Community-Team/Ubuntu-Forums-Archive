---
title: "Need help with crashes/freezes please"
date: 2009-12-10
forum: General Help
---

### Post by hidinginthemountains on 2009-12-10
Since installing Jaunty a couple weeks ago, I have been experiencing a number of glitches that I am having trouble reproducing. Well "glitches" might be understating it. My laptop will occasionally either lock up entirely (CAPS LOCK flashes sometimes when this happens) becoming unresponsive to anything except a hard reset. Other times it will actually reset itself out of nowhere without giving me any indications that something is going wrong.

I have attached a listing of my hardware.

I'm not sure what log entries might be relevant so I'm including a few snippets from the last time it did one of these "spontaneous resets". What I'm seeing leads me to believe it may be realted to my wifi and/or sound (which has some wierd stutters and skips and is often active when the freezes happen).

> Dec 10 11:35:04  kernel: [39407.844402] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 11:35:29  dhclient: DHCPREQUEST of 192.168.1.100 on wlan0 to 192.168.1.1 port 67
Dec 10 11:35:29  dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
Dec 10 11:35:29  dhclient: bound to 192.168.1.100 -- renewal in 35143 seconds.
Dec 10 11:35:29  NetworkManager: <info>  DHCP: device wlan0 state changed reboot -> renew 
Dec 10 11:35:29  NetworkManager: <info>    address 192.168.1.100 
Dec 10 11:35:29  NetworkManager: <info>    prefix 24 (255.255.255.0) 
Dec 10 11:35:29  NetworkManager: <info>    gateway 192.168.1.1 
Dec 10 11:35:29  NetworkManager: <info>    nameserver '75.154.133.100' 
Dec 10 11:35:29  NetworkManager: <info>    nameserver '75.154.133.68' 
Dec 10 11:37:04  kernel: [39527.840419] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 11:39:04 kernel: [39647.836386] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 11:40:01  /USR/SBIN/CRON[5603]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 10 11:41:04  kernel: [39767.836419] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 11:43:04  kernel: [39887.848366] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 11:45:04  kernel: [40007.836383] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 11:47:04  kernel: [40127.840402] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 11:49:04  kernel: [40247.840386] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 11:50:01  /USR/SBIN/CRON[6056]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 10 11:53:04  kernel: [40487.844386] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 11:55:04  kernel: [40607.840385] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 11:59:04  kernel: [40847.872336] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 12:00:01  /USR/SBIN/CRON[6495]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Dec 10 12:00:01  /USR/SBIN/CRON[6498]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 10 12:01:04  kernel: [40967.864367] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 12:03:04  kernel: [41087.836416] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 12:07:04  kernel: [41327.836352] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 12:09:04  kernel: [41447.848419] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 12:10:01  /USR/SBIN/CRON[7121]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 10 12:17:01  /USR/SBIN/CRON[7599]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 10 12:17:04  kernel: [41927.840419] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 12:20:01  /USR/SBIN/CRON[7816]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 10 12:23:04  kernel: [42287.844383] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 12:25:04  kernel: [42407.836399] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 12:30:01  /USR/SBIN/CRON[8268]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 10 12:31:04  kernel: [42767.840385] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 12:33:04  kernel: [42887.848386] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 12:35:04  kernel: [43007.840403] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 12:37:04  kernel: [43127.836384] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 12:40:01  /USR/SBIN/CRON[8829]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 10 12:42:11  ntpd[4173]: kernel time sync status change 4001
Dec 10 12:45:04  kernel: [43607.840382] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 12:47:04  kernel: [43727.840405] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 12:50:01  /USR/SBIN/CRON[9278]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 10 12:51:04  kernel: [43967.836419] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 12:53:04  kernel: [44087.836386] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 12:55:04  kernel: [44207.840386] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 12:59:04  kernel: [44447.836419] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 13:00:01  /USR/SBIN/CRON[9717]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 10 13:00:01  /USR/SBIN/CRON[9723]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Dec 10 13:03:04  kernel: [44687.856347] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 13:05:04  kernel: [44807.836419] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 13:07:04  kernel: [44927.840402] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 13:09:04  kernel: [45047.836435] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 13:10:01  /USR/SBIN/CRON[10183]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 10 13:13:04  kernel: [45287.836436] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 13:15:04  kernel: [45407.856985] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 13:16:18  ntpd[4173]: kernel time sync status change 0001
Dec 10 13:17:01  /USR/SBIN/CRON[10506]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 10 13:20:01  /USR/SBIN/CRON[10818]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 10 13:29:04  kernel: [46247.836517] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 13:30:01  /USR/SBIN/CRON[11161]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 10 13:33:04  kernel: [46487.836952] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 13:35:04  kernel: [46607.858899] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 13:37:04  kernel: [46727.832736] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 13:39:04  kernel: [46847.857418] ath5k phy0: noise floor calibration timeout (2412MHz)
Dec 10 13:40:37  syslogd 1.5.0#5ubuntu3: restart.
Dec 10 13:40:38  kernel: Inspecting /boot/System.map-2.6.28-17-generic

...anyway, you get the idea. *kern.log* is basically an unending stream of > ath5k phy0: noise floor calibration timeout so I'm left assuming that this is a problem.

Please suggest more info I can provide, ways I can test, or alternatives to try. This is a big problem for me, all help appreciated. :confused:

---

### Post by hidinginthemountains on 2009-12-10
I think I've got rid of that message by enabling the restricted driver. I'll wait and hope that this prevents the crashes now.

---

### Post by hidinginthemountains on 2009-12-10
I just had another freeze and reset. At the time the main thing I was doing was watching a show at [http://watch.discoverychannel.ca/](http://watch.discoverychannel.ca/)

> Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740414] *pde = 00000000 
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740431] Dumping ftrace buffer:
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740435]    (ftrace buffer empty)
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740438] Modules linked in: binfmt_misc radeon ppdev drm bridge stp bnep sbp2 lp parport joydev snd_hda_intel snd_usb_audio snd_pcm_oss snd_mixer_oss snd_seq_dummy snd_pcm snd_usb_lib snd_seq_oss snd_hwdep gspca_zc3xx snd_seq_midi snd_rawmidi gspca_main pcmcia snd_seq_midi_event videodev psmouse snd_seq snd_timer snd_seq_device v4l1_compat serio_raw yenta_socket rsrc_nonstatic wlan_scan_sta pcspkr video pcmcia_core snd soundcore snd_page_alloc i2c_piix4 ath_rate_sample input_polldev output shpchp ati_agp agpgart ath_pci wlan ath_hal(P) usbhid ohci1394 ieee1394 8139too 8139cp mii fbcon tileblit font bitblit softcursor
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740486] 
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740491] Pid: 3093, comm: Xorg Tainted: P           (2.6.28-17-generic #58-Ubuntu) Satellite A100
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740495] EIP: 0060:[<c0122c38>] EFLAGS: 00013092 CPU: 0
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740498] EIP is at __ticket_spin_lock+0x8/0x20
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740501] EAX: ff0e0300 EBX: f6351c90 ECX: 00000005 EDX: 00000100
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740504] ESI: 00003292 EDI: 00000000 EBP: f6351b0c ESP: f6351b0c
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740506]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740514]  f6351b14 c0122d58 f6351b24 c05003ee f6351c90 ff0e0300 f6351b34 c014f159
Dec 10 18:16:50 stoke-buntu kernel: [ 3063.740731] ---[ end trace baf45a2c3dde8172 ]---
Dec 10 18:16:50 stoke-buntu kernel: [ 3063.756220] [drm] Num pipes: 2
Dec 10 18:16:55 stoke-buntu bonobo-activation-server (ian-6237): could not associate with desktop session: Failed to connect to socket /tmp/dbus-IH4befunJ7: Connection refused
Dec 10 18:18:45 stoke-buntu exiting on signal 15
Dec 10 18:19:29 stoke-buntu syslogd 1.5.0#5ubuntu3: restart.

I believe that the above is the applicable part of my log. Please suggest what else I can do here...

---

### Post by hidinginthemountains on 2009-12-10
The following is from my syslog:

> Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740377] BUG: unable to handle kernel paging request at ff0e0300
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740394] IP: [<c0122c38>] __ticket_spin_lock+0x8/0x20
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740414] *pde = 00000000 
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740420] Oops: 0002 [#1] SMP 
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740424] last sysfs file: /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/charge_full
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740431] Dumping ftrace buffer:
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740435]    (ftrace buffer empty)
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740438] Modules linked in: binfmt_misc radeon ppdev drm bridge stp bnep sbp2 lp parport joydev snd_hda_intel snd_usb_audio snd_pcm_oss snd_mixer_oss snd_seq_dummy snd_pcm snd_usb_lib snd_seq_oss snd_hwdep gspca_zc3xx snd_seq_midi snd_rawmidi gspca_main pcmcia snd_seq_midi_event videodev psmouse snd_seq snd_timer snd_seq_device v4l1_compat serio_raw yenta_socket rsrc_nonstatic wlan_scan_sta pcspkr video pcmcia_core snd soundcore snd_page_alloc i2c_piix4 ath_rate_sample input_polldev output shpchp ati_agp agpgart ath_pci wlan ath_hal(P) usbhid ohci1394 ieee1394 8139too 8139cp mii fbcon tileblit font bitblit softcursor
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740486] 
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740491] Pid: 3093, comm: Xorg Tainted: P           (2.6.28-17-generic #58-Ubuntu) Satellite A100
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740495] EIP: 0060:[<c0122c38>] EFLAGS: 00013092 CPU: 0
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740498] EIP is at __ticket_spin_lock+0x8/0x20
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740501] EAX: ff0e0300 EBX: f6351c90 ECX: 00000005 EDX: 00000100
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740504] ESI: 00003292 EDI: 00000000 EBP: f6351b0c ESP: f6351b0c
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740506]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740509] Process Xorg (pid: 3093, ti=f6350000 task=f63725b0 task.ti=f6350000)
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740512] Stack:
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740514]  f6351b14 c0122d58 f6351b24 c05003ee f6351c90 ff0e0300 f6351b34 c014f159
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740521]  f3fce700 f6351bf0 f6351b50 c01cc4e4 ff0e0300 f3fc9300 f3fce700 f6351bf0
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740527]  f3fc9300 f6351b60 c04999f7 c053f0a0 00001000 f6351b6c c04220ef 0000000c
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740534] Call Trace:
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740537]  [<c0122d58>] ? default_spin_lock_flags+0x8/0x10
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740542]  [<c05003ee>] ? _spin_lock_irqsave+0x2e/0x40
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740549]  [<c014f159>] ? add_wait_queue+0x19/0x50
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740557]  [<c01cc4e4>] ? __pollwait+0x64/0xe0
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740565]  [<c04999f7>] ? unix_poll+0x17/0xb0
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740572]  [<c04220ef>] ? sock_poll+0xf/0x20
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740579]  [<c01cc16e>] ? do_select+0x2fe/0x610
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740584]  [<c01cc480>] ? __pollwait+0x0/0xe0
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740587]  [<c0133de0>] ? default_wake_function+0x0/0x10
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740592]  [<c0133de0>] ? default_wake_function+0x0/0x10
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740595]  [<c0133de0>] ? default_wake_function+0x0/0x10
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740599]  [<c0133de0>] ? default_wake_function+0x0/0x10
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740602]  [<c0133de0>] ? default_wake_function+0x0/0x10
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740606]  [<c0133de0>] ? default_wake_function+0x0/0x10
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740609]  [<c0132248>] ? enqueue_task_fair+0x68/0x70
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740612]  [<c0131cde>] ? resched_task+0x1e/0x70
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740616]  [<c0133c54>] ? try_to_wake_up+0x104/0x290
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740619]  [<c0133deb>] ? default_wake_function+0xb/0x10
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740623]  [<c0128ec0>] ? __wake_up_common+0x40/0x70
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740628]  [<c015846d>] ? clocksource_get_next+0x3d/0x50
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740636]  [<c0157092>] ? update_wall_time+0x4c2/0x8e0
Dec 10 18:16:49 stoke-buntu kernel: [ 3063.740639]  [<c0156ad3>] ? getnstimeofday+0x53/0x110
Dec 10 18:16:50 stoke-buntu kernel: [ 3063.740643]  [<c04285fd>] ? skb_dequeue+0x4d/0x70
Dec 10 18:16:50 stoke-buntu kernel: [ 3063.740649]  [<c049cb47>] ? unix_stream_recvmsg+0x227/0x490
Dec 10 18:16:50 stoke-buntu kernel: [ 3063.740653]  [<c0127c05>] ? sched_slice+0x35/0x50
Dec 10 18:16:50 stoke-buntu kernel: [ 3063.740657]  [<c02a8e70>] ? apparmor_socket_recvmsg+0x10/0x20
Dec 10 18:16:50 stoke-buntu kernel: [ 3063.740667]  [<c01cc6a4>] ? core_sys_select+0x144/0x270
Dec 10 18:16:50 stoke-buntu kernel: [ 3063.740671]  [<c0152b5a>] ? hrtimer_try_to_cancel+0x3a/0x90
Dec 10 18:16:50 stoke-buntu kernel: [ 3063.740675]  [<c0156ad3>] ? getnstimeofday+0x53/0x110
Dec 10 18:16:50 stoke-buntu kernel: [ 3063.740679]  [<c01cc9ac>] ? sys_select+0x2c/0xb0
Dec 10 18:16:50 stoke-buntu kernel: [ 3063.740683]  [<c0103f6b>] ? sysenter_do_call+0x12/0x2f
Dec 10 18:16:50 stoke-buntu kernel: [ 3063.740687] Code: ff ff 90 b9 0a 2b 12 c0 b8 0d 2b 12 c0 e9 59 ff ff ff 90 b9 10 2b 12 c0 b8 13 2b 12 c0 e9 49 ff ff ff 90 55 ba 00 01 00 00 89 e5 <3e> 66 0f c1 10 38 f2 74 06 f3 90 8a 10 eb f6 5d c3 8d b4 26 00 
Dec 10 18:16:50 stoke-buntu kernel: [ 3063.740723] EIP: [<c0122c38>] __ticket_spin_lock+0x8/0x20 SS:ESP 0068:f6351b0c
Dec 10 18:16:50 stoke-buntu kernel: [ 3063.740731] ---[ end trace baf45a2c3dde8172 ]---
Dec 10 18:16:50 stoke-buntu gdm[3089]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Dec 10 18:16:50 stoke-buntu NetworkManager: <info>  (ath0): device state change: 8 -> 3 
Dec 10 18:16:50 stoke-buntu kernel: [ 3063.756220] [drm] Num pipes: 2
Dec 10 18:16:50 stoke-buntu NetworkManager: <info>  (ath0): deactivating device (reason: 38). 
Dec 10 18:16:50 stoke-buntu NetworkManager: <info>  ath0: canceled DHCP transaction, dhcp client pid 3829 
Dec 10 18:16:50 stoke-buntu NetworkManager: <WARN>  check_one_route(): (ath0) error -34 returned from rtnl_route_del(): Sucess  
Dec 10 18:16:50 stoke-buntu avahi-daemon[3164]: Withdrawing address record for 192.168.1.100 on ath0.
Dec 10 18:16:50 stoke-buntu avahi-daemon[3164]: Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.1.100.
Dec 10 18:16:50 stoke-buntu avahi-daemon[3164]: Interface ath0.IPv4 no longer relevant for mDNS.
Dec 10 18:16:55 stoke-buntu bonobo-activation-server (ian-6237): could not associate with desktop session: Failed to connect to socket /tmp/dbus-IH4befunJ7: Connection refused
Dec 10 18:16:57 stoke-buntu gdm[3086]: CRITICAL: gdm_config_value_get_bool: assertion `value->type == GDM_CONFIG_VALUE_BOOL' failed 
Dec 10 18:17:01 stoke-buntu /USR/SBIN/CRON[6313]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 10 18:17:04 stoke-buntu gdm[3086]: WARNING: Failed to start X server several times in a short time period; disabling display :0 
Dec 10 18:17:13 stoke-buntu ntpd[4043]: Deleting interface #5 ath0, 192.168.1.100#123, interface stats: received=35, sent=35, dropped=0, active_time=3001 secs
Dec 10 18:18:38 stoke-buntu init: tty4 main process (2272) killed by TERM signal
Dec 10 18:18:38 stoke-buntu init: tty5 main process (2273) killed by TERM signal
Dec 10 18:18:38 stoke-buntu init: tty2 main process (2279) killed by TERM signal
Dec 10 18:18:38 stoke-buntu init: tty3 main process (2282) killed by TERM signal
Dec 10 18:18:38 stoke-buntu init: tty6 main process (2283) killed by TERM signal
Dec 10 18:18:38 stoke-buntu init: tty1 main process (3430) killed by TERM signal
Dec 10 18:18:39 stoke-buntu init: control-alt-delete respawning too fast, stopped
Dec 10 18:18:39 stoke-buntu last message repeated 8 times
Dec 10 18:18:45 stoke-buntu bluetoothd[3052]: bridge pan0 removed
Dec 10 18:18:45 stoke-buntu bluetoothd[3052]: Stopping SDP server
Dec 10 18:18:45 stoke-buntu bluetoothd[3052]: Exit
Dec 10 18:18:45 stoke-buntu exiting on signal 15
Dec 10 18:19:29 stoke-buntu syslogd 1.5.0#5ubuntu3: restart.

I think you can see my trying to reset X and reboot the system when it locked up (at least I assume that's what I'm looking at, I'm no expert) :???:

---

### Post by hidinginthemountains on 2009-12-10
have filed bug here [https://bugs.launchpad.net/bugs/495322](https://bugs.launchpad.net/bugs/495322)

---

### Post by joes7 on 2009-12-10
Use the LiveCD's fix option. It will definitely help you. Yes, there are loads of bugs matching your description on Ubuntu's Bug Squad page. 

You can also get into recovery mode, if you have GRUB enabled.
```

Ubuntu [your version]
Ubuntu [your version] Recovery Mode <---Run this option

```

I wish you the best of lucks,
Merry Christmas!

---

### Post by hidinginthemountains on 2009-12-10
Thanks for the direction! Now I just need to find a Jaunty CD (did Jaunty by way of upgrade from Intrepid, first and only time I've "upgraded" Ubuntu).

nm: read more carefully, I'll do it via GRUB :)

---

### Post by hidinginthemountains on 2009-12-11
well, I've made it through a day without any crashes. the dpkg repair option you directed me too seems to have done the trick.

I'm going to guess that this is solved. I'll wait a few days to be sure before I close it at launchpad, but if it doesn't recur I'll post what I did and suggest they close it.

---

