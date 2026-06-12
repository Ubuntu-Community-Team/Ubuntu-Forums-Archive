---
title: "PC freezes randomly Ubuntu 10.04 LTS"
date: 2010-06-24
forum: General Help
---

### Post by burnxez on 2010-06-24
Hello, I just installed Ubuntu 10.04 LTS , and I liked it a lot, however I'm having a little trouble.
My PC freezes randomly for about 5-10 minutes and after that everything works fine again, then it freezes one more time and so on...
I've been doing a little research and found nothing useful.
I'm kinda new to this Ubuntu system so I might be missing something...
I've got an Intel Pentium 4 HT 3.2Ghz Processor and an Intel DGCC101 Motherboard with an Ati Xpress X200 chipset.
If you need anymore info just let me know :)
Any help would be much appreciated.
Thanks.

---

### Post by mörgæs on 2010-06-24
A random freeze is a difficult error to trace. There can be many reasons. 

First, you can run the command **top** to see whether a particular process is overloading the CPU. Press q for quitting top.

---

### Post by Rubi1200 on 2010-06-24
You might want to consider turning desktop effects off and see if that helps.

System > Preferences > Appearance > Visual Effects and set to None.

---

### Post by burnxez on 2010-06-24
Ok, I've used top and nothing is eating too much CPU, in fact there's never any kind of peek on cpu usage, it seems like if the freeze had never existed, is there anything else I can check?

About desktop effects, I've already tried that, but it still happens :(

Hello it's me again, I've found some info that might be useful, here are the logs of my problem:

> [ 5381.318639] Clocksource tsc unstable (delta = 229632934087 ns)
[ 5381.321258] BUG: soft lockup - CPU#1 stuck for 214s! [pulseaudio:1112]
[ 5381.321265] Modules linked in: btrfs zlib_deflate crc32c libcrc32c ufs qnx4 hfsplus hfs minix ntfs vfat msdos fat jfs xfs exportfs reiserfs nls_utf8 isofs binfmt_misc snd_hda_codec_realtek fbcon tileblit font bitblit softcursor vga16fb vgastate snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device radeon snd ttm ppdev soundcore lp drm_kms_helper parport_pc snd_page_alloc i2c_piix4 psmouse serio_raw drm i2c_algo_bit parport shpchp 8139too 8139cp mii pata_atiixp sata_sil
[ 5381.321352] CPU 1:
[ 5381.321355] Modules linked in: btrfs zlib_deflate crc32c libcrc32c ufs qnx4 hfsplus hfs minix ntfs vfat msdos fat jfs xfs exportfs reiserfs nls_utf8 isofs binfmt_misc snd_hda_codec_realtek fbcon tileblit font bitblit softcursor vga16fb vgastate snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device radeon snd ttm ppdev soundcore lp drm_kms_helper parport_pc snd_page_alloc i2c_piix4 psmouse serio_raw drm i2c_algo_bit parport shpchp 8139too 8139cp mii pata_atiixp sata_sil
[ 5381.321430] Pid: 1112, comm: pulseaudio Not tainted 2.6.32-21-generic #32-Ubuntu         
[ 5381.321435] RIP: 0033:[<00007f00707cab1f>]  [<00007f00707cab1f>] 0x7f00707cab1f
[ 5381.321449] RSP: 002b:00007f006d0ae0b0  EFLAGS: 00000202
[ 5381.321452] RAX: 00007f006d0ae100 RBX: 0000000000000010 RCX: 00000000000000a0
[ 5381.321456] RDX: 0000000000000001 RSI: 0000000000d8a7b4 RDI: 0000000000000004
[ 5381.321460] RBP: ffffffff81013cae R08: 0000000000000010 R09: 0000000000000008
[ 5381.321464] R10: 0000000000000096 R11: 0000000000000000 R12: 000000000000008f
[ 5381.321468] R13: 000000000000009b R14: 00007f0069cd1000 R15: 000000000000009b
[ 5381.321473] FS:  00007f006d0b1710(0000) GS:ffff880001c80000(0000) knlGS:0000000000000000
[ 5381.321477] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[ 5381.321481] CR2: 00007f0069cd1000 CR3: 000000002e644000 CR4: 00000000000006e0
[ 5381.321485] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 5381.321489] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 5381.321493] Call Trace:
[ 5381.333036] Switching to clocksource acpi_pm
[ 5381.333972] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.

I don't know what am I supposed to do...

---

### Post by mörgæs on 2010-06-25
The error

```
BUG: soft lockup - CPU#1 stuck for
``` appears once in a while in Pulseaudio. I have not encountered it myself, but googling gives a lot of hits.


You could try switching to Open Sound
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

or just install 9.10 and see if it works better.

---

### Post by burnxez on 2010-06-27
> **mörgæs said:**
> The error

```
BUG: soft lockup - CPU#1 stuck for
``` appears once in a while in Pulseaudio. I have not encountered it myself, but googling gives a lot of hits.


You could try switching to Open Sound
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

or just install 9.10 and see if it works better.

Thanks but it didn't work, I heard some things about Arch Linux so I installed it, and until now everything is sweet, no freezes, maybe the only bad point is that it took me a 2 days to configure and install, and it isn't "cool" by default, and I "feel" it's a little bit slower... but at least now I can work n.n

Anyway, thanks :)

---

### Post by nacho32 on 2010-06-27
was it a 64 bit you installed? or 32 ? would always go with the 32 for stability,  you could try the 9.10  it is very stable but you will have a billion updates to do,, good luck

---

### Post by mörgæs on 2010-06-27
> **burnxez said:**
> Thanks but it didn't work, I heard some things about Arch Linux so I installed it, and until now everything is sweet, no freezes, maybe the only bad point is that it took me a 2 days to configure and install, and it isn't "cool" by default, and I "feel" it's a little bit slower... but at least now I can work n.n


Great. If you like Arch, then maybe you are interested in a minimal Ubuntu:

[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

I know that your problem is solved; this is just as inspiration.


I agree on the 32 bit part. When in doubt, go for 32.

---

