---
title: "problem configuring mplayer"
date: 2006-04-04
forum: General Help
---

### Post by harys on 2006-04-04
hi, ive installed mplayer with synaptic manager using this wiki link : [https://wiki.ubuntu.com/MplayerInstallHowto?highlight=%28mplayer%29](https://wiki.ubuntu.com/MplayerInstallHowto?highlight=%28mplayer%29) . i get the root privileges in the terminal and run gedit ~/.mplayer/config. i copy and paste the following block into the file : 
# Specify default video driver (see -vo help for a list).
vo=xv,sdl,x11

# Specify default audio driver (see -ao help for a list).
ao=alsa,oss,sdl,esd,arts

# Drop frames to preserve audio/video sync.
framedrop = yes

# get a default OSD font from fontconfig
fontconfig = yes
font = "Sans"
subfont-text-scale = 3
But when i save the file i got this error message : Could not save the file "/root/.mplayer/config". need a help. thanks. harys

---

