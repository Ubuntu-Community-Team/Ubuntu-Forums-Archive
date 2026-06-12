---
title: "Crashes"
date: 2011-07-15
forum: General Help
---

### Post by kevin.krenz on 2011-07-15
Hello,

I have a fresh install of 11.04 on my ThinkPad, and it is crashing to a black & white text screen unpredictably. I was able to find the following in the syslog, which looks similar to what I see when it crashes:
```

Jul 15 09:34:20 kevin-laptop kernel: [  777.670138] BUG: unable to handle kernel paging request at 00766650
Jul 15 09:34:20 kevin-laptop kernel: [  777.670183] IP: [<c133c37b>] __pm_runtime_resume+0x1b/0x60
Jul 15 09:34:20 kevin-laptop kernel: [  777.670220] *pde = ba66f067 
Jul 15 09:34:20 kevin-laptop kernel: [  777.670239] Oops: 0002 [#1] SMP 
Jul 15 09:34:20 kevin-laptop kernel: [  777.670263] last sysfs file: /sys/devices/pci0000:00/0000:00:1d.7/usb2/idVendor
Jul 15 09:34:20 kevin-laptop kernel: [  777.670302] Modules linked in: parport_pc ppdev joydev snd_hda_codec_conexant binfmt_misc arc4 iwlagn thinkpad_acpi snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi iwlcore i915 pcmcia snd_seq_midi_event mac80211 snd_seq zaurus cdc_ether snd_timer usbnet cdc_acm cdc_wdm cfg80211 yenta_socket snd_seq_device pcmcia_rsrc pcmcia_core psmouse snd drm_kms_helper serio_raw drm snd_page_alloc soundcore nvram i2c_algo_bit tpm_tis tpm tpm_bios video lp parport usbhid hid firewire_ohci ahci firewire_core crc_itu_t e1000e libahci
Jul 15 09:34:20 kevin-laptop kernel: [  777.670670] 
Jul 15 09:34:20 kevin-laptop kernel: [  777.670681] Pid: 1646, comm: modem-manager Not tainted 2.6.38-10-generic #46-Ubuntu LENOVO 7417CTO/7417CTO
Jul 15 09:34:20 kevin-laptop kernel: [  777.670743] EIP: 0060:[<c133c37b>] EFLAGS: 00010202 CPU: 0
Jul 15 09:34:20 kevin-laptop kernel: [  777.670773] EIP is at __pm_runtime_resume+0x1b/0x60
Jul 15 09:34:20 kevin-laptop kernel: [  777.670800] EAX: 00766580 EBX: 00766580 ECX: f853307c EDX: 00000004
Jul 15 09:34:20 kevin-laptop kernel: [  777.670833] ESI: 00766564 EDI: 00766580 EBP: ee95be6c ESP: ee95be5c
Jul 15 09:34:20 kevin-laptop kernel: [  777.670866]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jul 15 09:34:20 kevin-laptop kernel: [  777.670895] Process modem-manager (pid: 1646, ti=ee95a000 task=ed5ba5e0 task.ti=ee95a000)
Jul 15 09:34:20 kevin-laptop kernel: [  777.670937] Stack:
Jul 15 09:34:20 kevin-laptop kernel: [  777.670950]  f853307c ece23000 00766564 00766580 ee95be80 c13a90d7 ece23000 00000010
Jul 15 09:34:20 kevin-laptop kernel: [  777.671007]  00000000 ee95bea4 f8530944 c13095e0 ecc71600 ece22800 00000296 ece23000
Jul 15 09:34:20 kevin-laptop kernel: [  777.671064]  ece22800 ece2300c ee95beb8 f8530aa7 ece22800 00000000 ecc71600 ee95bf44
Jul 15 09:34:20 kevin-laptop kernel: [  777.671121] Call Trace:
Jul 15 09:34:20 kevin-laptop kernel: [  777.671142]  [<c13a90d7>] usb_autopm_get_interface+0x27/0x60
Jul 15 09:34:20 kevin-laptop kernel: [  777.671177]  [<f8530944>] acm_port_down+0x34/0x100 [cdc_acm]
Jul 15 09:34:20 kevin-laptop kernel: [  777.671210]  [<c13095e0>] ? tty_port_close_start+0xd0/0x1c0
Jul 15 09:34:20 kevin-laptop kernel: [  777.671242]  [<f8530aa7>] acm_tty_close+0x67/0xb0 [cdc_acm]
Jul 15 09:34:20 kevin-laptop kernel: [  777.671273]  [<c13025bf>] tty_release+0x10f/0x4e0
Jul 15 09:34:20 kevin-laptop kernel: [  777.671300]  [<c1127acf>] ? do_readv_writev+0x14f/0x190
Jul 15 09:34:20 kevin-laptop kernel: [  777.671329]  [<c11283f5>] __fput+0x95/0x1c0
Jul 15 09:34:20 kevin-laptop kernel: [  777.671353]  [<c112853d>] fput+0x1d/0x30
Jul 15 09:34:20 kevin-laptop kernel: [  777.671376]  [<c112527e>] filp_close+0x4e/0x70
Jul 15 09:34:20 kevin-laptop kernel: [  777.671401]  [<c1125aa5>] sys_close+0x75/0xd0
Jul 15 09:34:20 kevin-laptop kernel: [  777.671427]  [<c150a194>] syscall_call+0x7/0xb
Jul 15 09:34:20 kevin-laptop kernel: [  777.671453]  [<c1500000>] ? detect_ht+0x14f/0x16d
Jul 15 09:34:20 kevin-laptop kernel: [  777.671478] Code: 8b 1c 24 8b 74 24 04 89 ec 5d c3 90 8d 74 26 00 55 89 e5 83 ec 10 89 5d f4 89 75 f8 89 7d fc 3e 8d 74 26 00 f6 c2 04 89 c3 74 07 <f0> ff 80 d0 00 00 00 8d 73 5c 89 f0 89 55 f0 e8 51 db 1c 00 8b 
Jul 15 09:34:20 kevin-laptop kernel: [  777.671729] EIP: [<c133c37b>] __pm_runtime_resume+0x1b/0x60 SS:ESP 0068:ee95be5c
Jul 15 09:34:20 kevin-laptop kernel: [  777.671774] CR2: 0000000000766650

```

