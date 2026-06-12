---
title: "Could not play video!"
date: 2009-12-15
forum: General Help
---

### Post by malikge on 2009-12-15
Hello.
I am using Ubuntu 8.10 and I want to know how to play 3gp files.
I am using GNOME M PLAYER, TOTEM PLAYER, and M PLAYER.
When I play the 3gp file through Mplayer the video play fine but no sound, it give an error that:

            Cannot find codec for audio foarmat 0x726D6173

and if I play any format video on Mplayer it gives error that:

         Could not open/initialize audio device -> no sound.

any help on that...
Thanks

---

### Post by zeroseven0183 on 2009-12-15
Try [B]VLC Player

[/B]It can play 3GP files

---

### Post by omgseth on 2009-12-15
VLC is really the go-to player for everything. I've never had a single piece of media that VLC didn't play :)

---

### Post by omgseth on 2009-12-15
There should also be codecs in the repositories that you can download. I quick look through the Software Center never hurts ;)

---

### Post by malikge on 2009-12-15
I have installed VLC all the videos run fine but still when I play 3gp files it gives an error that:

                           No suitable decoder module:

how can I install it codecs?

---

### Post by malikge on 2009-12-15
Any Help!

---

### Post by zeroseven0183 on 2009-12-21
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by AlexDudko on 2009-12-21
Install Mobile Media Converter [http://www.miksoft.net/](http://www.miksoft.net/) You could convert your 3gp video to any other format, which you could play with sound. Or install mplayer with its own codecs package **essential** 

P. S. Neither vlc or any other player precompiled and available from repositories will play 3gp video with sound if sound is in .amr format. Codecs for this type of sound format, as far as I know, aren't included in any package in repositories.

---

### Post by andrew.46 on 2009-12-28
Hi Alex,

> **AlexDudko said:**
> Neither vlc or any other player precompiled and available from repositories will play 3gp video with sound if sound is in .amr format. Codecs for this type of sound format, as far as I know, aren't included in any package in repositories.

Exactly. Contrary to the popular belief that vlc 'uses its own codecs' vlc plays amr sound by utilising a version of libavcodec that has had amr support compiled in. It should be less of an issue now libavcodec can be compiled against libopencore-amr but unfortunately the issue grumbles along nevertheless...

Andrew

---

### Post by AlexDudko on 2009-12-28
Though you can find packages with amr codecs for some other distros. For instance rpmfusion's gstreamer-bad-extras for Fedora has it.

---

### Post by Redundant Username on 2009-12-28
Have you tried [Mplayer]("http://www.mplayerhq.hu/design7/news.html")?

---

