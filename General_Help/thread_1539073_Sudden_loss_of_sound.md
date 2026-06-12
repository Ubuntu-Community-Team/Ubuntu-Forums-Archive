---
title: "Sudden loss of sound"
date: 2010-07-26
forum: General Help
---

### Post by K-cid on 2010-07-26
The day before my sound suddenly stopped working in Ubuntu 10.04 (custom build desktop PC). It is now completly gone and nothing I do makes it comes back.
It is not a hardware related issue as it does work in Windows. 
The only things I did during the previous days is run a few user apps and a software update after getting back from a few weeks of vacation.

I checked all common sound and permission issues (even ran mpg321 with sudo). I also created an alsa report available at [http://www.alsa-project.org/db/?f=727515997b52f206e6a27a47f3c451dc21175c9d](http://www.alsa-project.org/db/?f=727515997b52f206e6a27a47f3c451dc21175c9d) where you can even check my slider settings (all on).

I am puzzled as everything seems ok, but I have no sound.

Can somebody shed a light on this?

Thank you,

K-cid

---

### Post by Junaid Ali on 2010-07-26
If the sound comes back after rebooting you can try this 

sudo alsa force-reload

---

### Post by K-cid on 2010-07-26
The sound is always gone, even when I reboot. The

```
sudo alsa force-reload     
```command does give a lot of warnings though:

```
sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/****/.gvfs
      Output information may be incomplete.
Terminating processes: 9104lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/****/.gvfs
      Output information may be incomplete.
 9270lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/****/.gvfs
      Output information may be incomplete.
 9291lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/****/.gvfs
      Output information may be incomplete.
 9310lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/****/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 9331lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/****/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 9352(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/****/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 9352(pulseaudio). 
Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-seq-midi-event snd-seq snd-pcm-oss snd-mixer-oss snd-ca0106 snd-ac97-codec snd-pcm snd-rawmidi snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-ca0106 snd-ac97-codec snd-pcm snd-rawmidi snd-timer snd-seq-device snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-seq-midi-event snd-seq snd-pcm-oss snd-mixer-oss snd-ca0106 snd-ac97-codec snd-pcm snd-rawmidi snd-timer snd-seq-device snd-page-alloc.


```

---

