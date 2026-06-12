---
title: "Internet Radio Application?"
date: 2011-08-04
forum: General Help
---

### Post by unknown user on 2011-08-04
I am looking for a good application that I can use it listen to an Internet radio station with, without opening the stations website and then loading it that way. Something that will sit in my system tray, out of the way. I looked in the software center and thought that Radio Tray may be the answer, but it would not load on my 11.04 system. I then looked at KRadio, but could not enter the radio station I needed. Does anyone know any good apps that I could use to do this?

---

### Post by bodhi.zazen on 2011-08-04
I personally use streamtuner, not sure if it will fit your needs.

---

### Post by oldos2er on 2011-08-04
Amarok, vlc, mplayer, kaffeine, etc.

---

### Post by ron999 on 2011-08-04
....

---

### Post by flemur13013 on 2011-08-04
I use VLC because it's far better than anything else I found for dealing with playlists - it's playlist format compatibility and the station info it displays are better than other programs (some programs just show the URL w/no title) .  

I got the playlist entries from various websites, like you're trying to do.

I start it like this: 

```
vlc /data/music/Playlists/0_OTR_NPR.m3u & 
```The M3U file consists of URLs for OTR (old time radio) stations from shoutcast (tho I forget how I got them; I just remember that it was a PITA) and NPR stations from their websites.

Also, because the formats seem to vary depending on which program wrote the file, the M3U file looks like this:
```
#EXTM3U
#EXTINF:0,00 NPR CPR KCFR 1
http://66.162.107.142/cpr1_lo
#EXTINF:0,GBS SciFi Radio
http://94.102.154.146:7236/
...repeat last two lines for each station...
```
(The "00 NPR" is part of the title - zeros for ordering by name)

---

### Post by andrew.46 on 2011-08-04
There is a nice extension for vlc that makes radio playback a snap: [Streaming Radio Player Extension for VLC]("http://www.coderholic.com/extending-vlc-with-lua/"). I attach a gratuitous screenshot of this extension in action with vlc :).

---

### Post by spottedhog on 2011-08-24
Radio Tray.  [http://radiotray.sourceforge.net/]("http://radiotray.sourceforge.net/")

---

### Post by raja.genupula on 2011-08-24
banshee also having radio application .last.fm . how it sounds  ?

---