I also noticed that in the kern.log, there is a continual loop of connecting and disconnecting a USB device. I don't know if it's related.

At any rate, I'm not sure where to start with troubleshooting this. If anyone has ideas or can point me in the right direction, I'd appreciate it.

---

### Post by kevin.krenz on 2011-07-18
Any ideas or suggestions here? I really appreciate any help.

---

### Post by kevin.krenz on 2011-07-20
Since I had a fresh install with nothing important on it, I tried re-installing using the 64-bit desktop version. For whatever reason, my computer is no longer crashing. I wish that I had the time to properly follow up on this, but I don't.

NOTE: This did not fix the problem. See later post.

---

### Post by Idefix82 on 2011-07-21
Hi Kevin,

what laptop is this exactly? I have the same problem on my Thinkpad Edge 13, running 11.04, 64 bit. Did you by any chance try playing around with Compiz effects under the Unity desktop? I had a suspicion that that's when my problems started. I will give reinstalling a shot.

---

### Post by wildmanne39 on 2011-07-21
> **Idefix82 said:**
> Hi Kevin,

what laptop is this exactly? I have the same problem on my Thinkpad Edge 13, running 11.04, 64 bit. Did you by any chance try playing around with Compiz effects under the Unity desktop? I had a suspicion that that's when my problems started. I will give reinstalling a shot.
Hi, if you need to you can reset unity by clicking on reset unity and compiz in my signature and then just reset unity and you can use this link to change settings in compiz.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by Idefix82 on 2011-07-21
> **wildmanne39 said:**
> Hi, if you need to you can reset unity by clicking on reset unity and compiz in my signature and then just reset unity and you can use this link to change settings in compiz.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

Thanks, I did that in fact. That was the only way to get back to a desktop in the first place, since enabling the cube in compiz had had the effect that all the desktop had disappeared except for the wallpaper and no key had any effect (except for the good old Alt+F1 and Alt+F7). But I still thought that something might have broken as a result of these manipulations. Of course, it is perfectly possible that the issues are completely unrelated.

---

### Post by wildmanne39 on 2011-07-21
Hi, yes they probably are unrelated, since this thread is solved you should start your own thread with a good title and we will see if we can help you.

---

### Post by Idefix82 on 2011-07-21
> **wildmanne39 said:**
> since this thread is solved you should start your own thread with a good title and we will see if we can help you.

Done: [http://ubuntuforums.org/showthread.php?t=1808956]("http://ubuntuforums.org/showthread.php?t=1808956")

---

### Post by kevin.krenz on 2011-08-17
I thought that this might be an issue with my hard drive, but replacing it didn't help - the frequent crashes resumed after a couple of days.

I noticed that the crashes were consistently related to the modem-manager process, and as I don't need it, I ran the following: 
```
sudo apt-get purge modemmanager
```

Since then, I haven't had any crashes.

---

