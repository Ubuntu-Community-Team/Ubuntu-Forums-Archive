---
title: "Random logout/crashes"
date: 2011-02-06
forum: General Help
---

### Post by Alternated on 2011-02-06
Hi, I'm using Ubuntu 10.10 and it crashes to the login screen repeatedly- at least once for every time the computer starts up. I can't see any real pattern to it.

(When I log back in, the sound is always muted... which is weird)

I'm a happy-but-clueless newbie-- 'fraid you'll have to keep it simple :-)


Here's some bad-sounding extracts from syslog that I've often seen timestamped from around the time of a crash. Hope they're useful:

    pulseaudio[3460]: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 144.
    pulseaudio[3460]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
(..)
    gdm-session-worker[3453]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
    NetworkManager[707]: <error> [1297030642.506413] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
    NetworkManager[707]: <error> [1297030642.575489] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name

---

### Post by mörgæs on 2011-02-07
How stable is the system if you run from a live CD?

---

### Post by Alternated on 2011-02-07
Just tested the system out with the Live CD over a few hours.

Yes-- the system seems completely stable when running from the Live CD.

---

### Post by mörgæs on 2011-02-08
Then I guess a good first step is simply to back up your files and reinstall. Remember to have wired internet access during installation.

---

### Post by P4man on 2011-02-08
Might also be worth checking your disk. from the live session, go to system > administration > disk utility. Select your harddrive and check the SMART status. If it says smart is not enabled, go in to your BIOS settings and enable it there.

---

