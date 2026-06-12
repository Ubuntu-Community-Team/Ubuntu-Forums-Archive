---
title: "Kernel Failure in Fedora11....Why?"
date: 2009-07-24
forum: General Help
---

### Post by lukaszr on 2009-07-24
Here is the log. can someone help me out...why am i getting this error?

> Kernel failure message 1:
------------[ cut here ]------------
WARNING: at include/net/mac80211.h:1956 ath_get_rate+0x8c/0x3ea [ath9k]() (Tainted: P        W )
Hardware name: HP G60 Notebook PC
Modules linked in: fuse sco bridge stp llc bnep l2cap bluetooth vboxnetadp vboxnetflt vboxdrv sunrpc ip6t_REJECT nf_conntrack_ipv6 ip6table_filter ip6_tables ipv6 cpufreq_ondemand powernow_k8 dm_multipath uinput snd_hda_codec_nvhdmi arc4 snd_hda_codec_conexant ecb snd_hda_intel nvidia(P) snd_hda_codec ath9k uvcvideo mac80211 snd_hwdep snd_pcm videodev forcedeth v4l1_compat serio_raw joydev cfg80211 snd_timer snd soundcore snd_page_alloc video wmi output pata_amd usb_storage ata_generic pata_acpi nouveau drm i2c_algo_bit i2c_core [last unloaded: scsi_wait_scan]
Pid: 1873, comm: wpa_supplicant Tainted: P        W  2.6.29.6-213.fc11.i586 #1
Call Trace:
 [<c042ebc6>] warn_slowpath+0x7c/0xa4
 [<c0421eb8>] ? __wake_up+0x37/0x40
 [<c06974bf>] ? netlink_unlock_table+0x2c/0x2f
 [<c0698c79>] ? netlink_broadcast+0x1d3/0x20f
 [<f8654e4a>] ath_get_rate+0x8c/0x3ea [ath9k]
 [<f7d1ddd8>] rate_control_get_rate+0x84/0xc5 [mac80211]
 [<f7d22d30>] invoke_tx_handlers+0x3a5/0x9df [mac80211]
 [<c067d52b>] ? skb_release_data+0x92/0x96
 [<c041bb33>] ? default_spin_lock_flags+0x8/0xd
 [<f7d226e2>] ? __ieee80211_tx_prepare+0x1e2/0x21a [mac80211]
 [<f7d24578>] ieee80211_master_start_xmit+0x2a4/0x3b4 [mac80211]
 [<c0428199>] ? try_to_wake_up+0x22a/0x235
 [<c06842e1>] dev_hard_start_xmit+0x1ed/0x24c
 [<c0421eb8>] ? __wake_up+0x37/0x40
 [<c0692437>] __qdisc_run+0xcb/0x1b4
 [<c068476c>] dev_queue_xmit+0x340/0x440
 [<c067de7c>] ? __alloc_skb+0x59/0x106
 [<f7d257d4>] ieee80211_tx_skb+0x56/0x59 [mac80211]
 [<f7d1a19b>] ieee80211_send_deauth_disassoc+0xd0/0xd8 [mac80211]
 [<f7d1a26b>] ieee80211_set_disassoc+0xc8/0x17b [mac80211]
 [<f7d1a409>] ieee80211_sta_req_auth+0x44/0x60 [mac80211]
 [<f7d149c1>] ieee80211_ioctl_siwgenie+0x50/0x5d [mac80211]
 [<c06ee4f2>] ioctl_standard_call+0x1af/0x263
 [<c0682604>] ? dev_name_hash+0x1b/0x47
 [<c0682604>] ? dev_name_hash+0x1b/0x47
 [<c06ee679>] wext_handle_ioctl+0xd3/0x15e
 [<f7d14971>] ? ieee80211_ioctl_siwgenie+0x0/0x5d [mac80211]
 [<c0685e3f>] dev_ioctl+0x54f/0x56f
 [<c0531114>] ? avc_has_perm+0x41/0x4d
 [<c0677c29>] sock_ioctl+0x1d4/0x1e0
 [<c0677a55>] ? sock_ioctl+0x0/0x1e0
 [<c04aa457>] vfs_ioctl+0x1d/0x74
 [<c04aad3d>] do_vfs_ioctl+0x480/0x4ba
 [<c0532ccf>] ? selinux_file_ioctl+0x3f/0x42
 [<c04aadbd>] sys_ioctl+0x46/0x66
 [<c0403f72>] syscall_call+0x7/0xb
