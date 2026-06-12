---
title: "MPD shoutcast"
date: 2010-03-08
forum: General Help
---

### Post by akernan on 2010-03-08
I'm using MPD with no problem locally, but I'd like to broadcast to rest of my network.  I have shoutcast enabled with the internal MPD httpd server.  I can connect and it plays a song for about 30 secs and stops.  I'm unable to connect to the stream with other audio players like VLC.  Any Ideas?

Thanks,
Tony

---

### Post by Sin@Sin-Sacrifice on 2010-03-08
Not sure but you might want to ask the [Networking guys]("http://ubuntuforums.org/forumdisplay.php?f=336"). They love that stuff.

---

### Post by akernan on 2010-03-12
I put a post in the networking section a couple days ago and no one replied.  Can someone here help me?

---

### Post by n0dix on 2010-03-12
Well, you can add streams to MPD from Shoutcast and play them. But, Shoutcast itself, i don't think so.

---

### Post by akernan on 2010-03-12
Ok, you lost me...I am doing broadcasts with MPD, but they only play for about 30 secs before stopping.

---

### Post by n0dix on 2010-03-12
You need a special configuration in your mpd.conf file.
See the doc in [Arch Doc]("http://wiki.archlinux.org/index.php/Music_Player_Daemon").

The info to add in mpd.conf is:
```
audio_output {
          type   "httpd"
          name   "What you want"
          encoder "lame"     # vorbis or lame supported
          port    "8000"
          bitrate  "128"
          format   "44100:16:2"  # change 2 to 1 for mono
  }
```

---

### Post by akernan on 2010-03-12
> **n0dix said:**
> You need a special configuration in your mpd.conf file.
See the doc in [Arch Doc]("http://wiki.archlinux.org/index.php/Music_Player_Daemon").

The info to add in mpd.conf is:
```
audio_output {
          type   "httpd"
          name   "What you want"
          encoder "lame"     # vorbis or lame supported
          port    "8000"
          bitrate  "128"
          format   "44100:16:2"  # change 2 to 1 for mono
  }
```

I added the above lines to /etc/mpd.conf and when I restart the daemon I get the following error **output: line 51: No such encoder: lame**.  I don't know why I'm getting this error because lame is installed.

---

### Post by n0dix on 2010-03-13
> **akernan said:**
> I added the above lines to /etc/mpd.conf and when I restart the daemon I get the following error **output: line 51: No such encoder: lame**.  I don't know why I'm getting this error because lame is installed.

Try with: "vorbis"

---

### Post by akernan on 2010-03-13
I changed it back to vorbis, that got rid of the error.  I changed my web browser prefs and used the m3u-handle.sh script to open the playlist, that fixed my problem.  Thanks for the replies.

I also added Music Player Minion add-on to Firefox so I could control MPD.

---

