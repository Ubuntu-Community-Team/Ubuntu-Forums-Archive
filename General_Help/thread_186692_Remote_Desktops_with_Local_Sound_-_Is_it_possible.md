---
title: "Remote Desktops with Local Sound - Is it possible?"
date: 2006-06-02
forum: General Help
---

### Post by maxweld on 2006-06-02
Is it possible to get local sound when running a remote desktop?

I have an old laptop which I can already connect to my main machine using XDMCP - this works fine except that any sound produced is on the main machine and not on the laptop. 

Is it possible to to get the sound to the laptop using XDMCP?

Or - and what got me excited - I opened the 'Terminal Server Client' applications (Applications -> Internet -> Terminal Server Client) and noticed some of the settings which are greyed out 

On the General tab, under the protocols, it suggests that XDMCP might be available, but it is greyed out. And under the Local Resources tab. it suggests that local sound might be possible. Does any body have any experience of this?

Or - does anybody have experience of the other protocols suggested which are not greyed out (RDP, RDPv5 & VNC) Which are known to work well with sound? Are these better than XDMCP? Which is best, and easy to set up?

Thanks

---

### Post by maxweld on 2006-06-02
Moving thios to Desktop Forum

---

### Post by garyng on 2006-06-02
esound daemon.

I would try freenx/nxclient though as that already does the dirty work for you, i.e. the client has a esd(at least on the windows client) builtin and makes the right environment variable setup so any apps on the server knows esd would do the right thing.

---

