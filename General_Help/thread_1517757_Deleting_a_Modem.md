---
title: "Deleting a Modem"
date: 2010-06-25
forum: General Help
---

### Post by 2edgesword on 2010-06-25
My sound is not working and I have a suspicion (I've try a lot of other things to no avail) that the systems is attempting to play sound through the modem.
 
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC262 Analog [ALC262 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 1/1
Subdevice #0: subdevice #0
 
How do I delete the modem? I never use it so deleting in doesn't affect functionality for me.

---

### Post by 3Miro on 2010-06-25
I am not sure "deleting" a hardware is possible in Linux. Maybe disabling, but not deleting as in Windows.

Right-click on the sound icon should let you select different input/output audio devices. Also, you can go to terminal (Apps -> Accessories -> Terminal) and type:
```
alsamixer
```
Play with the nettings to make sure you don't just have something muted or volume turned way down.

If this doesn't work, you can try:
```
 sudo alsa force-reload 
```
and see if you get any errors.

---

### Post by 2edgesword on 2010-06-25
Thanks 3Miro. I'll give it a try and report back.

---

### Post by ajgreeny on 2010-06-25
You may need to just disable the modem driver from **System ->Administration ->Hardware Drivers** as there was a known conflict in the past.

It will do no harm, if you don't use the modem, but also disable the item "Check for new hardware drivers" from your startup applications list, or you will continuously be reminded that it is available.

---

### Post by 2edgesword on 2010-06-25
I confirmed the correct sound device was selected in Alsamixer, I disabled the modem driver and ran sudo alsa force-reload and got the following warnings.

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/paul/.gvfs
      Output information may be incomplete.
Terminating processes: 1265lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/paul/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/paul/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/paul/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

Rebooted but still no sound.

---

### Post by Dustin2128 on 2010-06-25
did you check volume levels in alsamixer? I've panicked many times when I lost sound but then noticed that while master was at 100, *speaker* was at 0.

---

### Post by 2edgesword on 2010-06-25
> **Dustin2128 said:**
> did you check volume levels in alsamixer? I've panicked many times when I lost sound but then noticed that while master was at 100, *speaker* was at 0.

Master volume is at 100% but there is no slide labeled "speaker" only "master", "headphone", "pcm","front", "front mic", "front mic boost", "mic", "mic boost", "beep", "CD", "Mono", "caller I", "capture" (three labelled capture) and "off hook". All are unmuted "00" and to the max.,

---

