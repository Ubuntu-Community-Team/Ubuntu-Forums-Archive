---
title: "Ubuntu 9.10 Karmic won't wake up from suspend (sleep) mode"
date: 2009-12-25
forum: General Help
---

### Post by joe-the-indian on 2009-12-25
Hello :)

I've got a Toshiba Satellite l30-113 laptop, when I send it to sleep mode it won't wake up afterwards - just showing blinking cursor. 

I tried to figure out which device causes this - followed pldg's instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=1138178&highlight=wake"), but dmesg's output doesn't make any sense to me so I attached it here - can anyone help please :)

---

### Post by Dave Kristol on 2010-01-16
I'm experiencing something that may be related.  I've got a Dell Inspiron 1420, also running Karmic, which I recently installed (upgraded, that is).

I've seen these different behaviors when I try to resume from suspend by opening the laptop's lid (apart from normal behavior):

1) I get the login box, but the keyboard and trackpad are dead -- no response.  After maybe a minute, the laptop spontaneously goes back to sleep.  Hitting the Power button usually resumes the laptop successfully, though sometimes it repeats the back-to-sleep behavior.

2) The login box appears briefly, then disappears, leaving just a blinking text cursor in the upper left.  I can close the lid and the laptop sleeps.  When I open the lid, the laptop usually resumes successfully.

A few times, when I tried to resume the laptop after one of the above, it bypassed the login screen altogether and resumed my session.  No password provided.

The suspend/resume seemed reasonably reliable in prior Ubuntu releases.

Nothing stood out as odd when I looked at /var/log/pm-suspend.log, except of course for the suspend that immediately followed the resume.

Dave Kristol

---

### Post by efflandt on 2010-01-16
Did your laptop show anything in pm-suspend.log at all about resuming?

I have one troublesome laptop that I thought initially came back from 9.10 suspend to gui login, but keyboard/mouse were unresponsive.  I got it to hibernate successfully once, which logged the thawing in pm-suspend.log.  But when I tried suspend again, it only comes back to a black screen with no backlight, and whatever that sets seems to do likewise for hibernate, which actually shows the color progress screen saying Waking...please wait, then blacks out.  pm-suspend log shows it going into suspend or hibernate, but never showed anything waking from suspend, and no longer shows thawing from hibernate.

All other laptops/desktops I have used work fine for suspend or hibernate.

---

### Post by Dave Kristol on 2010-01-17
> **efflandt said:**
> Did your laptop show anything in pm-suspend.log at all about resuming?

pm-suspend.log showed what looked to me like a normal suspend sequence followed by a normal resume sequence.  And the stuff in the log looked the same (based on casual examination) for the "bad" case vs. the "good" case.

Dave Kristol

---

### Post by fixedd on 2010-01-24
> **Dave Kristol said:**
> 1) I get the login box, but the keyboard and trackpad are dead -- no response.  After maybe a minute, the laptop spontaneously goes back to sleep.  Hitting the Power button usually resumes the laptop successfully, though sometimes it repeats the back-to-sleep behavior.

This is the same problem I'm having (also after an upgrade). The only difference is that it only happens to me if I try to resume while running on battery power. If I'm plugged in it works fine.

---

### Post by athrash on 2010-01-24
Similar problem. I put the computer to sleep and it won't wake up. So I haven't been on Ubuntu for some time now. Hoping this will come up as a fix soon.

---

### Post by shawnhcorey on 2010-01-26
I have an old PowerBook G4 and I have a similar problem.  It won't suspend when the lid is closed.

However, I think I have a work around.  I can suspend it from the Quit/Logout menu (top panel, extreme right).  But when I restart it, I get a blank screen.  I tried switching to a text console (Ctrl+Alt+F1) but no dice (Ctrl+Alt+F7 switches back to the GUI).  So I tried killing X Window (Ctrl+Alt+Backspace) and the Lock-Screen/Request-Password box popped up.  Since then, after each suspend, it seems to work normally.

Please note, your mileage may vary.

---

### Post by freedryk on 2010-01-26
I've got it, too.  Lenovo x61t, pm-suspend.log shows normal suspend sequence, but my suspend light never stops blinking--typically it blinks for 3 seconds or so while suspending, but now it just keeps on blinking.  Suspend still working in windows.  I tried booting into an older kernel, but same result.  I put it to sleep last night without noticing that it didn't complete the suspend, and when I woke up this morning the battery was dead, so the laptop is definitely not going to sleep.  I can't break out of the suspend sequence either--when I open the lid, the laptop just keeps blinking.

---

### Post by freedryk on 2010-01-26
Just discovered I can suspend as long as I don't login to gnome.  I dropped to the terminal before logging into gdm and sudo pm-suspend worked.  On resume I returned to gdm and closed the lid, and it suspended properly again.  Then I logged into gnome and suspend failed as before.

---

### Post by freedryk on 2010-01-26
Also I started a bug for this: [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/512972](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/512972)

---

### Post by InfiniteImpulse on 2010-01-26
I'm having the same problem on my HP Pavilion dv9000. I am a first time Linux user and this is the only problem I have encountered after about a week of use. I hope there is a fix soon because I would like to dedicate this laptop to Ubuntu instead of continuing to dual boot with Vista :(

---

### Post by whittaker007 on 2010-01-28
Pretty much the same issue here except I'm using a desktop HTPC rather than a laptop. It seems the sleep is triggered by the power management settings after a certain amount of time of inactivity. When I try to wake it up I get a blank command prompt with a flashing cursor, but keyboard input doesn't seem to work and I have no choice but to reboot.

Even more annoying is that it sleeps even when there are programs running in the background (encoding video with HandBrake for example). And when I reboot the sound is muted to top it all off.

I've turned off sleep mode altogether for now, but I really would like some kind of sensible power management to work in Ubuntu.

---

### Post by mozilla2004 on 2010-01-28
I have a similar problem with my desktop computer.  After computer goes to sleep, it doesn't wake up.  Sometimes I hear the computer wake up, but my monitors stay off.

