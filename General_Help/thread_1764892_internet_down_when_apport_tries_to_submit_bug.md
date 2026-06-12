---
title: "internet down when apport tries to submit bug"
date: 2011-05-22
forum: General Help
---

### Post by uranger on 2011-05-22
Is there anyway to resubmit a bug with apport after it has failed to submit? Apport attempted to submit a kernel problem at a time when the internet was down. Because the kernel problem was related to wireless ...

I have the snippet in kern.log:

May 22 10:25:37 chris-laptop kernel: [ 2071.930133] ------------[ cut here ]------------
May 22 10:25:37 chris-laptop kernel: [ 2071.930181] WARNING: at /build/buildd/linux-2.6.38/net/mac80211/util.c:1176 ieee80211_reconfig+0x47b/0x480 [mac80211]()
May 22 10:25:37 chris-laptop kernel: [ 2071.930188] Hardware name: Inspiron 1525                   
May 22 10:25:37 chris-laptop kernel: [ 2071.930192] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat mmc_block snd_hrtimer binfmt_misc parport_pc ppdev snd_hda_codec_idt snd_hda_codec_hdmi joydev arc4 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi iwl3945 snd_rawmidi i915 iwlcore snd_seq_midi_event dell_wmi snd_seq sparse_keymap mac80211 dell_laptop dcdbas drm_kms_helper snd_timer uvcvideo r852 sm_common nand nand_ids nand_ecc snd_seq_device videodev cfg80211 psmouse serio_raw v4l2_compat_ioctl32 mtd snd drm soundcore i2c_algo_bit snd_page_alloc video lp parport ahci firewire_ohci sdhci_pci sdhci firewire_core crc_itu_t sky2 libahci
May 22 10:25:37 chris-laptop kernel: [ 2071.930305] Pid: 2415, comm: kworker/0:0 Not tainted 2.6.38-8-generic #42-Ubuntu
May 22 10:25:37 chris-laptop kernel: [ 2071.930311] Call Trace:
May 22 10:25:37 chris-laptop kernel: [ 2071.930326]  [<ffffffff81065cef>] ? warn_slowpath_common+0x7f/0xc0
May 22 10:25:37 chris-laptop kernel: [ 2071.930335]  [<ffffffff81065d4a>] ? warn_slowpath_null+0x1a/0x20
May 22 10:25:37 chris-laptop kernel: [ 2071.930361]  [<ffffffffa01f0d7b>] ? ieee80211_reconfig+0x47b/0x480 [mac80211]
May 22 10:25:37 chris-laptop kernel: [ 2071.930379]  [<ffffffffa01d0c70>] ? ieee80211_restart_work+0x0/0xa0 [mac80211]
May 22 10:25:37 chris-laptop kernel: [ 2071.930396]  [<ffffffffa01d0cd6>] ? ieee80211_restart_work+0x66/0xa0 [mac80211]
May 22 10:25:37 chris-laptop kernel: [ 2071.930407]  [<ffffffff8108269d>] ? process_one_work+0x11d/0x420
May 22 10:25:37 chris-laptop kernel: [ 2071.930416]  [<ffffffff81083298>] ? worker_thread+0x168/0x360
May 22 10:25:37 chris-laptop kernel: [ 2071.930425]  [<ffffffff81083130>] ? worker_thread+0x0/0x360
May 22 10:25:37 chris-laptop kernel: [ 2071.930433]  [<ffffffff810877e6>] ? kthread+0x96/0xa0
May 22 10:25:37 chris-laptop kernel: [ 2071.930443]  [<ffffffff8100ce24>] ? kernel_thread_helper+0x4/0x10
May 22 10:25:37 chris-laptop kernel: [ 2071.930451]  [<ffffffff81087750>] ? kthread+0x0/0xa0
May 22 10:25:37 chris-laptop kernel: [ 2071.930458]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
May 22 10:25:37 chris-laptop kernel: [ 2071.930464] ---[ end trace 133a8fddb2db2949 ]---

What can I do now??

Thanks.

---

### Post by mc4man on 2011-05-22
Browse to /var/crash/ and see if the related, if any, crash report is in there
If so then R or double L click on (I forget), and choose to submit

---

### Post by uranger on 2011-05-22
great, thanks. i was able to submit the bug in this way.

---

