---
title: "Sound in Gnome broken but fine in rest of programs"
date: 2006-05-26
forum: General Help
---

### Post by AirRaven on 2006-05-26
I can't seem to get any sound at all out of my GNOME- it won't preview any music files when I hover my mouse over them, and I can't play anything in RhythmBox- it just gives the "ERROR" icon next to the song title and moves onto the next song.

The strange thing is, things like Xine and VLC still have perfect sound. I even have sound in gdm when I start up. It's just GNOME.

Any ideas what's gone wrong?

---

### Post by Lord Illidan on 2006-05-26
Is esd running?
Also, could it be a codec issue? Does Totem play mp3s?

---

### Post by AirRaven on 2006-05-26
[QUOTE=Lord Illidan]Is esd running?
Also, could it be a codec issue? Does Totem play mp3s?[/QUOTE]
How do I tell if esd's running? I'm still not completely sure where everything is in Ubuntu yet. It doesn't come up in the System Monitor, if that's what you mean.

And yeah- Totem-xine plays MP3s perfectly.

---

### Post by Lord Illidan on 2006-05-26
[quote=AirRaven]How do I tell if esd's running? I'm still not completely sure where everything is in Ubuntu yet. It doesn't come up in the System Monitor, if that's what you mean.

And yeah- Totem-xine plays MP3s perfectly.[/quote]

Did you install the gstreamer codecs?

Lastly, run rythmbox from a terminal, and see what error messages it puts up.

---

### Post by AirRaven on 2006-05-26
[QUOTE=Lord Illidan]Did you install the gstreamer codecs?

Lastly, run rythmbox from a terminal, and see what error messages it puts up.[/QUOTE]
I've installed every Gstreamer codec that's vaguely related- still nothing.

I just upgraded Totem-xine to the latest Totem-Gstreamer and Rhythmbox seems to work fine now for some reason. Might not be related- I did install a bunch of other GStreamer related packages at the same time.

When I run Rhythmbox now I get this:
[quote=Rhythmbox from Terminal](rhythmbox:10720): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

(rhythmbox:10720): Rhythmbox-WARNING **: Unable to load icon media-eject

(rhythmbox:10720): Rhythmbox-WARNING **: Unable to start mDNS browsing
[/quote]

Probably nothing to do with what the problem here is. 

I still can't get any sound in GNOME proper. Which is bizarre- no logon sounds work, and no previews of MP3 files/other sound files in Nautilus.

---

### Post by Sweet Spot on 2007-05-10
Thought I'd bump this thread since I have a related problem. Ran rhythmbox in terminal which gave me : > (rhythmbox:5855): Rhythmbox-WARNING **: Unable to start mDNS browsing: MDNS serv ice is not running


Will search more for this, but could it be related ?

---

### Post by rudiz on 2007-05-10
Try this Firefox add-on:

MultimediaPlayerConnectivity

---