I have an AMD Athlon X2 processor, nvidia EN9400GT video card, and ASUS M4A77TD motherboard.

This is what the last lines of my /var/log/pm-suspend.log looks like:

```
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Thu Jan 28 12:03:17 EST 2010: performing suspend
Thu Jan 28 13:11:35 EST 2010: Awake.
Thu Jan 28 13:11:35 EST 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: Function not supported
Function not supported
success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume suspend: success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: no
```

---

### Post by fixedd on 2010-01-28
Are we all using the proprietary NVidia drivers perhaps?

---

### Post by freedryk on 2010-01-28
I'm using intel video.  More mysteriously, my laptop suspend began spontaneously working again yesterday.  I did absolutely nothing to fix it.  No idea what that's about.

---

### Post by nardis_Miles1 on 2010-01-29
I'm using a Compaq presqrio V5000 ATI Radeon XPRESS 200M (open ati driver). It also does the Snow White thing. No Prince yet.

---

### Post by Dave Kristol on 2010-01-31
> **Dave Kristol said:**
> I'm experiencing something that may be related.  I've got a Dell Inspiron 1420, also running Karmic, which I recently installed (upgraded, that is).

I've seen these different behaviors when I try to resume from suspend by opening the laptop's lid (apart from normal behavior):

1) I get the login box, but the keyboard and trackpad are dead -- no response.  After maybe a minute, the laptop spontaneously goes back to sleep.  Hitting the Power button usually resumes the laptop successfully, though sometimes it repeats the back-to-sleep behavior.

2) The login box appears briefly, then disappears, leaving just a blinking text cursor in the upper left.  I can close the lid and the laptop sleeps.  When I open the lid, the laptop usually resumes successfully.

A few times, when I tried to resume the laptop after one of the above, it bypassed the login screen altogether and resumed my session.  No password provided.

The suspend/resume seemed reasonably reliable in prior Ubuntu releases.

Nothing stood out as odd when I looked at /var/log/pm-suspend.log, except of course for the suspend that immediately followed the resume.

Dave Kristol

This is follow-up to my own post.

I have lived with this problem now for a couple of weeks, and it seems to have become less severe and frequent.  Suspend is always reliable.  Resume works maybe 90% of the time.  I'm only seeing pathology #1 above now.

I have a hunch, maybe a red herring, that there's a time sequencing problem.  Either something is now waiting long enough, or something is taking too long to suspend, so when I try to resume, the previous suspend sequence continues and completes.  When I press the power button, the laptop wakes up and all is well.

For the record, I also have an Nvidia video controller.

Dave Kristol

Edit:
As luck would have it, after I posted this, I experienced several repeats of the problem.  I'm inclined to agree with those who associate this with battery state:  The problems occurred after I plugged the laptop in again after using it on battery.

The good news is I've always been able to get things working again.  If the laptop spontaneously went to sleep again, hitting the power button resumed it successfully.  On one such occasion, the message "Time limit exceeded" (I think) appeared briefly at the bottom of the login box before the laptop went to sleep again.   If the login screen appeared, but the laptop was unresponsive, closing the lid and opening it again worked.

---

### Post by InfiniteImpulse on 2010-01-31
I've discovered that if I hit the power button I can wake my HP Pavilion dv9700 from suspend, but the screen is really dim, whether or not my power adapter is plugged in. So, I still have to reboot. Right now I've adjusted the power settings to shut off the screen when the laptop is closed, but it still runs for some time, and being a large media laptop is consumes more power than I'd like.

Sorry if I don't know the correct technical jargon, I'm just trying to give as much info on the problem as possible. I'm a Linux newbie, still hoping this problem is fixed so that I can wipe the Vista partition off of my system!

Like Dave my laptop has a Nvidia video controller.

Edit: Yes I am using the proprietary Nvidia drivers, it's the only way that I can stream video to my TV. As I mentioned it's a media laptop.

---

### Post by SaintDanBert on 2010-02-04
> **freedryk said:**
> I've got it, too.  Lenovo x61t, pm-suspend.log shows normal suspend sequence, but my suspend light never stops blinking--typically it blinks for 3 seconds or so while suspending, but now it just keeps on blinking.  
...
I can't break out of the suspend sequence either--when I open the lid, the laptop just keeps blinking.

My Lenovo X61-tablet running Karmic behaves mostly the same, but
[list]
[*]pm-suspend.log is empty
[*]can only "start running" at the blinking suspend light (new moon LED) by using hard power cycle.
[*]same behavior whether I ask for "sleep" or "hibernate"
[/list]

With Karmic doing everything thing through [highlight]event processing[/highlight] like **upstart**, **acpid**, and **udev** ... AND ... with the huge volume of available documentation on what is going on and how to use and diagnose all of this (cough, cough, wink, wink) ... I'm at a total loss to help diagnose any of this.

Very Frustrated,
~~~ 0;-/ Dan

---

### Post by saif_held on 2010-02-04
Same here guys, I've MSI Laptop and the machine won't wake from suspend or hibernate.

The power button's a LED circle around that would blink during the suspend but the moment I hit any key to wake it, I would hear the hard disk spins but then the the spinning disappears and I must perform a forced-hard-shutdown. 

P.S. I also use Karmic..this seriously bugs I hope it gets fixed soon because that's the only problem I face with my machine.

---

### Post by Admiral_Payne on 2010-02-04
I've had that problem on this machine until I've upgraded my video drivers. After I installed proprietary driver, the problem magically disappeared :s

I still have the problem with another machine. Strangely that one doesn't wake up from suspend, but it does wake up after hibernation. On this machine it's the other way around!

What graphics drivers are you guys using?

I'm using ATI/AMD proprietary FGLRX graphics driver here; OpenGL 
Vendor        : ATI Technologies Inc.
Renderer        : ATI Radeon HD 3400 Series
Version        : 2.1.9016
Direct Rendering        : Yes

Other machine, OpenGL
Vendor        : Mesa Project
Renderer        : Software Rasterizer
Version        : 2.1 Mesa 7.6
Direct Rendering        : Yes

