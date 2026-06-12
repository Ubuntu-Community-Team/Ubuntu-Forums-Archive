---
title: "Sound Problems.."
date: 2012-03-23
forum: General Help
---

### Post by MeguhNad on 2012-03-23
Hi forum,

I recently installed Xubuntu 11.10 yesterday and it's all been working great. Except for one problem: When I press the mute key on my keyboard, the volume mutes, however when pressed again, the panel shows the sound unmuting but the sound isn't actually unmuted. I used to get around this problem by typing: "amixer set Master unmute" into the terminal. And it used to work, unmute my sproblemsound. Now, however, the terminal is giving me this text after I have entered the above command:

ALSA lib conf.c:1205:(parse_def) lc does ALSA lib conf.c:1205:(parse_def) lc does not exists
ALSA lib conf.c:1685:(snd_config_load1) _toplevel_:3:18:No such file or directory
ALSA lib conf.c:3467:(snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:3326:(snd_config_hooks_call) function snd_config_hook_load returned error: No such file or directory
ALSA lib conf.c:3713:(snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach default error: No such file or directory
not exists
ALSA lib conf.c:1685:(snd_config_load1) _toplevel_:3:18:No such file or directory
ALSA lib conf.c:3467:(snd_config_hook_load) /eproblemstc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:3326:(snd_config_hooks_call) function snd_config_hook_load returned error: No such file or directory
ALSA lib conf.c:3713:(snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach default error: No such file or directory


So I'm stuck with no sound at the minute. Any help is much appreciated.

---

### Post by anaconda on 2012-04-17
Having the same problem in xubuntu 12.04
mute works, but cant get the sound back

The only place I DO get it back is if I log off, and click the speaker thing from the login screen.

(even rebooting doesnt give the sound back)

Why is this thread marked as solved?

---

### Post by anaconda on 2012-04-17
found a working solution here:
[http://ubuntuforums.org/showthread.php?t=1871357&page=2](http://ubuntuforums.org/showthread.php?t=1871357&page=2)

---

