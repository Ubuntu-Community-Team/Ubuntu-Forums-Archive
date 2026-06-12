---
title: "VLC won't work well on Maverick"
date: 2011-04-17
forum: General Help
---

### Post by PCaddicted on 2011-04-17
Hi,
I've installed VLC media player on my Ubuntu 10.10 system.I downloaded a video in nbr format from the Neverball official website(neverball.org) but VLC couldn not play it.I downloaded some other videos and VLC was still unable to run them.
But I have some video clips in flv format and in ogg and VLC can play them.
Does Ubuntu or the VLC media player have a problem?Do you suppose I have to install more libraries/codecs in order to play clips from neverball.org?
[Also,I would like to be answered on the other thread,because I still haven't fixed the Gtkradiant run error(URL:[http://ubuntuforums.org/showthread.php?t=1729207]("http://ubuntuforums.org/showthread.php?t=1729207"))]

---

### Post by flipper T on 2011-04-17
what on earth is nbr format ?

---

### Post by PCaddicted on 2011-04-17
That is simply the format of the videos I downloaded from the Neverball official website!I had never heard of it before,but it is a format...any help?
If you are not convinced,go where I went myself: [http://table.nevercorner.net/]("http://table.nevercorner.net/")
Download a video from there and try to play it with VLC and the default player of Ubuntu.
See if it works.

---

### Post by flipper T on 2011-04-17
pls give exact link to these files on neverball.org

i can't find them

---

### Post by flipper T on 2011-04-17
wow


nbr is a game replay

clue: **_N_**ever _**B**_all _**R**_eplay...you expect vlc to play this ?


load it into neverball and watch to your hearts content.

---

### Post by PCaddicted on 2011-04-17
The files are listed on that page beginning with 12d.Click on the game controller button(at the right) to download the file you are trying to get.Hope you've understood.As far as I know from my own experience,you do not need to have Javascript enabled.

---

### Post by PCaddicted on 2011-04-17
Oh,thank you for the clue..I am feeling so silly now!But how can I play that replay inside Neverball,on Ubuntu,any ideas?

---

### Post by flipper T on 2011-04-17
i'd go back to neverball.org's forum and ask

---

### Post by garvinrick4 on 2011-04-17
```
Package: vlc                             
State: installed
Automatically installed: no
Version: 1.1.9-1ubuntu1
Priority: optional
Section: universe/graphics
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 3,797 k
Depends: ttf-freefont, vlc-nox (= 1.1.9-1ubuntu1), libaa1 (>= 1.4p5),
         libavcodec52 (>= 4:0.6-1~) | libavcodec-extra-52 (>= 4:0.6-1~),
         libavutil50 (>= 4:0.6-1~) | libavutil-extra-50 (>= 4:0.6-1~), libc6 (>=
         2.8), libfreetype6 (>= 2.2.1), libfribidi0 (>= 0.19.2), libgcc1 (>=
         1:4.1.1), libgl1-mesa-glx | libgl1, libqtcore4 (>= 4:4.7.0~beta1),
         libqtgui4 (>= 4:4.5.3), libsdl-image1.2 (>= 1.2.10), libsdl1.2debian
         (>= 1.2.10-1), libstdc++6 (>= 4.5), libtar, libva-x11-1, libva1,
         libvlccore4 (>= 1.1.0), libx11-6, libx11-xcb1, libxcb-keysyms1 (>=
         0.3.6), libxcb-randr0 (>= 1.1), libxcb-shm0, libxcb-xv0 (>= 1.2),
         libxcb1, libxext6, libxpm4, zlib1g (>= 1:1.2.3.3.dfsg)
Recommends: vlc-plugin-notify (= 1.1.9-1ubuntu1), vlc-plugin-pulse (=
            1.1.9-1ubuntu1), xdg-utils
Suggests: mozilla-plugin-vlc, videolan-doc
Breaks: vlc-nox (< 1.1.5-1)
Replaces: vlc-nox (< 1.1.5-1)
Provides: mp3-decoder
Description: multimedia player and streamer
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4, DivX,
 MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia streams
 from various network sources. 
 
 VLC can also be used as a streaming server that duplicates the stream it reads
 and multicasts them through the network to other clients, or serves them
 through HTTP. 
 
 VLC has support for on-the-fly transcoding of audio and video formats, either
 for broadcasting purposes or for movie format transformations. Support for most
 output methods is provided by this package, but features can be added by
 installing additional audio plugins (vlc-plugin-pulse, vlc-plugin-sdl) or video
 plugins (vlc-plugin-sdl, vlc-plugin-ggi, vlc-plugin-svgalib). There is also a
 web browser plugin in the mozilla-plugin-vlc package.
Homepage: http://www.videolan.org/vlc/
```

---

### Post by flipper T on 2011-04-17
go to your home folder

press ctrl h to display hidden folders

go to .neverball/replays

put nbr files in there

start neverball

view replays

---

### Post by apochry on 2011-04-17
Right click the .nbr replay file, select 'Open With Other Application...', click 'Use a custom command', type "neverball" in the field and hit Return (Enter). Voila!

A friendly tip: I don't think this is  a good way do go in the ubuntu forums. You have to provide detailed information, be kind and patient. Than you can expect a good answer. You don't have to feel silly, no one is born with Linux/Computer knowledge, but you'll have to learn lots of things. Not everything in Linux is done by clicking. There is answer to most of the questions you'll ever come up with in the forums, you need just to read.  Try to read more before writing.

Best regards
Izzo

---

### Post by PCaddicted on 2011-04-18
Thank you very much,flipper t and apochry.

---

