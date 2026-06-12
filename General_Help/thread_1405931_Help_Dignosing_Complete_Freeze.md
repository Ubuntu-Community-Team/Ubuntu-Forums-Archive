---
title: "Help Dignosing Complete Freeze"
date: 2010-02-13
forum: General Help
---

### Post by slibuntu on 2010-02-13
Hi all,

Recently my laptop has developed an annoying habit, every now and then, at completely random times, surfing the net, not doing anything particularly taxing. The display goes dark, and the computer becomes completely unresponsive. AltSysReq and k doesn't kill X, and even the ALT - SYSREQ - REISUB doesn't work either. The lights are on and the fan is spinning but the display is blank and I cannot interface with it at all.

How can I go about figuring out why this happens? Which are the pertinant logs to look through?

I got this from syslog, it seems to have happenened at the same time the PC hung up, though I'm not sure is it a cause, or is it the effect.

> Feb 13 13:44:52 shane-laptop pulseaudio[1654]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Feb 13 13:44:52 shane-laptop pulseaudio[1654]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Feb 13 13:44:52 shane-laptop pulseaudio[1654]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.


How can I figure this out? Thanks for your help.

System Info:
Dell XPS M1330, Ubuntu 9.10, nvidia gfx card

---

### Post by mhgsys on 2010-02-13
> Feb 13 13:44:52 shane-laptop pulseaudio[1654]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
``` and
change the following line;

```
options snd-hda-intel power_save=10 power_save_controller=N
```
to
```
options snd-hda-intel power_save=0 power_save_controller=N
```

reboot;

Btw, It may be handy to also monitor the temperature on your laptop

```
sudo apt-get install computertemp
```

after that right click a panel, click add to panel and select computer temperature monitor.

That way you can monitor the temperature set an alarm etc.



If you don't get any output on the computertemp-sensor, install libsensors4 & lm-sensors as well.
after that run


```
sudo sensors-detect
```

reboot; and try to monitor the temperature again.

---

### Post by slibuntu on 2010-02-13
Thanks for the suggestion, since the problem randomly happens, I'll have to wait and see does your solution help.

As for monitoring temperature, I use conky for that, and keep an eye on it. What temperatures are too high? CPU hovering at 48, GFX card at 60 and HDD at 40, though the HDD does sometimes go as high as 50.

What is the reason for the hang up? And why does the fix mentioned fix it?

---

### Post by mhgsys on 2010-02-13
As for the temperature, those rates seem pretty ok to me. 
Bios will shut down the computer when it reaches something like 80 or 90 degrees I guess depending on the setting.

Anyway; the "fix" will stop your soundcard from going into sleep mode.

I needed to change that line myself as well on my laptop, since my sound completely stopped working at random.

Seeing your error code;>  Feb 13 13:44:52 shane-laptop pulseaudio[1654]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Feb 13 13:44:52 shane-laptop pulseaudio[1654]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Feb 13 13:44:52 shane-laptop pulseaudio[1654]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.

makes me think this is the problem which keeps crashing your laptop.

(if this fix does not work out for you; try commenting out that line;... just put a # in front of it)

---

