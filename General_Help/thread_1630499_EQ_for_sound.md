---
title: "EQ for sound"
date: 2010-11-25
forum: General Help
---

### Post by then_dude on 2010-11-25
hello,

i'm looking for a very good EQ, with a lot of bands, that i can use for all my audio applications in ubuntu.

some people told me that i should look at 

AiXcoustic Creations: Electri-Q - posihfopit

what do you think of it, but most of all, how do i install this software : the aixcoustic one? 

thanks 
**[]("http://www.aixcoustic.com/index.php/Electri-Q-posihfopit/30/0/")**

---

### Post by lykeion on 2010-11-25
You are aware that the software you mention is a plugin for WinAmp/VST? You can't use this plugin for audio applications in Ubuntu.
What you can do in Ubuntu is to use a system-wide equalizer for PulseAudio. The procedure to install it is described here: [http://exploreubuntu.wordpress.com/2010/04/18/equalizer-for-pulse-audio/](http://exploreubuntu.wordpress.com/2010/04/18/equalizer-for-pulse-audio/)

---

### Post by then_dude on 2010-11-25
thanks a lot

no i wasn't aware of it, but that is the reason why i could find anything about an ubuntu install 

ihave looked at the link you gave me, but i'm in need for an EQ with more bands, the double amount would be great. 

thanks, i'll install this one, cause maybe there isn't one with  more bands

thanks again

---

### Post by lykeion on 2010-11-26
If you need a system-wide EQ with more bands you can use [JAMin]("http://jamin.sourceforge.net/en/about.html"). 
You'll need to install [JACK]("http://jackaudio.org/") and then you should be able to route your audio programs through JAMin. 
Note that not all audio applications have JACK output, there's a list of compatible apps [here]("http://jackaudio.org/applications"). 
All this might be more of a hassle to setup, so the easy way out is to settle for the 15-band EQ I suggested earlier.

---

