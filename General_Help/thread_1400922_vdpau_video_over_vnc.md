---
title: "vdpau video over vnc?"
date: 2010-02-07
forum: General Help
---

### Post by kilowhisky on 2010-02-07
It appears vino doesn't allow for vdpau/hardware accelerated video to be displayed over vnc. Is there any way to enable it or a different vnc server that allows for this?  Google has failed me. 

I'm currently using nvidia driver 195.30 on ubuntu 9.10 with kernel 2.6.31-16-server.

---

### Post by falconindy on 2010-02-07
Video over VNC? Good luck with that. Given network connectivity, you have 2 options:

1) Use a proper network stream (VLC has the ability to do this)
2) Mount the remote drive (NFS, Samba, SSHFS, etc.) and play the video on a local media player.

---

### Post by kilowhisky on 2010-02-07
> **falconindy said:**
> Video over VNC? Good luck with that. Given network connectivity, you have 2 options:

1) Use a proper network stream (VLC has the ability to do this)
2) Mount the remote drive (NFS, Samba, SSHFS, etc.) and play the video on a local media player.

I'm not try to actually play the video over vnc. Some apps like xbmc, boxee, mythtv just display a black screen over it for everything including the menus and often i log via vnc to configure things or test settings.

---