---[ end trace b394516ebb53db83 ]---


Kernel failure message 2:
------------[ cut here ]------------
WARNING: at include/net/mac80211.h:1956 ath_get_rate+0x8c/0x3ea [ath9k]() (Tainted: P          )
Hardware name: HP G60 Notebook PC
Modules linked in: fuse sco bridge stp llc bnep l2cap bluetooth vboxnetadp vboxnetflt vboxdrv sunrpc ip6t_REJECT nf_conntrack_ipv6 ip6table_filter ip6_tables ipv6 cpufreq_ondemand powernow_k8 dm_multipath uinput snd_hda_codec_nvhdmi arc4 snd_hda_codec_conexant ecb snd_hda_intel nvidia(P) snd_hda_codec ath9k uvcvideo mac80211 snd_hwdep snd_pcm videodev forcedeth v4l1_compat serio_raw joydev cfg80211 snd_timer snd soundcore snd_page_alloc video wmi output pata_amd usb_storage ata_generic pata_acpi nouveau drm i2c_algo_bit i2c_core [last unloaded: scsi_wait_scan]
Pid: 1873, comm: wpa_supplicant Tainted: P           2.6.29.6-213.fc11.i586 #1
Call Trace:
 [<c042ebc6>] warn_slowpath+0x7c/0xa4
 [<c0421eb8>] ? __wake_up+0x37/0x40
 [<c06974bf>] ? netlink_unlock_table+0x2c/0x2f
 [<c0698c79>] ? netlink_broadcast+0x1d3/0x20f
 [<f8654e4a>] ath_get_rate+0x8c/0x3ea [ath9k]
 [<f7d1ddd8>] rate_control_get_rate+0x84/0xc5 [mac80211]
 [<f7d22d30>] invoke_tx_handlers+0x3a5/0x9df [mac80211]
 [<c067d52b>] ? skb_release_data+0x92/0x96
 [<c041bb33>] ? default_spin_lock_flags+0x8/0xd
 [<f7d226e2>] ? __ieee80211_tx_prepare+0x1e2/0x21a [mac80211]
 [<f7d24578>] ieee80211_master_start_xmit+0x2a4/0x3b4 [mac80211]
 [<c0428199>] ? try_to_wake_up+0x22a/0x235
 [<c06842e1>] dev_hard_start_xmit+0x1ed/0x24c
 [<c0421eb8>] ? __wake_up+0x37/0x40
 [<c0692437>] __qdisc_run+0xcb/0x1b4
 [<c068476c>] dev_queue_xmit+0x340/0x440
 [<c067de7c>] ? __alloc_skb+0x59/0x106
 [<f7d257d4>] ieee80211_tx_skb+0x56/0x59 [mac80211]
 [<f7d1a19b>] ieee80211_send_deauth_disassoc+0xd0/0xd8 [mac80211]
 [<f7d1a26b>] ieee80211_set_disassoc+0xc8/0x17b [mac80211]
 [<f7d1a409>] ieee80211_sta_req_auth+0x44/0x60 [mac80211]
 [<f7d149c1>] ieee80211_ioctl_siwgenie+0x50/0x5d [mac80211]
 [<c06ee4f2>] ioctl_standard_call+0x1af/0x263
 [<c0682604>] ? dev_name_hash+0x1b/0x47
 [<c0682604>] ? dev_name_hash+0x1b/0x47
 [<c06ee679>] wext_handle_ioctl+0xd3/0x15e
 [<f7d14971>] ? ieee80211_ioctl_siwgenie+0x0/0x5d [mac80211]
 [<c0685e3f>] dev_ioctl+0x54f/0x56f
 [<c0531114>] ? avc_has_perm+0x41/0x4d
 [<c0677c29>] sock_ioctl+0x1d4/0x1e0
 [<c0677a55>] ? sock_ioctl+0x0/0x1e0
 [<c04aa457>] vfs_ioctl+0x1d/0x74
 [<c04aad3d>] do_vfs_ioctl+0x480/0x4ba
 [<c0532ccf>] ? selinux_file_ioctl+0x3f/0x42
 [<c04aadbd>] sys_ioctl+0x46/0x66
 [<c0403f72>] syscall_call+0x7/0xb
---[ end trace b394516ebb53db82 ]---


---

### Post by chriskin on 2009-07-24
you really should ask in the fedora forums :)

---

