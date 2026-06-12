---
title: "Can Mplayer plugin stream MP3 podcast files?"
date: 2006-01-23
forum: General Help
---

### Post by Yleeyas on 2006-01-23
Hello all,

O/S: Ubuntu Breezy (5.10)
S/W Firefox 1.5
Mplayer, and Mplayer plugin for FF

When I try to listen to a podcast (MP3 format), by selecting an RSS feed in my Firefox live bookmarks, the Mplayer plugin starts to buffer the d/l, but when it starts playing it the d/l seems to stop at about 3 minutes worth of playtime. These podcasts are normally over 1 hour long.
If I d/l the file to disk and start the full Mplayer (Applications>Sound and Video>Mplayer) the whole 1hr podcast is there.

Is there a way to get the Mplayer plugin to 'stream' the whole MP3 file?:?: :confused:

TIA
Yleeyas

---

### Post by ice60 on 2006-01-24
[QUOTE=Yleeyas]Hello all,

O/S: Ubuntu Breezy (5.10)
S/W Firefox 1.5
Mplayer, and Mplayer plugin for FF

When I try to listen to a podcast (MP3 format), by selecting an RSS feed in my Firefox live bookmarks, the Mplayer plugin starts to buffer the d/l, but when it starts playing it the d/l seems to stop at about 3 minutes worth of playtime. These podcasts are normally over 1 hour long.
If I d/l the file to disk and start the full Mplayer (Applications>Sound and Video>Mplayer) the whole 1hr podcast is there.

Is there a way to get the Mplayer plugin to 'stream' the whole MP3 file?:?: :confused:

TIA
Yleeyas[/QUOTE]
hi, i don't use Firefox or Mplayer :rolleyes:  but i have used about 6/7 different players to listen to various podcasts/mp3's and i always do it manually - copy the address to the clipboard then tell the player to play/stream the url.  

so you should be able to do it manually at least til you work out how to do it automatically. if you can't do it with Mplayer, which i doubt, you can open Totem>Movie>Open Location and put the url there to stream it.

of course this all depends on your connection being fast enough to stream the audio,  dialup may be abit too slow.

---

### Post by Yleeyas on 2006-01-24
Hello ice60,

Thanx for your attention to this problem.

I have been just downloading the whole podcast, using Mplayer (full mode) to listen, but I'd like to determine if there's a way to get the Mplayer plugin to stream within FF, it's just more convenient. I don't mind doing the 'manual' bit or even using Totem, as you suggested, but I'd like to figure out why the Mplayer plugin **isn't** doing it.;) 

Thanx again

Yleeyas

---

### Post by ice60 on 2006-01-25
hi, i just thought - have you installed mozplugger? it's in synaptic.
> Plugin allowing external viewers to be launched inside Mozilla
mozplugger allows you to seamlessly integrate external applications
to view files downloaded from the web that Mozilla can not normally
handle. The application is embedded within a Mozilla window as to act
like and feel like a true plugin.

i use it too because it works for Opera.

**[color=blue]EDIT[/color]** i just re-read the blurb and it's about viewing not listening :(  it might help though

---

### Post by Yleeyas on 2006-01-25
Hello again ice60,

I'll have a look at mozplug, but it sounds like it's for applications which don't have a native mode plugin for Moz/FF. My problem really is that there's a plugin but it's not functioning (streaming) like I think it should be.

By the way, I tried using Totem for streaming, and found that I had to download a gstreamer 'helper' before it would work. This didn't help my FF problem though. 

Oh well, I'll sort this out yet;) 

Thanx again,

Yleeyas

---

