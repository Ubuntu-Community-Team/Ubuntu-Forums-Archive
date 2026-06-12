---
title: "Periodic Lockups"
date: 2009-11-30
forum: General Help
---

### Post by lazerradial2003 on 2009-11-30
Ever since I installed Karmic (fresh install, new home partition with old data copied to it) I've experienced both periodic lockups and more rarely, periodic instant reboots (where the machine just shuts off completely and goes to POST. Initially these happened several times a day, It's got better of late (I assume due to package updates and now only happens every couple of days). 

The last message in /var/log/syslog following the most recent lockup was this: 

```
Nov 30 12:09:39 ben-laptop kernel: [21589.728006] BUG: soft lockup - CPU#0 stuck for 61s! [updatedb.mlocat:5806]
Nov 30 12:09:39 ben-laptop kernel: [21589.728006] Modules linked in: aes_i586 aes_generic binfmt_misc ppdev vboxnetadp vboxnetflt vboxdrv snd_hda_codec_realtek snd_hda_intel snd_hda_codecNov 30 12:10:48 ben-laptop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
```

Prior to that in the log there is this: 

```
Nov 30 12:08:34 ben-laptop kernel: [21524.232007] BUG: soft lockup - CPU#0 stuck for 61s! [updatedb.mlocat:5806]
Nov 30 12:08:34 ben-laptop kernel: [21524.232007] Modules linked in: aes_i586 aes_generic binfmt_misc ppdev vboxnetadp vboxnetflt vboxdrv snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss arc4 snd_pcm ecb snd_seq_dummy iwl3945 snd_seq_oss snd_seq_midi iwlcore pcmcia iptable_filter snd_rawmidi mac80211 snd_seq_midi_event ip_tables lp yenta_socket snd_seq joydev sdhci_pci parport rsrc_nonstatic cfg80211 snd_timer sdhci pcmcia_core snd_seq_device acer_wmi led_class psmouse serio_raw snd soundcore snd_page_alloc x_tables dm_raid45 xor fbcon tileblit font bitblit softcursor i915 drm i2c_algo_bit b44 ssb mii video intel_agp agpgart output
Nov 30 12:08:34 ben-laptop kernel: [21524.232007] 
Nov 30 12:08:34 ben-laptop kernel: [21524.232007] Pid: 5806, comm: updatedb.mlocat Not tainted (2.6.31-15-generic #50-Ubuntu) Aspire 5630     
Nov 30 12:08:34 ben-laptop kernel: [21524.232007] EIP: 0060:[<c0266e06>] EFLAGS: 00010286 CPU: 0
Nov 30 12:08:34 ben-laptop kernel: [21524.232007] EIP is at ext4_iget+0x56/0x710
Nov 30 12:08:34 ben-laptop kernel: [21524.232007] EAX: f6e23300 EBX: f76fbe00 ECX: 00000000 EDX: f6e23300
Nov 30 12:08:34 ben-laptop kernel: [21524.232007] ESI: ea47c9a8 EDI: 00001fff EBP: e75d3dc4 ESP: e75d3d64
Nov 30 12:08:34 ben-laptop kernel: [21524.232007]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Nov 30 12:08:34 ben-laptop kernel: [21524.232007] CR0: 8005003b CR2: f76fbe00 CR3: 2b134000 CR4: 000006d0
Nov 30 12:08:34 ben-laptop kernel: [21524.232007] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Nov 30 12:08:34 ben-laptop kernel: [21524.232007] DR6: ffff0ff0 DR7: 00000400
Nov 30 12:08:34 ben-laptop kernel: [21524.232007] Call Trace:
Nov 30 12:08:34 ben-laptop kernel: [21524.232007]  [<c026c6bf>] ext4_lookup+0x7f/0x100
Nov 30 12:08:34 ben-laptop kernel: [21524.232007]  [<c0570ea8>] ? _spin_lock+0x8/0x10
Nov 30 12:08:34 ben-laptop kernel: [21524.232007]  [<c01f9b36>] ? d_alloc+0x136/0x190
Nov 30 12:08:34 ben-laptop kernel: [21524.232007]  [<c01efde7>] real_lookup+0xb7/0x110
Nov 30 12:08:34 ben-laptop kernel: [21524.232007]  [<c01f153d>] do_lookup+0x8d/0xb0
Nov 30 12:08:34 ben-laptop kernel: [21524.232007]  [<c01f1ee4>] __link_path_walk+0x584/0xb90
Nov 30 12:08:34 ben-laptop kernel: [21524.232007]  [<c01df8eb>] ? __slab_alloc+0x19b/0x260
Nov 30 12:08:34 ben-laptop kernel: [21524.232007]  [<c04877f0>] ? apparmor_file_alloc_security+0x20/0x90
Nov 30 12:08:34 ben-laptop kernel: [21524.232007]  [<c0570ea8>] ? _spin_lock+0x8/0x10
Nov 30 12:08:34 ben-laptop kernel: [21524.232007]  [<c01f2681>] path_walk+0x41/0x90
Nov 30 12:08:34 ben-laptop kernel: [21524.232007]  [<c01f2721>] do_path_lookup+0x51/0x90
Nov 30 12:08:34 ben-laptop kernel: [21524.232007]  [<c01f323c>] user_path_at+0x3c/0x70
Nov 30 12:08:34 ben-laptop kernel: [21524.232007]  [<c01eb8a5>] vfs_fstatat+0x35/0x70
Nov 30 12:08:34 ben-laptop kernel: [21524.232007]  [<c01eb93b>] vfs_lstat+0x1b/0x20
Nov 30 12:08:34 ben-laptop kernel: [21524.232007]  [<c01eb954>] sys_lstat64+0x14/0x30
Nov 30 12:08:34 ben-laptop kernel: [21524.232007]  [<c010336c>] syscall_call+0x7/0xb
```

