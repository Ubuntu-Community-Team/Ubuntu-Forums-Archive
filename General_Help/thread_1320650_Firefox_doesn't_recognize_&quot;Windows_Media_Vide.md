---
title: "Firefox doesn't recognize &quot;Windows Media Video 9&quot; videos."
date: 2009-11-09
forum: General Help
---

### Post by Somme on 2009-11-09
These packages have been already installed:
```
ubuntu-restricted-extras
w32codecs
non-free-codecs

```What else do I need to be able to play [COLOR=Gray]Windows Media Video 9[/COLOR] videos ? As an example, [this video]("http://www.tvnet.lv/onlinetv/play.php?id=347119&aid=347116&vfrag=0&adv=1&rand=0.70236557141364").

---

### Post by jbrown96 on 2009-11-09
You can try to install mozilla-plugin-vlc. I tried to open the video in VLC, but I got a codec error. The audio seemed to play, but not video. You could also try mozilla-mplayer. You will need to uninstall the vlc plugin and then close firefox before install mplayer.

---

### Post by Somme on 2009-11-09
> **jbrown96 said:**
> You can try to install mozilla-plugin-vlc. I tried to open the video in VLC, but I got a codec error. The audio seemed to play, but not video. You could also try mozilla-mplayer. You will need to uninstall the vlc plugin and then close firefox before install mplayer.

VLC plugin didn't worked ( "Waiting for video .." ). Do I need to install mplayer before I'll be able to use it's plugin with Mozilla ?

---

### Post by 6205 on 2009-11-09
Best choice in default GNOME desktop is default Totem-mozilla plugin. VLC or mplayer plugins are crap.. Just be sure that you have installed all necessary Gstreamer plugins like gstreamer plugins-bad, bad-multiverse, ugly, ugly-multiverse, gstreamer-ffmpeg and pitfdll + their depencies. But if you have VLC or mplayer plugins, first you have to remove them.

---

### Post by Somme on 2009-11-09
> **6205 said:**
> Best choice in default GNOME desktop is default Totem-mozilla plugin. VLC or mplayer plugins are crap.. Just be sure that you have installed all necessary Gstreamer plugins like gstreamer plugins-bad, bad-multiverse, ugly, ugly-multiverse, gstreamer-ffmpeg and pitfdll + their depencies. But if you have VLC or mplayer plugins, first you have to remove them.

I don't have Gnome installed and I've never used Totem, which is why it's not installed. Will give a try.

---

### Post by NFblaze on 2009-11-09
I tried it in Totem, and it didnt work for me. I actually havent used VLC, but the Totem plugin for Firefox sucks also. It wasnt too long ago that Totem itself gave me so many problems. Also, the codecs used for decoding with Totem are gstreamer. If you have luck let us know.

---

### Post by andrew.46 on 2009-11-10
Hi Somme,

> **Somme said:**
>  As an example, [this video]("http://www.tvnet.lv/onlinetv/play.php?id=347119&aid=347116&vfrag=0&adv=1&rand=0.70236557141364").

This stream played with the gecko-mediaplayer although the quality was pretty bad. Is this a low quality stream?

Andrew

---

### Post by Somme on 2009-11-10
> **andrew.46 said:**
> Hi Somme,



This stream played with the gecko-mediaplayer although the quality was pretty bad. Is this a low quality stream?

Andrew

Ok, thanks - will give it a try when I will solve my network issues ( another story in a separate thread ). As for the quality - yes, it's an embedded stream ( by default it's only 250x250 or so ) and the quality might suck if you want to watch it in full-screen mode ( tough, I never do that ).

---

### Post by Somme on 2009-11-10
After installing mplayer and it's plugin, I still can't watch my videos. It shows a black/white ( changing ) rectangle .. :neutral:

---

### Post by andrew.46 on 2009-11-10
Hi Somme,

> **Somme said:**
> After installing mplayer and it's plugin, I still can't watch my videos. It shows a black/white ( changing ) rectangle .. :neutral:

