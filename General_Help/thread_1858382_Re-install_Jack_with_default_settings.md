---
title: "Re-install Jack with default settings"
date: 2011-10-12
forum: General Help
---

### Post by M@s on 2011-10-12
While having some [troubles with LADISH]("http://ubuntuforums.org/showthread.php?t=1853521"), in search for a solution I pointlessly tried deleting all Jack packages and then reinstall them. I've solved the LADISH problem problem but now I have another one; after the re-install Jack is no longer working. I've tried changing the driver, interface and so on with QjackCtl but can't get it working again, however the server runs like normal but I can't hear anything. When things were working, I used to have like 6 system outputs, but now I have only 2.

So, if anyone haven't got a better idea, I would like to reinstall everything to default settings, just as when things were working flawlessly. But how do I reset it to default settings? I tried reinstall all the jack packages with Synaptic, but the configs are still the same.

---

### Post by CatKiller on 2011-10-12
It depends what you've fiddled with. Per-user configuration is stored in that user's Home folder. It'll be a directory that starts with a . - .jack or something. Just delete those settings and restart JACK. If you fiddled with system-wide settings, you'll need to restore the files that you changed: probably some files under /etc for ALSA and JACK, and potentially PulseAudio. Not at my computer at the moment, so I can't check the filenames for you.

---

### Post by M@s on 2011-10-15
Thanks, but I deleted the ~/.config/rncbc.org/QjackCtl.conf, made a reboot and now it's working!

---

