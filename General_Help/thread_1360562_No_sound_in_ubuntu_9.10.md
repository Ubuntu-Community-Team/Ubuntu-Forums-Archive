---
title: "No sound in ubuntu 9.10"
date: 2009-12-21
forum: General Help
---

### Post by Nosaj61 on 2009-12-21
Hello,

I have never been able to get sound on my system.. I had ubuntu 9.04 and now ubuntu 9.10, both 64 bit. I have tried a few guides but nothing seems to be working. 

When I try a forced reload with "sudo alsa force-reload" I get this:

```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mole/.gvfs
      Output information may be incomplete.
Terminating processes: 10992lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mole/.gvfs
      Output information may be incomplete.
 23621lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mole/.gvfs
      Output information may be incomplete.
 23621lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mole/.gvfs
      Output information may be incomplete.
 23648lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mole/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 23648lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mole/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 23674(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mole/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 23674(pulseaudio). 
Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-codec-ca0110 snd-hda-codec-nvhdmi snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-codec-ca0110 snd-hda-codec-nvhdmi snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-codec-ca0110 snd-hda-codec-nvhdmi snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-allocFATAL: Error inserting snd_seq_oss (/lib/modules/2.6.31-16-generic/updates/alsa/acore/seq/oss/snd-seq-oss.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_seq_oss (/lib/modules/2.6.31-16-generic/updates/alsa/acore/seq/oss/snd-seq-oss.ko): Unknown symbol in module, or unknown parameter (see dmesg)
 (failed).

```I have no idea what to do.

Thank you,
Nosaj61

---

