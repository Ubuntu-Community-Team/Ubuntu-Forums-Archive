---
title: "Mplayer / Mencoder problems :("
date: 2005-02-18
forum: General Help
---

### Post by ixus_123 on 2005-02-18
I have read & used the very useful script in the Howto section of these forums but I am still having problems with Mplayer although the more pressing problems seem to be with mencoder.

I am having problems getting mplayer to detect codecs & libraries that have been installed first.  My intention is to use the fronend to Mencoder - **Acidrip**.  Previously on my Slackware box I followed the acidrip howto & compiled from source with lame & ogg support.  Mencoder doesn't seem to want to find lame when configured in Ubuntu.  Ogg support isn't there either.

I've tried installing mplayer from source & then lsdvd & acidrip also from source & again on a clean install & selecting acidrip from the nerim repositories & letting it install Mplayer & mencoder custom with no joy again.

If someone would like to do a 'howto for dummies' on this I would be most grateful.  Otherwise I'm just going to have to dual boot back into slackware to backup my DVDs :(

Also if anyone has a list of every codec etc you should install before compiling mplayer to get a fully featred version I'd also be grateful for a link.  You know, things like oggvorbis, lame, mjpeg, etc etc

Thanks in advance

---

### Post by WillCooke on 2005-02-18
The way I solved *most* of my codec problems was to copy the w(in)32codecs to, I think, /etc/mplayer, or maybe it was /etc/codecs, I can't remember, I'll check when I get home.... But, the way I solved things like lame etc was to look in the configure.log that get's generated when you run ./configure.

In here you can see how the script works out what is and is not installed, then make sure you position things like lame libs in the place it expects to find it.
(Lame & ogg lib's are installable from apt, to save you building them)

---

### Post by ixus_123 on 2005-02-18
I've installed lame from apt but mencoder decides it doewn't want to use it, not in the acidrip front end at least.

I have also got w32codecs & the mplayer essential codec.  I'm going to try on another machine to see if its just some weird debian thing on this AMD

---