Repeated about once a minute all the way to the start of the log. 

Things I've tried:
[LIST]
[*]A completely new home partition - I once experienced a similar problem when trialing suse which turned out to be due to a corrupted home partition
[*]Running KDE instead of gnome, same problem occurs
[*]Disabling desktop effects
[/LIST]

Any advice on where to go next with this problem appreciated because other than that Karmic is running a treat!

---

### Post by lazerradial2003 on 2009-12-02
OK The instant reboots seem to be directly related to the wifi card. Extracts from the log each time one has occurred are attached, a majority of them seem to occur when the wifi connection is being established. In addition I managed to (sort of) repeatably cause the probelm by booting up with the wifi set to off using the switch on the front and then turning it on - it would go to a black screen then post as soon as the card was activated. 

Log file extracts attached. Any suggestions on what to try next much appreciated.

---

### Post by lazerradial2003 on 2009-12-03
Happening about two times a day at the moment, going to go back to Jaunty until Karmics a bit more stable. If I'm just going to install over the top of Karmic, do I need to delete any of the config folders in my home folder (separate partition).

---

### Post by jegerjensen on 2009-12-03
Could it be a problem with the ext4 driver? 

I don't know anything about the intrinsics of the kernel, so  I'm not sure.  But, since the call trace involves an ext4_lookup, it does seem reasonable.  You could try reinstalling karmic using ext3 and see if the problems go away...

---

### Post by lazerradial2003 on 2009-12-04
Sounds possible, thanks for the suggestions. Do you know if there's any tool I can run off a Live CD to convert and ext4 partition to ext3? If not I can do an install on a spare partition but would be useful if I could convert because then all other variables stay the same.

---

### Post by lazerradial2003 on 2009-12-06
Did a fresh install of Karmic with new home partition, both ext3 instead of ext4. Same crash occurred within minutes. Going to roll back to jaunty untill karmic is a bit more stable. Thanks for your ideas those guys!

---

