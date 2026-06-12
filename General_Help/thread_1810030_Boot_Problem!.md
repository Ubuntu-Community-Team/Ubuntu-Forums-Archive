---
title: "Boot Problem!"
date: 2011-07-22
forum: General Help
---

### Post by Condenzationator on 2011-07-22
HP ProBook 4710s
Ubuntu 11.04 (Natty Narwhal)

I booted up my computer (laptop) today, and it got to the point where the (mouse) cursor shows, but then it freezes on a black screen and gives me this:

```
[42.936405] BUG: unable to handle kernel paging request at f8a83da0
[42.936455] IP: [<f8572ab4>] rs600_gart_set_page+0x54/0x60 [radeon]
[42.936516] *pde = 30eff067 *pte = 00000000
[42.936553] Oops: 0002 [#1] SMP
[42.936586] last sysfs file: /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/voltage_now
[42.936647] Modules linked in: parport_pc ppdev snd_had_codec_hdmi snd_had_codec_analog rfcomm binfmt_misc sco bnep 12cap vboxnetadp vboxnetflt vboxdrv snd_had_intel snd_had_codec snd_hwdep arc4 uv cvideo radeon videodev btusb snd_pcm bluetooth snd_seq_midi snd_rawmidi iwlagn snd_seq_midi_event hp_wmi joydev ttm snd_seq sparse_keymap drm_kms_helper drm snd_timer iwlcore snd_seq_device mac80211 hp_accel psmouse serio_raw snd lis31v02d i2c_algo_bit cfg80211 soundcore snd_page_alloc video input_polldev lp parport ahci libahci sky2
[42.937127]
[42.937140] Pid: 1710, comm.: compiz Tainted: G        W I 2.6.38-10-generic #46-Ubuntu Hewlett-Packard HP ProBook 4710s/3074
[42.937228] EIP: 0060[<f8572ab4>] EFLAGS: 00010282 CPU: 1
[42.937280] EIP is at rs600_gart_set_page+0x54/0x60 [radeon]
[42.937317] EAX: f8a83da0 EBX: 00000000 ECX: ffffffea EDX: 000007b4
[42.937355] ESI: f8a80000 EDI: bf14a067 EBP: f09d5c5c ESP: f09d5c50
[42.937393] DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 00b8
[42.937427] Process compiz (pid: 1710, ti=f09d4000 task=f3666500 task.ti=f09d4000)
[42.937475] Stack:
[42.937490] bf14a000 f6fc7000 00000001 f09d5c98 f8545181 bf14a000 00000000 00000000
[42.937565] f6750940 007b4000 000007b4 00000001 f362a060 f0901ed0 00001ed0 00001ed0 f13ce780
[42.937641] f13cd3f8 00000000 f09d5cc0 f8542dff f13cd3f8 f13ce780 f09d5cc0 f82d768f
[42.937716] Call Trace:
[42.937749] [<f8545181>] radeon_gart_bind+0x91/0x190 [radeon]
[42.937802] [<f8542dff>] radeon_ttm_backend_bine+0x2f/0xa0 [radeon]
[42.937849] [<f82d768f>] ? ttm_tt_populate+0x6f/0x90 [ttm]
[42.937887] [<f82d76fc>] ttm_tt_bind+0x4c/0x70 [ttm]
[42.937923] [<f82daf1a>] ttm_bo_move_ttm+0xda/0xf0 [ttm]
[42.937961] [<f82d947e>] ttm_bo_handle_move_mem+0x2ae/0x380 [ttm]
[42.938015] [<f8544a80>] ? radeon_bo_move_notify+0x0/0x30 [radeon]
[42.938059] [<f82da195>] ttm_bo_move_buffer+0x125/0x140 [ttm]
[42.938102] [<f82da258>] ttm_bo_validate+0xa9/0x120 [ttm]
[42.938153] [<f8544683>] radeon_bo_list_validate+0x73/0xd0 [radeon]
[42.938211] [<f855b769>] radeon_cs_parser_relocs+0x209/0x250 [radeon]
[42.938270] [<f855b9f9>] ? radeon_cs_parser_init+0x249/0x2a0 [radeon]
[42.938330] [<f855bb75>] radeon_cs_ioctl+0x75/0x180 [radeon]
[42.938376] [<f8330cd1>] drm_ioctl+0x1e1/0x470 [drm]
[42.938427] [<f855bb00>] ? radeon_cs_ioctl+0x0/0x180 [radeon]
[42.938468] [<c1101791>] ? handle_mm_fault+0xb1/0x130 [radeon]
[42.938504] [<c150d3a0>] ?do_page fault+0x0/0x490
[42.938535] [<c150d5cf>] ? do_page_fault+0x22f/0x490
[42.938575] [<f8330af0>] ? drm_ioctl+0x0/0x470 [drm]
[42.938608] [<c113696b>] do_vfs_ioctl+0x7b/0x2e0
[42.938638] [<c1136c57>] sys_icotl+0x87/0x90
[42.938666] [<c150a194>] syscall_call+0x7/0xb
[42.938698] [<c1500000>] ? detect_ht+0x14f/0x16d
[42.938727] Code: 79 15 89 c8 8b 1c 24 8b 74 24 04 8b 7c 24 08 89 ec 5d c3 8d 74 26 00 3b 90 c8 02 00 00 77 e3 81 e7 00 f0 ff ff 83 cf 678d 04 d6 <89> 38 89 58 04 31 c9 eb cd 9d 76 00 55 89 e5 57 56 53 83 ec 14
[42.939097] EIP: [<f8572ab4>] rs600_gart_set_page+0x54/0x60 [radeon] SS:ESP 0068:f09d5c50
[42.939174] CR2: 00000000f8a83da0

```(note: I had to type it all out on another computer, so there may be possible mispells/typos!)

It was working fine yesterday, but it seems the graphics card is having an issue with something now. Any ideas on what to do?

Thanks!

Edit:
It's very strange, but it works now for some reason.
Was it just a failed initialization of the graphics card?
If at all possible, I'd still like to try and fix it somehow, as I've had to re-install Ubuntu once already due to what I'm strongly believing were graphics card issues. Is it my drivers? I didn't install the proprietary drivers for my ATI graphics card this time, since that's what I thought my problem was last time, but now I get graphics glitches in someplaces (a single white bar over some text, like on the sidebar on the left when the menu comes up).
I had Windows XP Pro installed before Ubuntu, and Ubuntu is the only one installed now. No problems at all before with Windows.
My graphics card is an ATI Mobility Radeon HD 4330

---

### Post by mynk on 2011-08-04
I am seeing a similar problem. You don't need to really type it to another comp. When you boot from the same machine with a previous kernel you should be able to find the logs under /var/log/ - I found it in /var/log/kern.log and look for the time of your interest.

I see that the foot print of the oops is slightly different for me so putting as much information as I can here -

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/820746](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/820746)

If you see the problem again you could file a bug also using -

ubuntu-bug linux

gathers most of the information for you and attach the /var/log/kern.log separately.

Hope this helps,
Mayank

---

