---
title: "MKV Files, Mplayer and Linux"
date: 2011-06-05
forum: General Help
---

### Post by ak4allz on 2011-06-05
Facing this problem:
-The Mkv video file cannot be opened by the Mplayer due to something that I don't know. I try to open it via the gnome-terminal and end up with something like this:

[IMG]http://i.imgur.com/TyIlQ.jpg[/IMG]

The, I try to play it with VLC media player. Everthing seems fine but after few minutes, I can see the lagging of the video and distractions on the screen.

Then, I've open my Windows 7 and play the mkv files with the KMplayer, everything is fine. No lagging, no distractions.

I've already updated the ubuntu-restricted-extras and nothing could help me. I've already installed the libxine1-ffmpeg and nothings good appeared. 

I've already installed the mkvtoolnix-gui (which is i don't know what is it) but similar prob appear.

So, how did u guys play mkv files? With no lags or disctractions? Tell me~

---

### Post by SeijiSensei on 2011-06-05
Stock mplayer from the repos has problems with some types of H.264 encodes.  These days I'm using mplayer2 which I built from source.  You can give that a try by following my instructions in [this post]("http://ubuntuforums.org/showpost.php?p=10841681&postcount=5").

You might also take a look at [this thread](http://ubuntuforums.org/showthread.php?t=1747753) where someone has similar problems to yours.

---

