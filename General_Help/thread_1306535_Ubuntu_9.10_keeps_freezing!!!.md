---
title: "Ubuntu 9.10 keeps freezing!!!"
date: 2009-10-30
forum: General Help
---

### Post by rwt911 on 2009-10-30
Hello,

I have a Lenovo Ideapad Y550, and I just upgraded to Ubuntu 9.10. It keeps freezing and getting kernel panics on my system! Does any one else have this problem. Should I revert to an older kernel?

---

### Post by prem1er on 2009-10-30
Monitor /var/log/syslog and post results after it crashes.

---

### Post by rwt911 on 2009-10-30
Ok hold on

---

### Post by rwt911 on 2009-10-30
Ok here it is, it was to big to upload as a text file so I zip'd it.

---

### Post by rwt911 on 2009-10-30
It has done it 3 times since posting the file!!

](*,)
](*,)
](*,)

I never had any problems with Ubuntu 9.04 and kernels up to 2.6.30!!

---

### Post by rwt911 on 2009-10-30
Make that 5!

](*,)
](*,)
](*,)

---

### Post by rwt911 on 2009-10-30
bump

---

### Post by prem1er on 2009-10-30
bump this a couple more times, i think someone will help you if you keep it up

---

### Post by philippe_carlo on 2009-10-30
It seems like you are having some kind of memory-related problem:
```

Oct 30 14:57:24 rwt-laptop kernel: [   59.890079] wlan0: no IPv6 routers present
Oct 30 14:57:25 rwt-laptop kernel: [   61.040107] Corrupted low memory at ffff880000005e10 (5e10 phys) = 82000200170000
Oct 30 14:57:25 rwt-laptop kernel: [   61.040112] Corrupted low memory at ffff880000005e68 (5e68 phys) = 0001fa00
Oct 30 14:57:25 rwt-laptop kernel: [   61.040115] Corrupted low memory at ffff880000005e88 (5e88 phys) = 00000001
Oct 30 14:57:25 rwt-laptop kernel: [   61.040118] Corrupted low memory at ffff880000005f48 (5f48 phys) = 9000000000000
Oct 30 14:57:25 rwt-laptop kernel: [   61.040121] ------------[ cut here ]------------
Oct 30 14:57:25 rwt-laptop kernel: [   61.040130] WARNING: at /build/buildd/linux-2.6.31/arch/x86/kernel/check.c:134 check_for_bios_corruption+0xe5/0x100()
Oct 30 14:57:25 rwt-laptop kernel: [   61.040133] Hardware name: INVALID
Oct 30 14:57:25 rwt-laptop kernel: [   61.040135] Memory corruption detected in low memory
Oct 30 14:57:25 rwt-laptop kernel: [   61.040137] Modules linked in: binfmt_misc ppdev vboxnetflt vboxnetadp vboxdrv snd_hda_codec_intelhdmi snd_hda_codec_si3054 snd_hda_codec_realtek snd_hda_intel arc4 ecb snd_hda_codec joydev snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy iwlagn uvcvideo snd_seq_oss asus_laptop iwlcore lp psmouse sdhci_pci snd_seq_midi videodev sdhci snd_rawmidi v4l1_compat v4l2_compat_ioctl32 snd_seq_midi_event serio_raw ricoh_mmc led_class parport snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc mac80211 iptable_filter ip_tables x_tables cfg80211 fbcon tileblit font bitblit softcursor ohci1394 ieee1394 tg3 i915 drm i2c_algo_bit intel_agp video output
Oct 30 14:57:25 rwt-laptop kernel: [   61.040201] Pid: 9, comm: events/0 Not tainted 2.6.31-14-generic #48-Ubuntu
Oct 30 14:57:25 rwt-laptop kernel: [   61.040203] Call Trace:
Oct 30 14:57:25 rwt-laptop kernel: [   61.040209]  [<ffffffff8105e788>] warn_slowpath_common+0x78/0xb0
Oct 30 14:57:25 rwt-laptop kernel: [   61.040212]  [<ffffffff8105e81c>] warn_slowpath_fmt+0x3c/0x40
Oct 30 14:57:25 rwt-laptop kernel: [   61.040215]  [<ffffffff810366a5>] check_for_bios_corruption+0xe5/0x100
Oct 30 14:57:25 rwt-laptop kernel: [   61.040218]  [<ffffffff810366c0>] ? check_corruption+0x0/0x30
Oct 30 14:57:25 rwt-laptop kernel: [   61.040221]  [<ffffffff810366c9>] check_corruption+0x9/0x30
Oct 30 14:57:25 rwt-laptop kernel: [   61.040226]  [<ffffffff810737a5>] run_workqueue+0x95/0x170
Oct 30 14:57:25 rwt-laptop kernel: [   61.040229]  [<ffffffff81073924>] worker_thread+0xa4/0x120
Oct 30 14:57:25 rwt-laptop kernel: [   61.040233]  [<ffffffff81078b30>] ? autoremove_wake_function+0x0/0x40
Oct 30 14:57:25 rwt-laptop kernel: [   61.040236]  [<ffffffff81073880>] ? worker_thread+0x0/0x120
Oct 30 14:57:25 rwt-laptop kernel: [   61.040238]  [<ffffffff81078746>] kthread+0xa6/0xb0
Oct 30 14:57:25 rwt-laptop kernel: [   61.040242]  [<ffffffff810130ea>] child_rip+0xa/0x20
Oct 30 14:57:25 rwt-laptop kernel: [   61.040245]  [<ffffffff810786a0>] ? kthread+0x0/0xb0
Oct 30 14:57:25 rwt-laptop kernel: [   61.040247]  [<ffffffff810130e0>] ? child_rip+0x0/0x20
Oct 30 14:57:25 rwt-laptop kernel: [   61.040249] ---[ end trace 45d2074a78711a5d ]---
Oct 30 14:57:37 rwt-laptop wpa_supplicant[1446]: CTRL-EVENT-SCAN-RESULTS 
Oct 30 14:58:17 rwt-laptop wpa_supplicant[1446]: CTRL-EVENT-SCAN-RESULTS 

```

