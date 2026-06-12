---
title: "totem mozilla plugin  wont play these mp4 files"
date: 2009-11-26
forum: General Help
---

### Post by sdowney717 on 2009-11-26
totem will play if you download first
but it should play in the browser, how to fix this?
[http://feeds.cbsnews.com/podcast_eveningnews_video_1/?tag=contentMain%3bcontentBody/](http://feeds.cbsnews.com/podcast_eveningnews_video_1/?tag=contentMain%3bcontentBody/)
feeds.cbsnews.com/podcast_eveningnews_video_1/?tag=contentMain%3bcontentBody/

it plays these fine
[http://feeds.pbs.org/pbs/frontlineworld/](http://feeds.pbs.org/pbs/frontlineworld/)

from about:plugins
> QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.28.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v

---

### Post by andrew.46 on 2009-11-26
Hi sdowney717,

Looks like the gecko-mediaplayer plugin plays these files ok, I attach a screenshot.

Andrew

---

### Post by sdowney717 on 2009-11-26
Great! it does work.
nice to see it, downloading is a pain. streaming is much better

what is interesting is I left the totem mozilla plugin and added gecko. totem still plays the frontline and gecko the cbs news

---

### Post by sdowney717 on 2009-11-26
well it is not working for some of the pbs files. gecko will cache all the way to 100% and they never play.

Any ideas on what is happening?

this is really hit and miss here.
for example the first one in the list plays, the second one will not, the cache keeps filling up even to 100% but never starts playing
I found that some will play some wont and what is the difference??
[http://feeds.pbs.org/pbs/wgbh/nova-video/](http://feeds.pbs.org/pbs/wgbh/nova-video/)

for example
student of physics and rocks will play
hunt for alien earths wont play

I can download the ones that wont play in a browser and they play fine with totem, vlc, gecko media player

---

### Post by sdowney717 on 2009-11-26
Even Banshee cant play these files without downloading
for example load the nova podcast into banshee
click the 'hunt for alien earths' and it will skip by it placing an 'x' 
it will then play the next one in the list. The only way it can play is banshee has to download the file.

interesting annoyance that banshee and gecko mozilla and totem mozilla can not play these files directly.

---

### Post by sdowney717 on 2009-11-26
screenshot shows the 'x'

---

### Post by sdowney717 on 2009-11-26
I downloaded some of these and looking at the av properties. the ones that dont play are 30 frames/sec 320 x 180
do play are 15 frames/sec

so is this a bug?

---

### Post by andrew.46 on 2009-11-26
Hi sdowney,

> **sdowney717 said:**
> hunt for alien earths wont play

I can certainly reproduce the problems you mention where this one in particular will not play properly in a browser with the gecko-mediaplayer but also will not play directly with vlc 1.0.3. My old friend MPlayer had no such trouble though. Try the following on your own system:
```

mplayer -cache 2048 'http://feeds.pbs.org/~r/pbs/wgbh/nova-video/~5/2D0HMNc3GUg/nsn_v_segment_alienearths.m4v'
```

I am not sure what the explanation is here but I note that MPlayer had no trouble playing these streams directly rather than downloading them... Perhaps you might be on the money with the different quality of the broadcasts?

Andrew

---

### Post by mc4man on 2009-11-27
If seems ( though didn't ck. all) that the ones that are "segments" need to be fully cached before playback begins.( takes about 20 secs here

If you give gnome-mplayer a min cache parameter in it's settings it attempts playback at that point but fails to start video and goes on caching.

While I guess you can have both the gecko and totem plugins installed I think you'll find the totem one overrides the gecko one in most cases.

---

### Post by sdowney717 on 2009-11-27
yes i can also play it with mplayer, but most people using ubuntu or the internet will just want to click on a link and have it just play. Having it not follow the expected behavior leads to the thinking 'linux does not work' etc...

how can we get this fixed properly?

---

### Post by andrew.46 on 2009-11-27
Hi sdowney,

> **sdowney717 said:**
> how can we get this fixed properly?

I would suggest write it up as a bug on the gecko mediaplayer issue tracker or approach the creator of the software [here]("http://groups.google.com/group/gecko-mediaplayer?pli=1"). He seems fairly approachable...

Andrew

---

### Post by sdowney717 on 2009-11-27
thanks i sent it in.

to submit bug reports in terminal type like this
ubuntu-bug gecko-mediaplayer

---

### Post by sdowney717 on 2009-11-27
[https://bugs.launchpad.net/ubuntu/+source/gecko-mediaplayer/+bug/489191](https://bugs.launchpad.net/ubuntu/+source/gecko-mediaplayer/+bug/489191)
so what does he mean by 


> Cesare Tirabassi  wrote 1 hour ago:  	  #2

Fixed by commit r195:

[http://code.google.com/p/gnome-mplayer/source/detail?r=1595](http://code.google.com/p/gnome-mplayer/source/detail?r=1595)
Changed in gecko-mediaplayer (Ubuntu):
status: 	New &#8594; Fix Committed
Cesare Tirabassi 1 hour ago
Changed in gnome-mplayer (Ubuntu):
status: 	New &#8594; Fix Committed
Cesare Tirabassi 1 hour ago
Changed in gecko-mediaplayer (Ubuntu):
status: 	Fix Committed &#8594; Invalid 

---

### Post by andrew.46 on 2009-11-27
Hi sdowney717,

The gentleman who responded to your bug report is the GNOME MPlayer packager for Ubuntu and he obviously has a connection of some sort with the developer. I built the revised source from svn and I have to admit on my setup it made no difference on that particular file. Perhaps mc4man might have time to try as well?

All the best,

Andrew

---

### Post by mc4man on 2009-11-27
Just to reiterate, if you have the totem plugin installed then that's what is used on the pbs site, not the gecko one.

 totem plays the 'non segment' ones immediately, doesn't play the segment ones at all

The commit was to gnome-mplayer so with a new one installed (-r 1596) and using the gecko plugin, in a browser window...

The non-segment ones play almost immediately, about 3 sec delay for minor buffering

The segment ones play but have to be fully buffered - after about 3 secs playback is attempted, fails, shows 'idle', then starts buffering again. Playback starts when the cache fill reaches 100% (about 30 secs here

And as noted mplayer from cli plays them all, vlc plays the non segment, only plays the segment ones in spurts of buffer size ( I still think vlc 1.0.X has issues with http caching, though 1.0.3 seems a little better, emphasis on little

---

