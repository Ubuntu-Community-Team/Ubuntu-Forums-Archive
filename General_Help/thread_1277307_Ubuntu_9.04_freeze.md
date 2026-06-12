---
title: "Ubuntu 9.04 freeze"
date: 2009-09-28
forum: General Help
---

### Post by yeeeev on 2009-09-28
Hi All,

Just had a system freeze (haven't had one in a few months).
Evince crashed a one minute later the whole system froze (no mouse, no ctrl+alt+F1, no ctrl+alt+backspace (I have that enabled))

I paste here the contents of my kern.log. Does anyone have an opinion regarding the cause, and what might be done to avoid it?

Thought I'd check here, before opening a bug report...

Thanks,
Yoav

Sep 28 11:30:24 yoav-laptop kernel: [54176.792027] __ratelimit: 18 callbacks suppressed
Sep 28 11:30:24 yoav-laptop kernel: [54176.792031] evince[4625]: segfault at 1014 ip b7a8e6a6 sp b6b6cb40 error 4 in libfontconfig.so.1.3.0[b7a86000+2b000]
Sep 28 11:34:09 yoav-laptop kernel: [54401.894857] NVRM: Xid (0001:00): 13, 0001 00000000 0000502d 00000214 00008000 00000040
Sep 28 11:34:53 yoav-laptop kernel: [54446.224148] usb 5-1: USB disconnect, address 2
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017] BUG: soft lockup - CPU#1 stuck for 61s! [Xorg:3734]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017] Modules linked in: ipt_MASQUERADE xt_DSCP binfmt_misc ppdev bridge stp bnep vboxnetadp vboxnetflt vboxdrv input_polldev ipt_REJECT ipt_LOG xt_limit xt_tcpudp xt_state ipt_addrtype ip6table_filter ip6_tables nf_nat_irc nf_conntrack_irc nf_nat_ftp nf_conntrack_ftp deflate zlib_deflate ctr twofish twofish_common camellia serpent blowfish des_generic cbc aes_i586 aes_generic xcbc rmd160 sha256_generic sha1_generic crypto_null af_key dm_crypt lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss arc4 snd_pcm ecb snd_seq_dummy snd_seq_oss snd_seq_midi iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack snd_rawmidi iwl3945 nf_defrag_ipv4 snd_seq_midi_event iptable_mangle snd_seq joydev iptable_filter uvcvideo mac80211 snd_timer hid_logitech ip_tables compat_ioctl32 psmouse snd_seq_device led_class ff_memless ricoh_mmc sdhci_pci sdhci videodev x_tables video snd soundcore nvidia(P) pcspkr v4l1_compat usbhid serio_raw output snd_page_alloc iTCO_wdt iTCO_vendor_support cfg80211 in
Sep 28 11:35:14 yoav-laptop kernel: el_agp agpgart dcdbas ohci1394 ieee1394 b44 ssb mii fbcon tileblit font bitblit softcursor
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017] 
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017] Pid: 3734, comm: Xorg Tainted: P           (2.6.28-15-generic #49-Ubuntu) Vostro 1700                     
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017] EIP: 0060:[<f87f2a98>] EFLAGS: 00003202 CPU: 1
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017] EIP is at _nv003985rm+0x23/0x24 [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017] EAX: 11678860 EBX: f613f400 ECX: 00009410 EDX: f9200000
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017] ESI: f5f8f800 EDI: ac4e0fe0 EBP: f61c5e08 ESP: f5f5dcfc
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017] CR0: 8005003b CR2: 08fee9d4 CR3: 35dd8000 CR4: 00000690
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017] DR6: ffff0ff0 DR7: 00000400
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017] Call Trace:
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f86eb571>] ? _nv008235rm+0x1c/0x9c [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f88601d5>] ? _nv001587rm+0xc3/0xf9 [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f885eb26>] ? _nv001607rm+0xc0/0x102 [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f87b50ea>] ? _nv008721rm+0xdf/0x1a4 [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f8524ae8>] ? _nv015421rm+0x1e7/0x230 [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f8524cfb>] ? _nv015536rm+0x1ca/0x367 [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f851c569>] ? _nv015538rm+0x4e/0x124 [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f8645312>] ? _nv011043rm+0x5eb/0x603 [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f864171b>] ? _nv011046rm+0x78/0x1c8 [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f8770985>] ? _nv002897rm+0x2a3/0x2da [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f864609f>] ? _nv010973rm+0x6d/0x16f [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f85844e6>] ? _nv003026rm+0x8a/0xd1 [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f85845dd>] ? _nv003030rm+0xb0/0x15e [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f8792a4d>] ? _nv003034rm+0x1a2/0x2e1 [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f878eec8>] ? _nv005235rm+0x4e/0x75 [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f86548e1>] ? _nv002980rm+0x195/0x54a [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f87f7c22>] ? rm_ioctl+0x3e/0x6d [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f889cae0>] ? nv_kern_ioctl+0x100/0x380 [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f889cdab>] ? nv_kern_unlocked_ioctl+0x1b/0x30 [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<f889cd90>] ? nv_kern_unlocked_ioctl+0x0/0x30 [nvidia]
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<c01ca4b8>] ? vfs_ioctl+0x28/0x90
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<c01a4fd5>] ? do_munmap+0x225/0x280
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<c0104629>] ? irq_entries_start+0x459/0x1000
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<c01ca99e>] ? do_vfs_ioctl+0x5e/0x200
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<c01caba3>] ? sys_ioctl+0x63/0x70
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<c0103f6b>] ? sysenter_do_call+0x12/0x2f
Sep 28 11:35:14 yoav-laptop kernel: [54466.629017]  [<c0104629>] ? irq_entries_start+0x459/0x1000

---

### Post by yeeeev on 2009-09-28
bump

---

### Post by wojox on 2009-09-28
Was this a big .pdf with a lot of graphics?

---

### Post by yeeeev on 2009-09-28
Big PDF with lots of boring graphs, but very few colors and no pictures...
It is a PDF I often look at, so I don't think there's something defetive about the PDF itself. The crash happened while scrolling down quickly in it.
There were no other abnormal resource issues (CPU was low, mem was low as well, no swapping, etc)

---

### Post by wojox on 2009-09-28
It looks like this started it: libfontconfig.so.1.3.0 which there's already a bug report for.
Don't know what else to tell you.

---

### Post by yeeeev on 2009-09-28
Can you provide a link to the mentioned bug report?
On the technical level, how can a user space library crash (which can happen from time to time) take down the whole system?

---

### Post by wojox on 2009-09-28
[http://www.fontconfig.org/wiki/](http://www.fontconfig.org/wiki/)

Don't know, unless when you were scrolling fast it just freaked out the graphics card. I see a lot of refrences to nvidia, as well as your cpu locking up for 61s. The seg fault seemed to have started with that  libfontconfig.so.1.3.0. You could also google  libfontconfig.so.1.3.0 and ubuntu to see more problems.

---

### Post by CHaoSlayeR on 2009-10-19
I had a similar issue (also freezing the desktop and all applications) with KVM. My lockups where not the same in duration (varying from 16 seconds up to 5 minutes).

The final solution for me was to simply upgrade the BIOS. Please try that before digging into the software layer.

C]-[aoZ

---

