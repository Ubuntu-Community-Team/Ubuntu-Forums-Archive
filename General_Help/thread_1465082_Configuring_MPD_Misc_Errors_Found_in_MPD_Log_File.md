---
title: "Configuring MPD: Misc Errors Found in MPD Log File"
date: 2010-04-29
forum: General Help
---

### Post by dannymichel on 2010-04-29
No idea what's going on here.
MPD used to start the song where i left it, when i re-booted.
here is what is in my MPD log file
```
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
Apr 29 03:54 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "default": No such file or directory
Apr 29 03:54 : player_thread: problems opening audio device while playing "Link to music d/Moloko/2003. Statues/08. The Only Ones.flac"
```
any ideas?

---

