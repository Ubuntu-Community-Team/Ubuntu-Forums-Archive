---
title: "howto: use pulseaudio dlna to my dlna/upnp client"
date: 2010-02-21
forum: General Help
---

### Post by joselitux on 2010-02-21
Hi all

I've noticed in my karmic Koala pulseaudio has many options to make my sound discoverable via upnp/dlna server. I've got a ps3 and a Pinnacle Soundbridge, suitable for this protocol and working fine with mt-daapd or ushare. 

But I would like to use mplayer and making the sound available to my devices. I've activated the options in Pulseaudio (paprefs) but can't play music in my client device and I can't see the server in the lan.

this is my config:

**sound Preferences**

 > output > DLNA/upnp Streaming (stereo)

**paprefs**

-Tab Network access
   click on "make discoverable Pulseaudio network sound devices available locally" &  same for "[...] Apple Airtunes"
-tab Network server
   All options clicked on
- tab Multicast RTP
   enabled "receiver", enabled "sender" and selected "send audio from local speakers"
-Tab simultaneous output
    not enabled

**padevchooser**

- Default server: my pc
- Default sink: DLNA/upnp Streaming
- Default source: internal analog Stereo


Can't see any upnp server.

any suggestion?

---

### Post by elfinit on 2010-03-31
Have exact the same problem. I have the feeling that padevchooser does not make any changes. Please help.

---