---

### Post by KristofferAG on 2010-02-04
I'm having a similar issue too. I don't get a blinking cursor or anything like that. It just goes to "Waking up, please wait" with the Ubuntu logo, and it never changes. I'm running an Acer Aspire 5930G.

---

### Post by nardis_Miles1 on 2010-02-04
So, this is a really dumb cludge, but it makes my laptop truly workable. I found this in the mail-list ubuntu-user

Under system-preferences-power management, for both AC power and battery power, (both are tabs) change the setting under *when laptop lid is closed* to *Blank screen*, and use Never when asked when to put your laptop to sleep. I've lost the advantage of battery saving under hybernate or sleep, but at least I can close my lid without losing my session.

---

### Post by shawnhcorey on 2010-02-04
> **nardis_Miles1 said:**
> So, this is a really dumb cludge, but it makes my laptop truly workable. I found this in the mail-list ubuntu-user

Under system-preferences-power management, for both AC power and battery power, (both are tabs) change the setting under *when laptop lid is closed* to *Blank screen*, and use Never when asked when to put your laptop to sleep. I've lost the advantage of battery saving under hybernate or sleep, but at least I can close my lid without losing my session.

The problem with this is that some laptops get too hot when their lid is closed unless the CPU is halted.

A better solution is to simply choose suspend or hibernate from the Quit menu.

---

### Post by KristofferAG on 2010-02-05
> **shawnhcorey said:**
> The problem with this is that some laptops get too hot when their lid is closed unless the CPU is halted.

A better solution is to simply choose suspend or hibernate from the Quit menu.

My laptop gets just way too hot if I do that.

Problem is, if I suspend or hibernate, it'll never wake up again. It annoys me.

---

### Post by shawnhcorey on 2010-02-05
> **KristofferAG said:**
> My laptop gets just way too hot if I do that.

Problem is, if I suspend or hibernate, it'll never wake up again. It annoys me.

I have a PowerBook G4, affectionately known as a ball burner. It gets very hot.  :)

The first time I suspend after a boot, the computer wakes up (I can hear the disk running) but it has a blank screen.  If I kill X Window (Ctrl+Alt+Backspace, or on my machine, Ctrl+Alt+Shift+Delete), it will restart and display the unlock screen prompt.  But it can take several minutes to restart; some patience is required.  After which, it comes up with the unlock screen when I awaken it.  At least so far (knock wood).

---

### Post by geodanny on 2010-02-10
Dave Kristol described my problems to a tee. I have a Dell Latitude D620 running a clean install of Karmic 9.10. It has the default linux graphics driver installed with the standard intel graphics card Dell put in the laptop. I'm not sure it is battery state as I get these problems whether I'm plugged in or not. 

The worst happens when it wakes up but does not give the login prompt. I can move the mouse but there is no response when clicking anything. The only button that works is the power button, which gives the shutdown prompt. 60 seconds later it reboots. That has happened twice today.

In case it helps, here are are logs when I tail /var/log/pm-suspend.log  These are taken right after one spell when I wake the computer from 'suspend,' the login prompt comes up but, before I type anything, the computer goes back to sleep. It was in suspend mode for about an hour, from 13:22 until 14:19. 

```
Thu Feb 11 13:22:35 PST 2010: performing suspend
Thu Feb 11 14:19:02 PST 2010: Awake.
Thu Feb 11 14:19:02 PST 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: Returned exit code 1.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume suspend: success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
/etc/pm/sleep.d/10_grub-common resume suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.
Initial commandline parameters: 
Thu Feb 11 14:19:04 PST 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: Adding quirks from HAL: --quirk-vbe-post --quirk-vbemode-restore 
success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux dell-pickle 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
aes_i586                8124  0 
aes_generic            27484  1 aes_i586
hidp                   14268  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
arc4                    1660  2 
ecb                     2524  2 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwl3945                77372  0 
pcmcia                 36808  0 
snd_timer              22276  2 snd_pcm,snd_seq
iwlcore               112796  1 iwl3945
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              181140  2 iwl3945,iwlcore
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class               4096  2 iwl3945,iwlcore
soundcore               7264  1 snd
yenta_socket           24296  1 
iptable_filter          3100  0 
joydev                 10240  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
rsrc_nonstatic         11644  1 yenta_socket
cfg80211               93052  3 iwl3945,iwlcore,mac80211
dell_wmi                2564  0 
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
dell_laptop             8128  0 
dcdbas                  7292  1 dell_laptop
lp                      8964  0 
btusb                  11856  2 
psmouse                56500  0 
serio_raw               5280  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221320  3 
tg3                   109600  0 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
             total       used       free     shared    buffers     cached
Mem:       1016972     967844      49128          0     118184     426372
-/+ buffers/cache:     423288     593684
Swap:       979956       7540     972416
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/etc/pm/sleep.d/10_grub-common suspend suspend: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Thu Feb 11 14:19:05 PST 2010: performing suspend
Thu Feb 11 14:19:17 PST 2010: Awake.
Thu Feb 11 14:19:17 PST 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: Returned exit code 1.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume suspend: success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
/etc/pm/sleep.d/10_grub-common resume suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.

```

Programs open at the time were Firefox and OpenOffice.

---

### Post by Dave Kristol on 2010-02-15
More confusing data points:

My laptop spent the day on battery.  When I lifted the lid to resume, I got the (now) familiar unresponsive login panel.  I closed the lid and opened it again.  Usually I can then log in, but this time the login panel was still unresponsive.  I plugged the laptop in (panel still unresponsive), closed the lid, and opened it again.  This time the login panel responded and I could log in.

Extrapolating from other posts here, it appears that the charging state of the laptop somehow has a bearing on the malady, though I can't figure out what exactly.

Dave Kristol

---

### Post by Len Tyree on 2010-02-16
Samo-Samo.
I am running a desktop of various (not dubious) parts.  When I go into hibernate or suspend, it will not pull itself out when prompted.
Even when I re-boot, it will not come back properly.
I have to shut the computer down completly and then open (start) it up again??  Who is doing what to whom in the maint shop??
I think someone put inb a fix, but did not take everything into consideration, and I am sure there are a lot of things to consider when putting in a fix.

