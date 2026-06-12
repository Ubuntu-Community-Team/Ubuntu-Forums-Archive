---
title: "Rythmbox / Coherence: DLNA client / server broken in 11.04 - fixes?"
date: 2011-04-17
forum: General Help
---

### Post by Mac9 on 2011-04-17
Has anyone else come across the following issue in the 11.04 beta?

For some reason I can't see Rhythmbox as a DLNA server anymore and its stopped working as a DLNA client. I've reported it as a bug here -> [URL="https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/757840"]

Am I the only one missing this feature?

Regards,
Mac

---

### Post by Mac9 on 2011-04-24
Just made a discovery which I thought I'd share with you all.

I found the source of inspiration at -> [http://coherence.beebits.net/wiki/RhythmBox](http://coherence.beebits.net/wiki/RhythmBox)

To get the Coherence plug-in to Rythmbox working again I deleted the following folder: upnp_coherence and retrieved the latest version using the instruction contained at the above site

YAY! :-)

---

### Post by Mac9 on 2011-04-25
PARTIALLY SOLVED: DLNA Servers are now visible in Rythmbox's side pane. 

The reason I'm now saying the issue is partially resolved, is that the plug-in now only lists 144 tracks, rather than the whole library. And the Android DLNA App I use can't control Rhytmbox any-more.

---