The system log suggests that there may be a problem with your BIOS. You may want to take a shot at updating its firmware. Also try the memory test that comes with the live CD. If this does not help or comes up with an explanation, it may well be a kernel bug in which case you should report it.

---

### Post by michaelzap on 2009-10-30
I did a clean install of Karmic x64 on my Y530 (with integrated Intel video) last night, and I had several (more than six) freezes before the end of the evening. The mouse pointer would freeze and only a hard reboot would bring it back up. I would get kernel crash notifications after restarting (and send in the error reports).

I also have "Corrupted low memory" lines in my syslog, so I think that the issue is the same as you're experiencing.

So far I'm not all that concerned. Karmic is dramatically better than Jaunty on this machine (puseaudio works, no video tearing or screen dimming, and excellent performance). So far I haven't had a freeze today (crosses fingers), so it might have been something that worked itself out after a while.

In any case, I don't think that it's your laptop in particular. There may be a kernel or driver issue, and if we keep reporting it they'll patch it. Obviously if you're system is unusable that's not something that you can ignore...

---

### Post by philippe_carlo on 2009-10-30
> **michaelzap said:**
> I did a clean install of Karmic x64 on my Y530 (with integrated Intel video) last night, and I had several (more than six) freezes before the end of the evening. The mouse pointer would freeze and only a hard reboot would bring it back up. I would get kernel crash notifications after restarting (and send in the error reports).

I also have "Corrupted low memory" lines in my syslog, so I think that the issue is the same as you're experiencing.

So far I'm not all that concerned. Karmic is dramatically better than Jaunty on this machine (puseaudio works, no video tearing or screen dimming, and excellent performance). So far I haven't had a freeze today (crosses fingers), so it might have been something that worked itself out after a while.

In any case, I don't think that it's your laptop in particular. There may be a kernel or driver issue, and if we keep reporting it they'll patch it. Obviously if you're system is unusable that's not something that you can ignore...

It may be helpful to report the bug.

---

### Post by michaelzap on 2009-10-30
> **philippe_carlo said:**
> It may be helpful to report the bug.

I sent kernel crash reports. If it happens again and I can gather enough info to make a proper bug report, I will.

---

### Post by rwt911 on 2009-10-30
Thanks for all your help, I have reported it.

---

### Post by michaelzap on 2009-10-30
> **rwt911 said:**
> Thanks for all your help, I have reported it.

Can you please post a link to your bug report? I just had another freeze, and I'd like to add info to it.

---

### Post by commonplace on 2009-10-30
IdeaPad Y530 here, with same issues. Could not be more disappointed with this release of Ubuntu.

The installation process was hell on my wife's laptop, as well, and it's totally different (hers is running 32-bit 9.10 on an HP Compaq laptop, and mine was 64-bit on the Lenovo IdeaPad).

Definitely won't be sticking with this version. Worst I've ever used of Ubuntu. I'm sure plenty of people are unaffected by these particular issues and think it's wonderful, but not us.

/Kevin

---

