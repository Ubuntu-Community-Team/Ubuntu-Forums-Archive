---
title: "Jaunty Freezes at random"
date: 2009-07-06
forum: General Help
---

### Post by ProphetOfDoom on 2009-07-06
Hi,
 
Over the last few weeks jaunty has become very unstable. It will freeze at random so that there is no response from mouse, keyboard or wacom tablet. The image on the screen is still visible. All input device lights go out. The only solution is to pull the plug out.
 
I've tried starting the sshd process in the hope of getting in after a crash but I can't - it may also be dropping the network connection.
 
There is nothing in any log I can find to indicate the problem. It's as if the system dies before it has a chance to make a log entry.
 
Using gimp and my wacom intuos I can be sure the isssue will occur very quickly, but just websurfing with firefox can also cause the crash. It happens with or without compiz running. This problem is killing me - I hit it 6 times in an hour yesteday.
 
I can't find a fix for this and I've googled like forever.
 
Anyone got any ideas? 
 
I'm runing AMD Athlon 2800, radeon 9200, 750Mb mem, intuos3. PC is silver if that helps.

---

### Post by MasterNetra on 2009-07-06
hmm sounds like it maybe a kernel issue, is jaunty up to date? Did your system do this from install or was it shortly after a kernel update? Additionally you could try disabling compiz for a period of time just in case its actually a compiz issue.

---

### Post by ProphetOfDoom on 2009-07-06
Hi,
 
Thanks - I am completely up to date with updates - I always install the latest recommended patches. 
 
I upgraded from 8.10 when 9.04 was released and initially it was ok. I can't be sure exactly when it started going bad - seems a lot lot worse in the last week and is now virtually unusable - but I do recall a couple of kernel updates in the last few weeks. Actually I tried moving to fedora in desparation yesterday (and now remember why I moved to ubuntu) and got the same issue there (albeit only once). So either my hardware is broken (memtester ran ok), or this is a kernel issue or a driver issue as you say. 
 
I've tried disabling compiz but that doesn't seem to help.

---

### Post by MasterNetra on 2009-07-06
Did you try a "Fresh" install of Jaunty? You could additionally try running jaunty without those additional Kernel Updates, just make sure when your updating you make sure that they are unchecked.

---

### Post by ProphetOfDoom on 2009-07-06
Not yet - I guess that makes sense. I'll try it tonight

---

### Post by Trapper on 2009-07-06
I can relate to this problem. I've had it with every install of U9.04 I've done, on 64 & 32 bit, various computers, with vesa video, nv video, nvidia video. It usually happens shortly after returning to the machines after they've been idle for a while or just a few minutes after boot up. It also sometimes happens after screensaver activation. Other times it doesn't. Like I said, various machines, various video drivers, etc. There's really no common denominator except that they all freeze occasionally and it's almost always when very little resources are being used. 64 bit tends to freeze more often than the 32 bit installs but they both do. None of my Fedora 10 & 11 installs on these same boxes have this issue. I ran U9.10 Alpha for a while. It also had the freeze problem. Also, U8.10 doesn't seem to have this issue. I never upgrade and always keep my machine up to date on a daily basis. The problem exists from the initial installs onward.

---

### Post by Serenity55 on 2009-07-06
I have been having this problem as well. It happens incredibly quickly, I have been moving the mouse and have had it stop midmotion. There is no way to recover short of reboot. INCREDIBLY annoying. Hasn't happened in any previous version of Ubuntu.

---

### Post by ProphetOfDoom on 2009-07-12
Done a fresh install. Web surfing with Firefox seems more stable and hasn't crashed in 5 days since the reinstall. Until tonight. Froze 4 times whilst using gimp/ wacom tablet. What does that suggest I wonder.....

---

### Post by Serenity55 on 2009-07-19
I still have this problem a lot, and I don't have a Wacom tablet. I have been trying to look for patterns and I noticed that it happens a lot when skype is running. Anyone else notice this???

---

### Post by ProphetOfDoom on 2009-07-19
I don't use skype. I can't find a pattern either and it appears a lot of people are having this issue, but without any log files I can't see how I can even begin to fix this.

I'm thinking of ditching Ubuntu now. :(

---

### Post by bsell on 2009-07-25
I can confirm the random freezes on 64-bit Jaunty from clean install. 

Machine specs:

Intel Dual-Core E5300 @ 2.6GHz
4 GB 1066 MHz DDR2 RAM
Nvidia GeForce 9500 GT 512 MB video card
D-Link Wireless card

After system restart, the messages log file always show:

