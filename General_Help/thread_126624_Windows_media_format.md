---
title: "Windows media format"
date: 2006-02-07
forum: General Help
---

### Post by fakie_flip on 2006-02-07
How can I play movies in and songs that are in windows media format? I like to use Totem player. Is it possible?

---

### Post by newuser111 on 2006-02-07
yes you use mplayer

or just use automatix, it will install all that stuff for you

---

### Post by nanotube on 2006-02-07
unfortunately, i dont think its possible to get totem to play that stuff. in my experience, totem is pretty useless to play just about anything. install mplayer (package mplayer-586) and it should play. read this page for more info:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#DVD.2C_Video.2C_and_Audio_playback](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#DVD.2C_Video.2C_and_Audio_playback)

---

### Post by Perfect Storm on 2006-02-07
Well, you can get Totem play very decent, this require universe and multiverse enable and PLF added:

```
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs lame sox ffmpeg mjpegtools vorbis-tools libdvdcss2 gstreamer0.8-plugins-multiverse avifile-divx-plugin avifile-mad-plugin avifile-mjpeg-plugin libdvdnav4 libdvdplay0 libdvdread3 totem-xine
gst-register-0.8
```

Though I recommend VLC:

```
sudo apt-get install wxvlc w32codecs libdvdnav4 libdvdplay0 libdvdread3 libdvdcss2
```

---

### Post by fakie_flip on 2006-02-09
I installed mplayer after enabling multiverse repositories. It also put XMMS in my Applications>Sound & Video menu in gnome. I have no idea what XMMS is. I am getting the error shown in the picture I attached. mplayer installed so many dependencies, that I wouldn't remember them if I wanted to uninstall them with mplayer.

---

### Post by Jens Willem on 2006-02-09
> How can I play movies in and songs that are in windows media format? I like to use Totem player. Is it possible?

Yes, it is. You only need to install the codecs. And if you want to use Totem, I recommend you to install totem-xine ("a more capable version of totem", according to the official wiki... and it's true!). All the information you need is here: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by carlosqueso on 2006-02-09
For Windows Media, follow these instructions after the ones above:

[http://www.ubuntuforums.org/showpost.php?p=411934&postcount=12](http://www.ubuntuforums.org/showpost.php?p=411934&postcount=12)

---

### Post by nanotube on 2006-02-10
hey
that font error is easy to fix. check out the howto on my howto page, here:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#DVD.2C_Video.2C_and_Audio_playback](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#DVD.2C_Video.2C_and_Audio_playback)
(look at the part that mentions your font error).
have fun.

---

### Post by nanotube on 2006-02-10
oh, and another thing - you can see all the packages that got installed with mplayer by opening up synaptic, and going File > History. there, search for mplayer, and it will show you all the packages that got installed at the same time as mplayer.
kind of a pain in the *** to go and uninstall them all, but at least you know what they are now. :) 
that is, if you do decide to uninstall mplayer. once you fix the font error, you probably will not want to - its a good media player.

---