Amyone having any ideas, please share them.
Thank you, Len Tyree.

---

### Post by qwerty2009 on 2010-02-16
my laptop suspended about 4 months ago and it completely broke my laptop cant start it up at all no bios or nothing just a battery charging led lol

---

### Post by Len Tyree on 2010-02-16
Samo-Samo..  Won't come back from either suspend or hibernate settings.

Even when I reboot, will not return; have to shut down completely then restart??

I am running a desktop of dubious origin, but runs great except for a few glitches like this.  And it looks like I am not alone.  

Anyway, any help would be appreciated.

Thank you, Len Tyree.

---

### Post by Admiral_Payne on 2010-02-16
I got Hibernation working by adding more swap memory. I've got 8GB RAM and had ~6GB swap. The idea is that your RAM is more or less copied into swap, so it helps to have swap > RAM.

I followed all the steps in the [article on linux.com about increasing swap memory](http://www.linux.com/archive/feature/113956), and now I've got hibernation working properly.
The only problem I have now is that after I let it wake up, it stays stuck on screensaver :) So I can move the mouse and type in my password and ****, but it keeps displaying screensaver as an overlay. After logging in with password everything goes back to normal

Hope this is of any help.

---

### Post by SaintDanBert on 2010-02-16
> **Admiral_Payne said:**
> 
...
I followed all the steps in the [article on linux.com about increasing swap memory](http://www.linux.com/archive/feature/113956), and now I've got hibernation working properly.
...

Can the HIBERNATE program configuration be set to write the data to some file other than swap space? I have 4GB ram and only 2GB of swap **file** not partition. Are you saying that I need a swap file that is the size of RAM or slightly larger?

Some issues:
1. Which program implements HIBERNATE (aka, suspend-to-disk)? Which program implements SLEEP (aka, suspend-to-ram)?
2. Where is desktop configuration that tells GNOME to run the above programs?

There is the panel button where I can select Shutdown, Restart, Sleep, Hibernate. Where is the panel configuration that says, "when I select *Hibernate* it runs a specific program?

Armed with the program, I can find its specific files and configuration -- even if I must read the code.


~~~ 0;-Dan

---

### Post by lavinog on 2010-02-17
The OP in this thread is having an issue with the open source ATI drivers.
Chances are, if your issue was due to having 8g of memory, it is likely that you are not using the open source ati drivers currently.

---

### Post by pastalavista on 2010-02-17
I have the same video_chip and had the same problem as you until I edited /etc/default/acpi-support  and I enabled (uncommented) a suspend option called RADEON_LIGHT and commented out #use DPMS=true. I also increased my swap partition because I added more RAM recently. It wakes up "most" of the time now. I always make sure and save work before I suspend though, just in case.

---

### Post by Len Tyree on 2010-02-17
I am having the same problem with my desktop system.  It will not wake up from the suspend or from the hibernate function.  Even when I reboot, it still stays down.  I have to shut the system down completely, then restart it.  Quite bothersom.
So I don't use either the suspend or hibernate functions.  

Len Tyree.

---

### Post by Admiral_Payne on 2010-02-17
> **SaintDanBert said:**
> Can the HIBERNATE program configuration be set to write the data to some file other than swap space? I have 4GB ram and only 2GB of swap **file** not partition. Are you saying that I need a swap file that is the size of RAM or slightly larger?
I've no idea. The way I see it you just fool the system into thinking it has more swap space. Whether or not it's completely written into a swap partition, file or both, is irrelevant. As long as it works :-) I've got 8 GB RAM, had ~6 GB swap partition and added a 5GB swap file.

> **lavinog said:**
> The OP in this thread is having an issue with the open source ATI drivers.
Chances are, if your issue was due to having 8g of memory, it is likely that you are not using the open source ati drivers currently.
I had this bug with both the proprietary drivers and standard drivers (also ATI). Though it appeared to swap from bug in hibernation to bug in suspend mode (I can't suspend properly now)... Not sure if it's related to drivers or something similar, but this was the fix for hibernate.

---

### Post by Len Tyree on 2010-02-19
> **Len Tyree said:**
> I am having the same problem with my desktop system.  It will not wake up from the suspend or from the hibernate function.  Even when I reboot, it still stays down.  I have to shut the system down completely, then restart it.  Quite bothersom.
So I don't use either the suspend or hibernate functions.  

Len Tyree.

xxxxxxxxxxx

---

### Post by lavinog on 2010-02-19
> **qwerty2009 said:**
> my laptop suspended about 4 months ago and it completely broke my laptop cant start it up at all no bios or nothing just a battery charging led lol

Did you try unplugging and pulling the battery out?

---

### Post by tnc on 2010-02-20
To add to the list of machines with the prob:

Old Dell workstation 350 2600 512 Ram.  

Suspend worked with the fresh install of 9.10.  I then installed a nVidia Geforce4 MX 440 gpu.  Karmic saw the need for nvidia drivers which I installed via the hardware drives thingy.  Now suspend brings up black screen on wake and I have to do a hard shutdown to get back to desktop.

So not limited to laptops.  I have not looked into the problem yet.

Tim

---

### Post by Admiral_Payne on 2010-02-20
> **tnc said:**
> Suspend worked with the fresh install of 9.10.  I then installed a nVidia Geforce4 MX 440 gpu.  Karmic saw the need for nvidia drivers which I installed via the hardware drives thingy.  Now suspend brings up black screen on wake and I have to do a hard shutdown to get back to desktop.
But what happens when you uninstall the proprietary drivers?

---

### Post by Byb on 2010-02-20
Similar problem here on a Desktop MB DFI AD73Pro + 3GB RAM (hibernation works) + nVidia AGP MX4000 + HD ATA maxtor on master IDE 0 (/root /tmp) + VIA VT6421 SATA raid adapter (RAID unused) with  HD SATA samsung 320GB (/var /home /srv /swap) and SATA Pioneer DVR215.
On resume, long (1s is long) beep in speakers (embeded audio chip) then the PC is frozen (even the NumLock)
Bios set to S3 (STR)
Any idea please?

---

### Post by Dave Kristol on 2010-02-21
> **pastalavista said:**
> I have the same video_chip and had the same problem as you until I edited /etc/default/acpi-support  and I enabled (uncommented) a suspend option called RADEON_LIGHT and commented out #use DPMS=true. I also increased my swap partition because I added more RAM recently. It wakes up "most" of the time now. I always make sure and save work before I suspend though, just in case.

Ahh, thank you for reminding me of /etc/default/acpi-support.  I compared my current (Karmic) version to the one I had been using with Intrepid/Jaunty.  I had added back a number of lines I had previously been using.  The comparison showed the new setting SUSPEND_METHODS.  The file says:

# Please specify a space separated list of options. The recommended value is
# "dbus pm-utils"

But my file said:

SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"

I changed the value to the recommended one, and so far I haven't had a recurrence of the failure to resume properly, though it's been less than a day.

Dave Kristol

<sigh>  2010-2-22:  No joy.  This did not really produce any change.  -- DK

---

### Post by tnc on 2010-02-22
> **Admiral_Payne said:**
> But what happens when you uninstall the proprietary drivers?

Good question! :)
Uninstall brings back normal operation.  Reinstall brings back same problem.  