> Jul 25 14:14:37 nooboontu pulseaudio[3400]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
Jul 25 14:34:17 nooboontu -- MARK --
Jul 25 14:54:17 nooboontu -- MARK --
Jul 25 15:24:10 nooboontu syslogd 1.5.0#5ubuntu3: restart.

---

### Post by thijsz on 2009-08-03
same issue here
using 2.6.28-3-rt #12-Ubuntu SMP PREEMPT RT Fri Apr 17 10:09:11 UTC 2009 i686 GNU/Linux

EDIT : forgot to mention that this is a clean install

i have read some posts about this being linked to the 9.04 intel video driver, but i cant seem to find these any more ...

messages log just before freeze :

Aug  3 22:17:23 ubuntu9 kernel: [  442.688903] Modules linked in: binfmt_misc i915 drm ppdev lp parport bridge stp bnep input_polldev video output dv1394 raw1394 snd_hda_intel hid_dell snd_usb_audio snd_pcm_oss snd_mixer_oss snd_pcm snd_usb_lib snd_seq_dummy snd_hwdep snd_seq_oss snd_seq_midi snd_rawmidi dcdbas snd_seq_midi_event e100 iTCO_wdt psmouse mii snd_seq iTCO_vendor_support ohci1394 serio_raw snd_timer pcspkr snd_seq_device ieee1394 snd soundcore usbhid snd_page_alloc intel_agp floppy agpgart fbcon tileblit font bitblit softcursor
Aug  3 22:17:23 ubuntu9 kernel: [  442.688970] Pid: 748, comm: kjournald2 Tainted: G        W  2.6.28-3-rt #12-Ubuntu
Aug  3 22:17:23 ubuntu9 kernel: [  442.688973] Call Trace:
Aug  3 22:17:23 ubuntu9 kernel: [  442.688985]  [<c050f991>] ? printk+0x18/0x1f
Aug  3 22:17:23 ubuntu9 kernel: [  442.688992]  [<c01307ec>] __schedule_bug+0x6c/0x80
Aug  3 22:17:23 ubuntu9 kernel: [  442.688996]  [<c05101cd>] schedule+0x50d/0x760
Aug  3 22:17:23 ubuntu9 kernel: [  442.689002]  [<c019e18a>] ? drain_cpu_pagevecs+0xba/0x140
Aug  3 22:17:23 ubuntu9 kernel: [  442.689008]  [<c05112f6>] rt_spin_lock_slowlock+0x176/0x220
Aug  3 22:17:23 ubuntu9 kernel: [  442.689014]  [<c0511b2d>] __rt_spin_lock+0x4d/0x50
Aug  3 22:17:23 ubuntu9 kernel: [  442.689020]  [<c0511b38>] rt_spin_lock+0x8/0x10
Aug  3 22:17:23 ubuntu9 kernel: [  442.689027]  [<c01bdd7d>] kmem_cache_free+0x3d/0x130
Aug  3 22:17:23 ubuntu9 kernel: [  442.689035]  [<c025c4e5>] __journal_remove_journal_head+0xa5/0x130
Aug  3 22:17:23 ubuntu9 kernel: [  442.689041]  [<c025e20f>] jbd2_journal_put_journal_head+0x5f/0xd0
Aug  3 22:17:23 ubuntu9 kernel: [  442.689046]  [<c02595fa>] jbd2_journal_commit_transaction+0x88a/0xf00
Aug  3 22:17:23 ubuntu9 kernel: [  442.689052]  [<c0132679>] ? load_balance_newidle+0x89/0x250
Aug  3 22:17:23 ubuntu9 kernel: [  442.689057]  [<c0511b38>] ? rt_spin_lock+0x8/0x10
Aug  3 22:17:23 ubuntu9 kernel: [  442.689060]  [<c025cec2>] kjournald2+0xb2/0x1f0
Aug  3 22:17:23 ubuntu9 kernel: [  442.689066]  [<c0151a40>] ? autoremove_wake_function+0x0/0x50
Aug  3 22:17:23 ubuntu9 kernel: [  442.689069]  [<c025ce10>] ? kjournald2+0x0/0x1f0
Aug  3 22:17:23 ubuntu9 kernel: [  442.689073]  [<c015164c>] kthread+0x3c/0x70
Aug  3 22:17:23 ubuntu9 kernel: [  442.689076]  [<c0151610>] ? kthread+0x0/0x70
Aug  3 22:17:23 ubuntu9 kernel: [  442.689081]  [<c0105547>] kernel_thread_helper+0x7/0x10

---

### Post by Primefalcon on 2009-08-03
are you using the ext4 filesystem?

---