MPlayer has a few different plugins written for it, the one I am using successfully is the gecko-mediaplayer. BTW you may be interested to know that the *real* address for the stream is:

mms://stream.grafton.lv/20091109_900_sekundes.wmv

Fascinating how the actual address is morphed like that :). Once I found the *real* location of the stream it was easier to examine. The stream is as you suspected Windows Media Video 9 and MPlayer most commonly uses the external wmv9dmo codec for this. So if you have a 32bit system you can add the Medibuntu repository:

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```

and then the codec package:

```
sudo ap-get install w32codecs
```

and then MPlayer and the gecko-mediaplayer will play this stream back for you, although I note that you feel you already have w32codecs installed? If you are running a 64bit MPlayer you may very well be out of luck as this codec is not supported under a pure 64bit installation.

All the best,

Andrew

---

### Post by Somme on 2009-11-10
> **andrew.46 said:**
> Hi Somme,
 
 
 
MPlayer has a few different plugins written for it, the one I am using successfully is the gecko-mediaplayer. BTW you may be interested to know that the *real* address for the stream is:
 
mms://stream.grafton.lv/20091109_900_sekundes.wmv
 
Fascinating how the actual address is morphed like that :). Once I found the *real* location of the stream it was easier to examine. The stream is as you suspected Windows Media Video 9 and MPlayer most commonly uses the external wmv9dmo codec for this. So if you have a 32bit system you can add the Medibuntu repository:
 
```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```
 
and then the codec package:
 
```
sudo ap-get install w32codecs
```
 
and then MPlayer and the gecko-mediaplayer will play this stream back for you, although I note that you feel you already have w32codecs installed? If you are running a 64bit MPlayer you may very well be out of luck as this codec is not supported under a pure 64bit installation.
 
All the best,
 
Andrew
 
Yes, w32codecs have been already installed but it still doesn't want to play .wmv. Even if I open the stream with VLC, I get a black screen ( instead of the actual video and audio ). Weird that .. videos work fine if I try to open them on Ubuntu ( standard Gnome ) :roll:

---

### Post by andrew.46 on 2009-11-10
Hi Somme,

> **Somme said:**
> Yes, w32codecs have been already installed but it still doesn't want to play .wmv. Even if I open the stream with VLC, I get a black screen ( instead of the actual video and audio ).

Unfortunately the way the vlc package is setup under Ubuntu the w32codecs are *not* used by vlc, although it is commonly believed that it *does*. MPlayer however does not have this limitation.

Andrew

---

### Post by Somme on 2009-11-11
> **andrew.46 said:**
> Hi Somme,
 
 
 
Unfortunately the way the vlc package is setup under Ubuntu the w32codecs are *not* used by vlc, although it is commonly believed that it *does*. MPlayer however does not have this limitation.
 
Andrew
 
Oh, ok - thnx for the information. MPlayer still shows me only white flashing rectangle.
One thing that made me wonder was the fact that when I enabled NoScript, I saw the video preview ( which normally doesn't show up even if it's disabled ), tough, wasn't able to play it :(

---

### Post by wilee-nilee on 2009-11-11
I think that is a bad link, it wont even play on my W7 setup with the K lite codecs installed and vlc. I get the waiting for video. gxine might be another option it is in synaptic.

---

### Post by Somme on 2009-11-11
> **wilee-nilee said:**
> I think that is a bad link, it wont even play on my W7 setup with the K lite codecs installed and vlc. I get the waiting for video. gxine might be another option it is in synaptic.
 
Windows XP - never had any problems ( and even right now while I'm writing this, one of them plays in background )
Windows 7 - tried a few days ago .. worked without any additional codecs.
 
As I said, it works on Ubuntu 9.10 too, but I can't get it up and running on Ubuntu Minimal + Openbox.

---

### Post by Somme on 2009-11-11
Damn, I think I'll just need to pass .. Now when I finally got mplayer plugin up and running ( in terms of .. progress ), video contains 2 blue rectangles and is gray ( like 10 years ago ).

Any ideas ? I've tried so many things ( related to this problem ) that my HDD will soon start to run out of space .. :D

---

