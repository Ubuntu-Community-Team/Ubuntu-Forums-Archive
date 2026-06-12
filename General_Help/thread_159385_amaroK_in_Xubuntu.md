---
title: "amaroK in Xubuntu"
date: 2006-04-12
forum: General Help
---

### Post by DigitalDuality on 2006-04-12
My amaroK won't play any files whatsoever, just got Xubuntu installed on Flight 6.  

It seems i can't install a bunch of Restricted Formats actually, i don't recall the messages, but my mp3, ogg, flacs and such play just fine in VLC and XMMS, i'd just rather have them in amaroK.

Any ideas?

---

### Post by Ramses de Norre on 2006-04-12
I think you need a couple of kde libraries to get amarok running.
I've got the whole kubuntu-desktop installed and amarok runs fine in other desktop environments.
Have you got all the gstreamer plugins installed? They are also used by amarok.

---

### Post by aysiu on 2006-04-12
Maybe it's a bug? You are using Dapper Drake, after all.

---

### Post by barthel on 2006-04-12
I'm listening to amaroK right now on Dapper. However, one of the changes I had to make was to use the xine engine instead of gstreamer.

Stable amaroK requires gstreamer-0.8, but dapper has gstreamer-0.10. The amaroK team is working on on gstreamer-0.10 support, but it hasn't reached the betas yet (and the beta packages have other dependencies that would remove part of dapper.)

If enough of the gstreamer-0.8 packages are still installed on your system, amaroK may not have automatically switched engines for you. 

So, if this is the issue, the fix would be:
[LIST=1]
[*]If not already installed, install the amaroK-xine package via Synaptic.
[*]Launch amaroK and select "Settings->Congiure amaroK".
[*]Click on "Engine" and change the "Sound System" to "xine Engine".
[/LIST]

Good luck!

---

### Post by DigitalDuality on 2006-04-12
nope that's not it.  the xine-engine was selected already.

---