### Post by lazerradial2003 on 2010-01-03
The plot thickens. Having gone back to Jaunty for a bit while I try and work out what's causing the problem, I had to install Fedora to test something out. The latest Fedora 12 release crashes in exactly the same way, just a "click" and then the computer goes back to POST. I'm fairly sure it's not hardware related because Jaunty runs quite happily 24/7 without crashing. Any suggestions on possible common factors or next steps to troubleshoot this would be very much appreciated!

---

### Post by pveurshout on 2010-01-03
[s]Could you try some of the different kernels available for Jaunty? I experienced the exact same kind of lockups and error messages in dmesg, but it turned out to go away after some kernel updates, and then come back with the next..

Problems:
2.6.28-13
2.6.28-14
2.6.28-16

Perfect:
2.6.28-15
2.6.28-17

Not sure:
2.6.28-11 (original)[/s]

Sorry, I noticed you didn't have any problems in Jaunty. Should read better next time. Perhaps the same thing with Karmic, though?

---

### Post by lazerradial2003 on 2010-01-05
They sounds like similar symptons so definitely sounds like it's worth trying, do you have any recommendations for the easiest way to move between kernels whilst still being able to get back to the previous one should it get even worse?

---

### Post by lazerradial2003 on 2010-03-03
Having rolled back to Jaunty because I was unable to solve these problems I've noticed a few new things. Firstly after an update to my Jaunty install last week, the problems now occur in Jaunty, does anyone know how to find out what updates were installed and when so I can try and narrow down what may be causing it? 

Secondly I get exactly the same symptoms when running the current stable release of Fedora on the same computer (Acer Aspire 5630)

Comments much appreciated!

---

### Post by lazerradial2003 on 2010-03-04
I'm looking at xserver as a possible common factor (since the problem seems to occur across distributions).

Does the attached logfile (from: cat .xsession-errors) mean anything to anyone?

---

### Post by pveurshout on 2010-03-19
> **lazerradial2003 said:**
> They sounds like similar symptons so definitely sounds like it's worth trying, do you have any recommendations for the easiest way to move between kernels whilst still being able to get back to the previous one should it get even worse?

Sorry for my delayed reply.. haven't been around on the forums much lately. From the Grub boot menu you can choose a kernel to boot with. This doesn't change anything in your system, so you can just roll back to the previous one by selecting it the next time you boot. You can install older kernels from the Synaptic Package Manager if there's just a few listed (let me know if you need help with that).

> **lazerradial2003 said:**
> I'm looking at xserver as a possible common factor (since the problem seems to occur across distributions).

Does the attached logfile (from: cat .xsession-errors) mean anything to anyone?

X is known to be the cause of some problems. I've never managed to figure out anything by looking at its logs, though. Sorry. I have never had any real hard lock ups because of X, by the way.

---

### Post by lazerradial2003 on 2010-03-21
Thanks for the reply, it's been a strange problem so far - the problems started happening in Jaunty as well as Karmic following an update and then went away again about 3 weeks later following another update. Booting with a different kernel didn't seem to fix it but it seems to come and go following updates which include new kernels so not sure what to think! 

Thanks again for your help. hopefully it won't start happening again with the next update!

---

### Post by pveurshout on 2010-03-25
Have you tried various alternative kernels or just one? (in that case you may have just been unlucky) Based upon your experience that the problem disappears and reappears following kernel updates, I would still give this possibility another shot. From your comment I understand that you do have at least one kernel version currently installed that works! :) Perhaps you could try finding it in a systematic manner: use a certain kernel, once it locks up, you start using the previous version. Once that one locks up, you start using the one before that. (Make sure you know which kernel you're booting, or else your "research results" are useless as you still don't know which kernels work and which don't.)

---

### Post by lazerradial2003 on 2010-03-27
Cheers for the response, I've tried four or five different kernels including two which didn't cause any problems when I used them previously. I've kept a record of kernel, what was I was doing when the crash occurred etc going back a few months and can't seen any discernable pattern. I'm starting to wonder if it's some sort of intermittent hardware failure which just happened to coincide with an update originally!

---

