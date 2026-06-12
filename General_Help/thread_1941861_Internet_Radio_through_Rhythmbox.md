---
title: "Internet Radio through Rhythmbox"
date: 2012-03-16
forum: General Help
---

### Post by sabby787 on 2012-03-16
Hello all,

Having a problem streaming internet radio through Rhythmbox. I add the station url, it buffers, it even shows me the artist, song info, etc. But it doesn't actually play. Yes my sound is working, yes the volume isn't muted. 

One thing I just noticed is it doesn't update the title song. If i reload the station it will update, but not if I leave it alone. Therefore it probably isn't playing. But I'm not getting any error messages.

Any ideas?

---

### Post by sabby787 on 2012-03-16
Restarted rhythmbox after installing a plugin, now it works. :guitar:

---

### Post by Sylslay on 2012-03-31
Some radio station move to their "flash palyers" like iBBC etc
and older "radio servers" are turned off ???

Plugin for radios, insteld via treminal.

sudo apt-get install rhythmbox-radio-browser

---

### Post by colobix on 2012-04-01
> **Sylslay said:**
> Some radio station move to their "flash palyers" like iBBC etc
and older "radio servers" are turned off ???

Plugin for radios, insteld via treminal.

sudo apt-get install rhythmbox-radio-browser

I don't know if flash (rtmp) streams will work in rhythmbox though.
Haven't tested it.
But if the original rtsp stream is not password protected by the broadcaster, you could use wireshark to find it.

---

