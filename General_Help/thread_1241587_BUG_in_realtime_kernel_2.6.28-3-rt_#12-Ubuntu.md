---
title: "BUG in realtime kernel 2.6.28-3-rt #12-Ubuntu"
date: 2009-08-16
forum: General Help
---

### Post by joseche on 2009-08-16
Hi all, the real-time kernel is showing the following dumps hundreds of times:

[  381.116613] BUG: scheduling while atomic: sirq-tasklet/1/24/0x00000002, CPU#1
[  381.116617] Modules linked in: i915 drm binfmt_misc ppdev btusb bridge stp bnep uinput lp parport snd_hda_intel line6usb snd_usb_audio snd_pcm_oss snd_mixer_oss snd_pcm snd_usb_lib snd_seq_dummy snd_hwdep snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event ieee80211_crypt_tkip snd_seq applesmc snd_timer snd_seq_device led_class intel_agp joydev iTCO_wdt wl(P) snd appleir hid_apple soundcore pcspkr appletouch input_polldev iTCO_vendor_support agpgart ieee80211_crypt isight_firmware snd_page_alloc usbhid video output ohci1394 ieee1394 sky2 fbcon tileblit font bitblit softcursor
[  381.116671] Pid: 24, comm: sirq-tasklet/1 Tainted: P        W  2.6.28-3-rt #12-Ubuntu
[  381.116674] Call Trace:
[  381.116682]  [<c050f991>] ? printk+0x18/0x1f
[  381.116688]  [<c01307ec>] __schedule_bug+0x6c/0x80
[  381.116691]  [<c05101cd>] schedule+0x50d/0x760
[  381.116694]  [<c05112f6>] rt_spin_lock_slowlock+0x176/0x220
[  381.116698]  [<c0511b2d>] __rt_spin_lock+0x4d/0x50
[  381.116700]  [<c0511b38>] rt_spin_lock+0x8/0x10
[  381.116704]  [<c01bcf71>] kmem_cache_alloc+0x41/0x180
[  381.116724]  [<f808e9a5>] ? osl_pktfree+0x45/0x80 [wl]
[  381.116729]  [<c0123e68>] ? default_spin_lock_flags+0x8/0x10
[  381.116734]  [<c043608c>] __alloc_skb+0x2c/0x110
[  381.116737]  [<c043636c>] dev_alloc_skb+0x1c/0x30
[  381.116748]  [<f808e9fc>] osl_pktget+0x1c/0x50 [wl]
[  381.116766]  [<f80eed31>] wlc_179+0xc1c/0x1136 [wl]
[  381.116782]  [<f81005b6>] ? wlc_dpc+0x2e4/0x4be [wl]
[  381.116787]  [<c0102da7>] ? __switch_to+0xb7/0x1a0
[  381.116790]  [<c0130850>] ? finish_task_switch+0x50/0x120
[  381.116800]  [<f8093209>] ? wl_dpc+0x39/0xc4 [wl]
[  381.116804]  [<c014130e>] ? __tasklet_action+0x7e/0x100
[  381.116807]  [<c014143e>] ? tasklet_action+0x4e/0x60
[  381.116810]  [<c0141b6b>] ? ksoftirqd+0x12b/0x260
[  381.116812]  [<c0141a40>] ? ksoftirqd+0x0/0x260
[  381.116817]  [<c015164c>] ? kthread+0x3c/0x70
[  381.116820]  [<c0151610>] ? kthread+0x0/0x70
[  381.116823]  [<c0105547>] ? kernel_thread_helper+0x7/0x10
[  459.285705] BUG: scheduling while atomic: sirq-tasklet/1/24/0x00000002, CPU#1
[  459.285709] Modules linked in: i915 drm binfmt_misc ppdev btusb bridge stp bnep uinput lp parport snd_hda_intel line6usb snd_usb_audio snd_pcm_oss snd_mixer_oss snd_pcm snd_usb_lib snd_seq_dummy snd_hwdep snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event ieee80211_crypt_tkip snd_seq applesmc snd_timer snd_seq_device led_class intel_agp joydev iTCO_wdt wl(P) snd appleir hid_apple soundcore pcspkr appletouch input_polldev iTCO_vendor_support agpgart ieee80211_crypt isight_firmware snd_page_alloc usbhid video output ohci1394 ieee1394 sky2 fbcon tileblit font bitblit softcursor
[  459.285760] Pid: 24, comm: sirq-tasklet/1 Tainted: P        W  2.6.28-3-rt #12-Ubuntu
[  459.285763] Call Trace:
[  459.285771]  [<c050f991>] ? printk+0x18/0x1f
[  459.285776]  [<c01307ec>] __schedule_bug+0x6c/0x80
[  459.285779]  [<c05101cd>] schedule+0x50d/0x760
[  459.285783]  [<c011a2b3>] ? lapic_next_event+0x13/0x20
[  459.285786]  [<c05112f6>] rt_spin_lock_slowlock+0x176/0x220
[  459.285789]  [<c0511b2d>] __rt_spin_lock+0x4d/0x50
[  459.285792]  [<c0511b38>] rt_spin_lock+0x8/0x10
[  459.285795]  [<c01bcf71>] kmem_cache_alloc+0x41/0x180
[  459.285799]  [<c0155b50>] ? hrtimer_interrupt+0x0/0x290
[  459.285804]  [<c0123e68>] ? default_spin_lock_flags+0x8/0x10
[  459.285808]  [<c043608c>] __alloc_skb+0x2c/0x110
[  459.285811]  [<c043636c>] dev_alloc_skb+0x1c/0x30
[  459.285826]  [<f808e9fc>] osl_pktget+0x1c/0x50 [wl]
[  459.285843]  [<f80eed31>] wlc_179+0xc1c/0x1136 [wl]
[  459.285859]  [<f81005b6>] ? wlc_dpc+0x2e4/0x4be [wl]
[  459.285863]  [<c0102da7>] ? __switch_to+0xb7/0x1a0
[  459.285866]  [<c0130850>] ? finish_task_switch+0x50/0x120
[  459.285877]  [<f8093209>] ? wl_dpc+0x39/0xc4 [wl]
[  459.285880]  [<c014130e>] ? __tasklet_action+0x7e/0x100
[  459.285883]  [<c014143e>] ? tasklet_action+0x4e/0x60
[  459.285886]  [<c0141b6b>] ? ksoftirqd+0x12b/0x260
[  459.285888]  [<c0141a40>] ? ksoftirqd+0x0/0x260
[  459.285892]  [<c015164c>] ? kthread+0x3c/0x70
[  459.285895]  [<c0151610>] ? kthread+0x0/0x70
[  459.285898]  [<c0105547>] ? kernel_thread_helper+0x7/0x10

---