### Post by rwt911 on 2009-10-30
[Here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/465617") is my bug report

---

### Post by michaelzap on 2009-10-31
I just discovered something that might be useful. My sound had also stopped working, and the memory errors seemed to be related to the (integrated) sound card. And it turns out that the software modem on my laptop is a sub-element of the sound card...

So I disabled the proprietary driver for my modem in System -> Hardware Drivers. After I did that, my sound card showed up again in the Sound Control Panel (before there were no detected devices in there). So maybe this is the root of the problem?

If so, I can certainly live without a modem (which I've never used and don't plan to use).

---

### Post by kircher on 2009-11-01
I believe this freezing might be the wpa_supplicant spamming your system with requests. I have the same problem, and in my logs, the last events before the system crashes and a restart is needed are always the same. Here is part of my syslog:
> Nov  1 22:15:55 desktop pulseaudio[1524]: ratelimit.c: 117 events suppressed
Nov  1 22:16:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:16:22 desktop pulseaudio[1524]: ratelimit.c: 67 events suppressed
Nov  1 22:17:01 desktop CRON[2182]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  1 22:17:06 desktop pulseaudio[1524]: ratelimit.c: 10 events suppressed
Nov  1 22:18:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:20:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:22:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:24:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:26:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:28:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:30:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:32:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:34:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:36:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:38:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:40:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:42:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:44:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
[COLOR="Red"]Nov  1 22:46:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS[/COLOR] 
[COLOR="SeaGreen"]Nov  1 22:49:41 desktop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.[/COLOR]
Nov  1 22:49:41 desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="740" x-info="http://www.rsyslog.com"] (re)start
Nov  1 22:49:41 desktop rsyslogd: rsyslogd's groupid changed to 102
Nov  1 22:49:41 desktop rsyslogd: rsyslogd's userid changed to 101
Nov  1 22:49:41 desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  1 22:49:41 desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  1 22:49:41 desktop kernel: [    0.000000] Linux version 2.6.31-14

I highlighted in red the last entry before the crash, and the first entry after restart in green. My previous system crashes (freezes) have the same log entry patterns. Plus I found this as well: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1799427.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1799427.html)

Here is a link to my thread [http://ubuntuforums.org/showthread.php?t=1308826](http://ubuntuforums.org/showthread.php?t=1308826)

---

### Post by kircher on 2009-11-01
I filed a bug report. Here it is: [https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/468519](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/468519)

---

### Post by commonplace on 2009-11-01
Just posted this in a couple of other threads:

Alright, here's something weird (at least, to me): I wiped out everything and installed **K**ubuntu 9.10 -- and it works great. Sound works. No freezes. No kernel errors. No speed issues. Everything is great.

I don't understand why this is, unless my issues were specific to GNOME...?? That doesn't really make sense to me, but it's the only explanation I have at the moment. I mean, this is the same kernel... so it's not the kernel, apparently.

I prefer KDE over GNOME but I'm going to stick with this for awhile and adapt -- it's better than having an unusable GNOME-based system (Ubuntu).

/Kevin

---

### Post by red_five on 2009-11-15
I have 4 installs of Ubuntu 9.10:
1- 32-bit server
2- 32-bit desktop
1- 64-bit desktop

The 64-bit and one of the 32-bit desktop installs are on laptops, the other 32-bit desktop install is a PXE netboot via NFSroot. On my server and 2 laptops I saw repeated kernel panics until I blacklisted the intel_agp module. My server is headless, so no need for X; my laptop uses PCI-Express, so no need for AGP, and the other laptop seems to work just fine without the module, even though it's old enough you'd think it would need intel_agp.

The pattern was always the same: any of the boxes would run fine for 8-10 minutes, then suddenly or gradually become unresponsive over about a minute, then finally caps lock and scroll lock would begin flashing: the sure sign of a kernel panic. Hard reboot, disk scan, and another few minutes to work until it happened again. It took me a couple hours on the server to figure it out, then just once or twice to determine the same fix was necessary on my other machines. Incedentally, if you have a machine that really doesn't need intel_agp, but has it loaded anyway, and you're getting this sort of behavior, just modprobe -r intel_agp, and that should stabilize your system until the next boot, by which time I hope you've blacklisted the module entirely.

---

### Post by Sobhy on 2009-11-15
I upgraded my Dell 5100 from Ubuntu 8.10 to 9.10 and when I boot up it gets to the main page, but when I try to open any programs from that page, it freezes up and have to do a hard reboot. If I bring it up in Safe Mode, it works great. Any suggestions on a fix. Thanks

---

### Post by nutznboltz on 2010-10-11
Can you please test and report if this works?

memory_corruption_check_size=128K

in the boot options.

The default is

memory_corruption_check_size=64K

but it seems that's not enough for some systems.

Thanks

If you don't know how to set BootOptions read

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Also this thread is very important to anyone looking at this bug

[http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-07/msg04621.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-07/msg04621.html)

---