It would seem, in my humble opinion, that the problem is the same in all situations: proprietary driver prevents wake function from working correctly....?

If so, then where would a person look to when searching for a solution?

Tim

---

### Post by Admiral_Payne on 2010-02-22
> **tnc said:**
> It would seem, in my humble opinion, that the problem is the same in all situations: proprietary driver prevents wake function from working correctly....?
Well..., I've got the same problem on a different computer. But that one doesn't have the proprietary driver installed (there isn't one, grrr ATI) :(

But it could of course be possible that there's something wrong with a specific proprietary driver.. I think that most Nvidia cards have the same driver, right? Perhaps it's just a bug in their driver ;)

---

### Post by lavinog on 2010-02-22
> **tnc said:**
> 
If so, then where would a person look to when searching for a solution?


What is wrong with not using the proprietary driver?

---

### Post by Admiral_Payne on 2010-02-23
> **lavinog said:**
> What is wrong with not using the proprietary driver?
Playing (graphically advanced) games like WoW usually have a significant drop in FPS when using the open source driver :(

---

### Post by DrDaveyAtoms on 2010-02-23
I am now experiencing this problem. I did not have this issue until yesterday when I activated the proprietary driver called "AMD/ATI proprietary FGLRX graphics driver". I need this in order to visualise my work. 

Is this a known bug? Are people (much more in the know than I am) looking into this?

---

### Post by Cavsfan on 2010-03-01
I have a desktop PC with Nvidia drivers. 
I have always had this problem since doing a fresh install of Karmic Koala 9.10, but everything 
worked fine in Jaunty Jackalope 9.04. It went to sleep and woke up just fine.

Now, the display just turns off, but the PC never goes to sleep. I do not see a "sleep" option in the drop down list, 
so I clicked hibernate and it did hibernate, but it would not wake up without touching the power button, which 
booted the system. Then when it started coming up, I could see "resuming system" displayed.

I too am anxious for this to be fixed as I like my PC to sleep and the fans to turn off when not in use.
And I think this happens on laptops and pcs both regardless of video driver.

---

### Post by pastalavista on 2010-03-01
I pretty much ruined my Karmic system trying to fix this bug. So I tried 10.04 Lucid (daily build - alpha) and all these problems were gone. It has a few new problems, of course, due to some new features but my Acer/AMD/ATI laptop basically works like it used to again. The bugs are really nothing too bad for me. Gwibber doesn't work :D It'll be interesting to see what that is when they fix it.

---

### Post by Cavsfan on 2010-03-02
> **pastalavista said:**
> I pretty much ruined my Karmic system trying to fix this bug. So I tried 10.04 Lucid (daily build - alpha) and all these problems were gone. It has a few new problems, of course, due to some new features but my Acer/AMD/ATI laptop basically works like it used to again. The bugs are really nothing too bad for me. Gwibber doesn't work :D It'll be interesting to see what that is when they fix it.

Did you do a fresh install or upgrade? Gwibber huh? Sounds interesting. :D

---

### Post by pastalavista on 2010-03-02
> **Cavsfan said:**
> Did you do a fresh install or upgrade? Gwibber huh? Sounds interesting. :D

Fresh install without reformatting /home. I've been enjoying testing and even though the bugs are annoying, it's been a learning experience, not terrible at all. I tested pretty extensively with the live CD (on USB flash) before installing.

---

### Post by StuartN on 2010-03-02
> **joe-the-indian said:**
> I've got a Toshiba Satellite l30-113 laptop, when I send it to sleep mode it won't wake up afterwards - just showing blinking cursor.

I notice that the OP has filesystem corruption, remounted readonly at the boot listed in the dmesg log (extract below). The events leading up to the filesystem error are not available.

There are some other threads and bug reports that have filesystem errors with varied symptoms, e.g. [http://www.backports.ubuntuforums.org/showthread.php?t=1309015](http://www.backports.ubuntuforums.org/showthread.php?t=1309015) and [http://www.backports.ubuntuforums.org/showthread.php?t=1380689](http://www.backports.ubuntuforums.org/showthread.php?t=1380689)

From the OP's dmesg:
```
[    3.703287] PM: Resume from disk failed.
[    3.713283] EXT3-fs: INFO: recovery required on readonly filesystem.
[    3.713287] EXT3-fs: write access will be enabled during recovery.
[    5.217034] kjournald starting.  Commit interval 5 seconds
[    5.217057] EXT3-fs: sda7: orphan cleanup on readonly fs
[    5.217064] ext3_orphan_cleanup: deleting unreferenced inode 441721
[    5.217122] ext3_orphan_cleanup: deleting unreferenced inode 441720
[    5.217131] ext3_orphan_cleanup: deleting unreferenced inode 441719
[    5.217139] ext3_orphan_cleanup: deleting unreferenced inode 441718
[    5.217147] ext3_orphan_cleanup: deleting unreferenced inode 441717
[    5.217154] ext3_orphan_cleanup: deleting unreferenced inode 441716
[    5.217164] ext3_orphan_cleanup: deleting unreferenced inode 258395
[    5.217181] ext3_orphan_cleanup: deleting unreferenced inode 256978
[    5.217189] ext3_orphan_cleanup: deleting unreferenced inode 441713
[    5.217197] ext3_orphan_cleanup: deleting unreferenced inode 441712
[    5.217203] ext3_orphan_cleanup: deleting unreferenced inode 441711
[    5.217211] ext3_orphan_cleanup: deleting unreferenced inode 441710
[    5.217218] ext3_orphan_cleanup: deleting unreferenced inode 441707
[    5.217226] ext3_orphan_cleanup: deleting unreferenced inode 441589
[    5.217233] ext3_orphan_cleanup: deleting unreferenced inode 441519
[    5.217239] ext3_orphan_cleanup: deleting unreferenced inode 441518
[    5.217244] ext3_orphan_cleanup: deleting unreferenced inode 441517
[    5.217250] ext3_orphan_cleanup: deleting unreferenced inode 441516
[    5.217255] ext3_orphan_cleanup: deleting unreferenced inode 441515
[    5.217260] EXT3-fs: sda7: 19 orphan inodes deleted
[    5.217263] EXT3-fs: recovery complete.
[    5.273250] EXT3-fs: mounted filesystem with writeback data mode.
```

---

### Post by Admiral_Payne on 2010-03-03
> **Cavsfan said:**
> so I clicked hibernate and it did hibernate, but it would not wake up without touching the power button, which booted the system. Then when it started coming up, I could see "resuming system" displayed.
Isn't that what it's supposed to do when hibernating? :-)

Anyway, hibernate works for me too. When putting it to suspend, it goes 'off' normally. Upon turning it back on, everything goes on (fans, hd, cdrom etc) apart from the graphics card. The screen stays black and the system does not respond to anything. The only way to get it back up is by resetting...

---

### Post by Drew. on 2010-03-03
This is usually an easy fix. Often the issue (when the screen is completely blank but power comes back) is that the backlight isn't on. When Ubuntu goes into suspend/hibernate, it turns off the LCD light. But, when it comes back up, it often doesn't turn back on. If you look really closely at your screen, you might see some contrasting colors in there. Just hit the shortcut to adjust your screen brightness (FN+F4 or whatever it is on your computer, up or down doesn't matter) and it will reactivate the backlight.
 
Hope this helps.
 
Drew
drewbrown.org

---

### Post by Admiral_Payne on 2010-03-04
> **Drew. said:**
> Often the issue (when the screen is completely blank but power comes back) is that the backlight isn't on.
I've got it on 2 desktops, the system doesn't respond to keyboard or mouse either. It appears like it just doesn't fully wake up, as if it crashes when starting the video card.

---

### Post by aqk on 2010-03-04
Yep- just to add my voice-
  I have a  E-machines DESKTOP with 9.10 up to date (except for latest 80 meg of OO 3.2) 
And if I walk away for 30 min or so, it goes to sleep, and does not wake up.
The keyboard is dead, and my only recourse is to press the OFF button for 5 seconds, to turn the machine off.  
Grrrr....

---

### Post by aqk on 2010-03-04
> **Drew. said:**
> This is usually an easy fix. Often the issue (when the screen is completely blank but power comes back) is that the backlight isn't on. When Ubuntu goes into suspend/hibernate, it turns off the LCD light. But, when it comes back up, it often doesn't turn back on. If you look really closely at your screen, you might see some contrasting colors in there. Just hit the shortcut to adjust your screen brightness (FN+F4 or whatever it is on your computer, up or down doesn't matter) and it will reactivate the backlight.
 
Hope this helps.
 
Drew
drewbrown.org
Not sure who you are replying to, but I have an old desktop with a CRT monitor.
When it goes to sleep, it is pretty much dead. If I power off/on the monitor, it shows the monitors screensaver i.e. "NO CONNECTION TO COMPUTER", indicating the video card is dead.
As well, the keybaord is dead :  "He's DEAD, Jim!"

---

### Post by aqk on 2010-03-04
An observation- 
As a test, I reduced the "Put the display to sleep"  from 30 minutes to ONE minute.
  I let it go to sleep, and walked away for 20 minutes.
When I came back, the mouse woke it up satisfactorily.
I'll try this again, changing the time back to 30 min again.

Note that my "Put the computer to sleep" is set to  NEVER.
Is it possible the act of changing the Power-management (the first time I have done it since applying all updates) has somehow fixed the problem?

  Most mysterious....

---

### Post by SaintDanBert on 2010-03-06
[highlight]I discovered what is the trouble here.[/highlight]

Karmic uses GRUB-v2 during system boot. Apparently, the right "restart" and "recovery" options (*my words*) are not added to the several system boot stanzas in the new style grub configuration. Try as I might, I do not find how to alter the grub configuration so that
[list=1]
[*]the correct options appear on the linux boot stanzas
[*]these options propagate any time there is a kernel image update
[/list]

Under Jaunty (v9.04) there is *resume=swap* as an option on the **kernel** entry to **/boot/grub/menu.lst**. Even Jaunty does foul things. If you do not install with a swap partition, the resume option does not get written.

Cheers,
~~~ 0;-/

---

### Post by StuartN on 2010-03-06
> **SaintDanBert said:**
> Try as I might, I do not find how to alter the grub configuration

You would edit /etc/default/grub. Change the line saying **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** to modify the default bootup or the line saying **GRUB_CMDLINE_LINUX=""** to propagate to all boot options.

Quite honestly I do not see that this can be the problem - I have several other machines that work perfectly well with Karmic, and the reported problems seem to affect laptops with SB600 Southbridge hardware.

---

### Post by Dave Kristol on 2010-03-07
I have more information that, I think, points in an interesting direction, though I don't know what to do about it.

I had another failure just now.  Opened the lid, got login box, dead keyboard and mouse.  However, I was able to login (ssh) from another machine, so the machine is definitely up.  I closed the lid again after awhile, then opened it again.  I got the login box again, but it said "time expired", and the screen went dark.  I hit the Shift key, the login box reappeared, and I could log in.

I looked in /var/log/auth.log and found the following:

This appeared, repeated four times:
Mar  7 17:03:55 dmklap3 su[31482]: Successful su for dmk by root
Mar  7 17:03:55 dmklap3 su[31482]: + ??? root:dmk
Mar  7 17:03:55 dmklap3 su[31482]: pam_unix(su:session): session opened for user dmk by (uid=0)
Mar  7 17:03:55 dmklap3 su[31482]: pam_unix(su:session): session closed for user dmk

followed by:
Mar  7 17:04:59 dmklap3 gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): conversation failed
Mar  7 17:04:59 dmklap3 gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): auth could not identify password for [dmk]

What was interesting is that of course I was never able to enter a password.

On the second open-lid event I see:
Mar  7 17:13:03 dmklap3 gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): conversation failed
Mar  7 17:13:03 dmklap3 gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): auth could not identify password for [dmk]
Mar  7 17:13:09 dmklap3 gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring

That is, the first two lines match up with the "Time expired" message.  The last line matches my successful login.  The same line appears multiple other times in the log, presumably on other successful logs.

My inference:  There's some kind of bad interaction (on my system) between resume and gnome-screensaver and its auth function.

Dave Kristol

---

### Post by StuartN on 2010-03-09
> **Dave Kristol said:**
> However, I was able to login (ssh) from another machine, so the machine is definitely up.

If it happens again, it might be worth checking kern.log and dmesg to see is there is anything informative about why it is hanging, like perhaps the filesystem switching to readonly.

In another thread [http://ubuntuforums.org/showpost.php?p=8936446&postcount=170](http://ubuntuforums.org/showpost.php?p=8936446&postcount=170) a post says that Linux kernel 2.6.33 solves the problem in beta Ubuntu 10.04.

---

### Post by Dave Kristol on 2010-03-09
> **StuartN said:**
> If it happens again, it might be worth checking kern.log and dmesg to see is there is anything informative about why it is hanging, like perhaps the filesystem switching to readonly.

In another thread [http://ubuntuforums.org/showpost.php?p=8936446&postcount=170](http://ubuntuforums.org/showpost.php?p=8936446&postcount=170) a post says that Linux kernel 2.6.33 solves the problem in beta Ubuntu 10.04.

At the time, I did look at all the other logs to see whether there was anything useful, but there wasn't.  For a little while I thought maybe the latest karmic kernel, 2.6.31-20, had solved the problem, but it didn't.  I can't quite put my finger on the precise connection, but I'm convinced it has something to do with whether the battery is charging or discharging.

Dave Kristol

---

### Post by StuartN on 2010-03-13
> **SaintDanBert said:**
> Under Jaunty (v9.04) there is *resume=swap* as an option on the **kernel** entry to **/boot/grub/menu.lst**. Even Jaunty does foul things. If you do not install with a swap partition, the resume option does not get written.

There is a related issue marked as solved in another thread [http://ubuntuforums.org/showthread.php?t=1306009](http://ubuntuforums.org/showthread.php?t=1306009), where the visible symptoms are very similar to this thread. The thread suggests that reverting to device names in fstab is more stable than using UUIDs, so you would **sudo gedit /etc/fstab** and comment out and replace the UUID lines like this:

```
# / was on /dev/sda4 during installation
UUID=795bc2fa-4700-46df-9a33-a19763ad3e88 /               ext3    errors=remount-ro 0       1
```
becomes:
```
# UUID=795bc2fa-4700-46df-9a33-a19763ad3e88 /               ext3    errors=remount-ro 0       1
/dev/sda4       /               ext3    errors=remount-ro 0       1
```

I have not lost any data with this issue, but it is infuriating to have the occasional system freeze and the frequent failed resumes.

---

### Post by StuartN on 2010-03-16
> **StuartN said:**
> The thread suggests that reverting to device names in fstab is more stable than using UUIDs

This did not improve things. There is a new version of Mountall in Karmic Proposed with this bug report attached [https://launchpad.net/bugs/456806](https://launchpad.net/bugs/456806) so I am trying that next.

---

### Post by Byb on 2010-03-23
> **Byb said:**
> Similar problem here on a Desktop MB DFI AD73Pro + 3GB RAM (hibernation works) + nVidia AGP MX4000 + HD ATA maxtor on master IDE 0 (/root /tmp) + VIA VT6421 SATA raid adapter (RAID unused) with  HD SATA samsung 320GB (/var /home /srv /swap) and SATA Pioneer DVR215.
On resume, long (1s is long) beep in speakers (embeded audio chip) then the PC is frozen (even the NumLock)
Bios set to S3 (STR)
Any idea please?
I post here the result of a test I did yesterday: I tested a liveCD 9.10 and it works. Could someone guide me to check for differences between the 2 modes that could be involved in the issue? Please ask me to post any log that could help.
I have a feeling about either the video or the addon sata controler. Before the test I reset the bios power management features to safe settings (I only enabled S3). The test is OK, not the true installation whose master disk is attached to the addon controler.
Thank you

---

### Post by Robbyx on 2010-03-23
I am using Nvdia prop drivers on a desktop. I have it set to go to sleep after 30 mins. Until today it worked ok. Now after an update I am finding that usb mouse is not working on waking from sleep and screen is blank.

---

### Post by Alan_Ross on 2010-03-24
> **tnc said:**
> To add to the list of machines with the prob:

Old Dell workstation 350 2600 512 Ram.  

Suspend worked with the fresh install of 9.10.  I then installed a nVidia Geforce4 MX 440 gpu.  Karmic saw the need for nvidia drivers which I installed via the hardware drives thingy.  Now suspend brings up black screen on wake and I have to do a hard shutdown to get back to desktop.

So not limited to laptops.  I have not looked into the problem yet.

Tim

Yes. Pretty much the same, with the only exception of the machine: a Compaq Evo d310 with 768 MB RAM + 2x40 GB HDDs. Windows XPP on the first drive, SuSE 9.1 on the second, until yesterday, when I've decided it was time to give a refresh to this oldie, and to give a try to Ubuntu. ...er... can I humbly add that I'm beginning to think I should have left everything untouched? :rolleyes: 

To make things even worse, however, today, after a couple of days spent in tinkering around to understand when or where did the issue get in, and after one more attempt with the suspend/hibernate thing, at the return,  in trying to wake up the machine, the Linux drive was completely unreachable. Pffft!! Evaporated...

Now, any attempt at regaining its control, made with gParted or whatever else, doesn't work...  :roll:

---

### Post by Robbyx on 2010-03-24
I have turned off the sleep mode. It is too risky. The hard reset causes damage generally.

---

### Post by nightwolf2k5 on 2010-03-24
if it is a laptop, try this..

After it brings up the blank screen, close the lid of the laptop so that it goes to the hibernate (i think) mode.
Open the lid and restart.

---

### Post by Alan_Ross on 2010-03-24
Update to my previous.

Now everything works again. I've nonetheless had to 1) do check the two drives via the BIOS; and 2) after having ascertained that everything was still there and working (thus, contrary to what I initially suspected, it seems that the partition table hasn't been corrupted at all), reinstall Ubuntu from scratch.

A couple of other notes. 

[LIST=1]
[*]The first time, this suspend/hibernate issue - I suspect - has been started from the installation of the nVidia drivers suggested by the system upgrade tool. It's no more than a suspect...
[*]This time, the whole mess seems to have been triggered by the **Language Support** update/installation, again, an update performed as suggested by the system.
[/LIST]

---

### Post by Admiral_Payne on 2010-03-25
> **Robbyx said:**
> I have turned off the sleep mode. It is too risky. The hard reset causes damage generally.
Where did you turn off the sleep mode? :-)

---

### Post by Robbyx on 2010-03-25
> **Admiral_Payne said:**
> Where did you turn off the sleep mode? :-)

In system there is a power management option.

---

### Post by Byb on 2010-03-26
Cool ! Back to the good old Windows NT4

---

### Post by Byb on 2010-03-26
Gasp :( nothing there to disable S3 in 9.10 French

---

### Post by Admiral_Payne on 2010-03-26
> **Robbyx said:**
> In system there is a power management option.
Yes of course, I've got that one turned off. I thought you had removed/disabled the sleep option completely :-)

---

### Post by Dave Kristol on 2010-04-07
This may be a red herring, but I've noticed, as the weather here (NJ) gets warmer, I have fewer suspend/resume problems.  I don't know why that might make a difference, but if my laptop is warm, resume seems to work reliably.

Dave Kristol

---

### Post by cmptch on 2010-04-17
I had problems with resuming until I disabled "Suspend" action in the keyboard shortcut GUI.

Perhaps it's trying to suspend and hibernate at the same time?  I fixed it by accident, interestingly.  I was trying to set the suspend key to eject, but it suspended anyway.

For the GUI>>>

System>>Preferences>>Keyboard Shortcuts

Then under "Desktop" You'll find the "Suspend" action.

I have to hit the I/0 key to get it back, but it comes back. XD

Edit:

Under:

System>>Preferences>>Power Management::General

You'll find that it can be set to hibernate or suspend, but not disabled.  This is where the conflict is, methinks.

---

### Post by Robbyx on 2010-04-17
> **cmptch said:**
> I had problems with resuming until I disabled "Suspend" action in the keyboard shortcut GUI.

Perhaps it's trying to suspend and hibernate at the same time?  I fixed it by accident, interestingly.  I was trying to set the suspend key to eject, but it suspended anyway.

For the GUI>>>

System>>Preferences>>Keyboard Shortcuts

Then under "Desktop" You'll find the "Suspend" action.

I have to hit the I/0 key to get it back, but it comes back. XD

I am not clear, does what you suggest prevent "suspend" and that I should go for hibernate in future?

What is the i/o key?

---

### Post by cmptch on 2010-04-17
> **Robbyx said:**
> I am not clear, does what you suggest prevent "suspend" and that I should go for hibernate in future?

What is the i/o key?


No.  It doesn't prevent suspend.  By removing the hotkey in "keyboard shortcuts", it clears the conflict it has with the setting in "power management".

I/0 is the power button.

It's kind of a silly conflict; one that should have been caught a long time ago.


I'm currently looking up the resume on keyboard for ubuntu, because my motherboard has a wake on Kb/M setting, and its on.


*Sometimes the answers always the simplest.*

---

### Post by Robbyx on 2010-04-17
> **cmptch said:**
> No.  It doesn't prevent suspend.  By removing the hotkey in "keyboard shortcuts", it clears the conflict it has with the setting in "power management".

When the suspend fails I have found I have had to restart the computer via the power button, and have  damaged open files by crashing the system.  I have the suspend keyboard shortcut already disabled on my machine and so I wonder if your solution will work for me. I had such problems with turning the power off in order to start the computer that I fear trying it again.

---

### Post by cmptch on 2010-04-17
I don't know if this is a solid solution, but it worked for me.  does it hibernate/suspend when your battery is very low or you close the laptop?  There's plenty of configuration options in the configuration editor:

Open terminal:

sudo gconf-editor

then under

apps___
__gnome-power-manager
_____buttons

is the only way to actually disable/enable sleep actions.  There's more options in "actions" for critical/low battery and UPS, as well as the the buttons do.

another question is if your button is a sleep or hibernate button.  It's usually sleep, but to check, go to the hotkey gui under preferences, select the sleep action, and press the button, it will tell you whether its a sleep or hibernate button..

Just don't leave open windows and files when testing it out and you should be fine. XD

---

