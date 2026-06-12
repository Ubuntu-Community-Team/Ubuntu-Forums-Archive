---
title: "Karmic upgrade - No sound after gdm/login"
date: 2010-03-26
forum: General Help
---

### Post by politas on 2010-03-26
I hate to start another "no sound" thread, but none of the others seem to match what happening to me.

I have a desktop machine, fairly basic, which I use as a jukebox. I was running a fairly simnple Jaunty 9.04 installation on it with absolutely no problems.

Recently, I upgraded to 9.10, and ever since then, I have no sound. Now, given that this machine's entire purpose is to play music constantly, I find this to be just a tad annoying.

When I restart the machine, I do hear the drums of the system ready sound, and if I flub my password, I hear the error sound, so gdm is using the sound system successfully, but I get no system sounds or application sound.

The particularly annoying thing is that I can find no symptoms other than the basic lack of sound. The soundcard has been detected and seems to be working:
```
me@juke:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```
```
lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```

I have checked in alsa-mixer, and nothing is muted or turned down

```
&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.20 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: SigmaTel STAC9221 A1                                                   &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00]                                                  &#9474;
&#9474;                                                                              &#9474;
&#9474;         &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;                                      &#9484;&#9472;&#9472;&#9488;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                       Mic In         &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9500;&#9472;&#9472;&#9508;          &#9492;&#9472;&#9472;&#9496;                                      &#9500;&#9472;&#9472;&#9508;         &#9474;
&#9474;         &#9474;OO&#9474;                                                    &#9474;OO&#9474;         &#9474;
&#9474;         &#9492;&#9472;&#9472;&#9496;                                                    &#9492;&#9472;&#9472;&#9496;         &#9474;
&#9474;          100        100<>100                                  100<>100       &#9474;
&#9474;      < Master >       PCM         Line Jac      Mic Jack      Speaker
```  

If I load up pacontrol, I see Rhythmbox in the playback tab, and the level meter shows it playing sound. I also see the level meter working away under the Output Devices tab.

I've tried alsa force-reloads
```
sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/politas/.gvfs
      Output information may be incomplete.
Terminating processes: 2762lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/politas/.gvfs
      Output information may be incomplete.
 2893lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/politas/.gvfs
      Output information may be incomplete.
 2919lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/politas/.gvfs
      Output information may be incomplete.
 2946lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/politas/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 2971lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/politas/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 2997(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/politas/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 2997(pulseaudio). 
Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc.
```

No change whatsoever.

Any ideas for how to fix this?

---

