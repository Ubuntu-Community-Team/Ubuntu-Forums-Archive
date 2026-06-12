---
title: "Internet Radio -I give up!"
date: 2010-04-23
forum: General Help
---

### Post by paulemony on 2010-04-23
Example:[http://fmodia.terra.com.br/portal/](http://fmodia.terra.com.br/portal/)

In Windows just click "Ouça ou vivo" (Listen Live) and away you go (WMP). Can also select one of "Só os melhore" (Just the hits) and it plays. In Ubuntu I've downloaded Amarok, MPlayer, Rhythm box, Streamtuner, & VLC, but am not going to live long enough to figure out how to stream with any of them (although "Só os melhores" plays OK). Would appreciate someone explaining EXACTLY how to stream this & any other WMP station. No problem with Flash stations such as [http://www.jazzandblues.org/](http://www.jazzandblues.org/) by the way.

---

### Post by Chronon on 2010-04-23
It's probably the case that you don't have the right codecs installed.  Have you installed the package "ubuntu-restricted-extras"?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by avtolle on 2010-04-23
> **chronon said:**
> it's probably the case that you don't have the right codecs installed.  Have you installed the package "ubuntu-restricted-extras"?

[https://help.ubuntu.com/community/restrictedformats](https://help.ubuntu.com/community/restrictedformats)
+1

---

### Post by tgalati4 on 2010-04-23
I tried using mplayer in a terminal:

tgalati4@tpad-Gloria7 ~ $ mplayer [http://fmodia.terra.com.br/portal/](http://fmodia.terra.com.br/portal/)
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 2.13GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://fmodia.terra.com.br/portal/](http://fmodia.terra.com.br/portal/).
Resolving fmodia.terra.com.br for AF_INET6...
Couldn't resolve name for AF_INET6: fmodia.terra.com.br
Resolving fmodia.terra.com.br for AF_INET...
Connecting to server fmodia.terra.com.br[200.177.252.40]: 80...
Cache size set to 320 KBytes
Cache fill:  8.30% (27201 bytes)   
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll

It looks like I'm missing a codec.  Find the codec then you may be able to listen to it.

tgalati4@tpad-Gloria7 /usr/lib/win32 $ ls -la avi*
-rw-r--r-- 1 root root  69632 2001-05-03 06:30 avimszh.dll
-rw-r--r-- 1 root root 114688 2001-05-03 06:30 avizlib.dll

Perhaps copying the avisynth.dll file from a windows machine might work.

---

### Post by bodhi.zazen on 2010-04-23
You could also consider installing streamtuner + audacious => tons of radio stations listed in stremtuner.

---

### Post by mc4man on 2010-04-23
> explaining EXACTLY how to stream this

First see if this is what you wanted for "Ouça ou vivo" (don't understand the language at all..

 possible address's to use in player or from cli


```
mmsh://stream-parc02.terra.com.br/mibodia?url=64211235153121R29911&MSWMExt=.asf
```

some players would probably just prefer
```
mmsh://stream-parc02.terra.com.br/mibodia?url=64211235153121R29911
```

or make a <whatever>.m3u with this inside and open the <whatever>.m3u in a player (stream is wma2 so pretty much any player should play  - for gstreamer apps just install the basic plugins

```
#EXTM3U
#EXTINF:0,Terra Networks - Radio FM O DIA
mmsh://stream-parc02.terra.com.br/mibodia?url=64211235153121R29911


```

Basic plugins for gstreamer
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

---

### Post by paulemony on 2010-04-25
I have streamtuner.audacious, gstreamer, & ubuntu-restricted-extras
already installed, and have tried the terminal entries suggested, but still no luck. As I understand it I either need to get the default players embedded in the radios' websites to work, or otherwise get one of the ubuntu alternatives such as streamtuner to do it, but even if I try to play one of the stations included In the application (such as Virgin Radio Classic Rock) streamtuner just closes! Can someone advise if it's actually possible to use streamtuner (or another application) to stream any station broadcasting on the net, & if so how to do it?

---

### Post by oldos2er on 2010-04-25
> **paulemony said:**
> Example:[http://fmodia.terra.com.br/portal/](http://fmodia.terra.com.br/portal/)

In Windows just click "Ouça ou vivo" (Listen Live) and away you go (WMP). 

This works for me. Have you installed w32codecs (or w64codecs if you're running 64-bit Ubuntu)? You'll need to enable the Medibuntu repository if you haven't already. [http://www.medibuntu.org](http://www.medibuntu.org)

---

### Post by Chronon on 2010-04-25
It streams right in firefox for me, so I assumed that installing codecs was the only roadblock.

---

### Post by mc4man on 2010-04-25
While there's no reason not to install w32codecs (w64codecs is pretty much worthless) I don't see where it should matter here
The stream is wma2 which is decoded by libavcodec and is mmsh which for gstreamer is supported by the bad plugin (pulls in libmms

As far as in browser the totem-mozilla plugin should work,(does here) one could always remove it and try the gecko-mediaplayer plugin instead.

On a side note - though not needed here one can improve the capabilities of the gstreamer plugins in karmic by enabling this ppa and updating. (brings karmic's gstreamer up to date, adds wma3(pro, amr thru opencore, ect.

[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

Edit:
Just to check something I booted to a hardy install that is straight up (in karmic and lucid have replaced the shared ffmpeg libs with my own

The stream linked above played back fine with the non-updated ffmpeg libs installed.
Then I allowed them to be updated and no good
If you recently had your ffmpeg libs updated then that may be your issue.
Updates to the ffmpeg libs for hardy thru karmic have broken decoding of wma - I thought I'd mentioned this - was another post

Hopefully updated packages will arrive shortly

updated packages for karmic will be available Mon..

related threads
[http://ubuntuforums.org/showthread.php?p=9161231#post9161231](http://ubuntuforums.org/showthread.php?p=9161231#post9161231)
[http://ubuntuforums.org/showthread.php?p=9166101#post9166101](http://ubuntuforums.org/showthread.php?p=9166101#post9166101)

---

### Post by WinterRain on 2010-04-26
The link works for me. I have the gecko mediaplayer firefox plugin. If you are using ubuntu 9.10 or earlier, you can also use the mozilla-mplayer plugin.

---

### Post by paulemony on 2010-04-26
"While there's no reason not to install w32codecs (w64codecs is pretty much worthless) I don't see where it should matter here
The stream is wma2 which is decoded by libavcodec and is mmsh which for gstreamer is supported by the bad plugin (pulls in libmms"

Which to me means:
&#932;&#959; &#961;&#949;&#973;&#956;&#945; &#949;&#943;&#957;&#945;&#953; wma2 &#960;&#959;&#965; &#945;&#960;&#959;&#954;&#969;&#948;&#953;&#954;&#959;&#960;&#959;&#953;&#949;&#943;&#964;&#945;&#953; &#945;&#960;&#972; &#964;&#959; libavcodec &#954;&#945;&#953; &#949;&#943;&#957;&#945;&#953; mmsh &#960;&#959;&#965; &#947;&#953;&#945; &#964;&#959; gstreamer &#965;&#960;&#959;&#963;&#964;&#951;&#961;&#943;&#950;&#949;&#964;&#945;&#953; &#945;&#960;&#972; &#964;&#959; &#954;&#945;&#954;&#972; plugin (&#964;&#961;&#945;&#946;&#940; &#963;&#964;&#945; libmms

However it sounds logical enough to be the answer, if someone can explain exactly (and I mean "exactly") what buttons to press to put this into action please elucidate!

---

### Post by Chronon on 2010-04-26
Open Synaptic or the Software Center and search for libavcodec52 and install that.  You probably also want to search for "gstreamer" and install the 'good', 'bad' and 'ugly' packages.

---

### Post by oldos2er on 2010-04-26
Did you try the info in post #2?

---

### Post by mc4man on 2010-04-26
> Which to me means:..

Didn't mean to confuse you, comment was more directed elsewhere and hopefully to point out you already have all you need installed.

> downloaded Amarok, MPlayer, Rhythm box, Streamtuner, & VLC, 
I have streamtuner.audacious, gstreamer, & ubuntu-restricted-extras
already installed

I think it's very likely you were affected by the slightly borked libavcodec update as mentioned in my last post with links

Reverted packages have been built - try updating thru the update manager (libavcodec, libavformat, ect.

link to bug 
[https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/567913](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/567913)

---

### Post by rjcroy on 2010-04-26
One thing I found last night about the totem-mozilla plugin when streaming some internet radio is that it was working embedded in the webpage, but that the volume was turned down to Zero in the player (not the desktop volume mind), so no sound! If I clicked on the embedded totem to bring it up full-screen I could turn up the volume and all was good.

---

