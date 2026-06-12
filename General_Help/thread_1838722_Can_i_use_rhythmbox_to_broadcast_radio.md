---
title: "Can i use rhythmbox to broadcast radio?"
date: 2011-09-04
forum: General Help
---

### Post by Reduced_Oxygen on 2011-09-04
I'm looking for a plugin which will allow me to broadcast whatever im listening to, so that others can connect and listen using my IP

---

### Post by Reduced_Oxygen on 2011-09-04
I found BUTT, but how do i install it

---

### Post by raja.genupula on 2011-09-04
[http://techcrunch.com/2007/06/07/make-your-own-internet-radio-station-ubroadcast/](http://techcrunch.com/2007/06/07/make-your-own-internet-radio-station-ubroadcast/)

---

### Post by Reduced_Oxygen on 2011-09-04
do u know how to setup a server? for shoutcast or icecast?

---

### Post by raja.genupula on 2011-09-04
[http://www.frihost.com/forums/vt-15354.html](http://www.frihost.com/forums/vt-15354.html)


go with this

---

### Post by Reduced_Oxygen on 2011-09-04
I appear to have a problem with BUTT, everything i broadcast comes out quiet and super treble

---

### Post by Reduced_Oxygen on 2011-09-05
Ok i had it all hooked up to a server with B.U.T.T. but everything comes out super treble... ?

---

### Post by cryptotheslow on 2011-09-05
Hmm... can't say I've used BUTT.

I've found IDJC to be a pretty competent shoutcast / icecast broadcaster. You'll find it in the repos. Last time I installed it on 10.04 it just worked without any messing around.

Previously (on 9.10) I had to mess around with jackd and alsa settings to get it right.

[http://idjc.sourceforge.net/install_first_run.html](http://idjc.sourceforge.net/install_first_run.html) is a useful resource.

It might be a bit over the top for what you want to achieve.

---

### Post by Reduced_Oxygen on 2011-09-06
IDJC is awsome but i was looking for somthing that could simply capture sound from rhythmbor my sound card

---

### Post by cryptotheslow on 2011-09-07
IDJC uses Jack for its input/output so it would be possible to use the Jack patch panel app to hook your soundcard output to say an unused aux input and have IDJC stream that. It would be a bit of a kludge to say the least but it's do-able. Not really much point to be honest - IDJC's strength is really its dual decks (playlists), crossfades, bed tracks and jingles - great for full on shoutcast dj'ing but in your setup you'd just be using its shoutcast encoding bits.

Only problem using an app that grabs all your soundcad output and streams it is that it will include all the dings etc. produced by any other apps.... hope you don't use voice chat :D You do really need a player specific shoutcast plugin like the SHOUTcast DSP Plug-In for Winamp - but that's Windows only unfortunately....  and IME quite prone to crashing Winamp completely if you change the playlist while streaming.

Best of luck, let us know what you cobble together :)

---

### Post by Reduced_Oxygen on 2011-09-08
I think i'll work on getting either butt or the shoutcast plugin for rhythmbox working, im not doing a radio station, just wanted a way that me and friends could all listen to the same music

---

