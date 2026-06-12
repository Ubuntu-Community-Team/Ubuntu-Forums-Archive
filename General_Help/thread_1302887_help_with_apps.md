---
title: "help with apps"
date: 2009-10-27
forum: General Help
---

### Post by bds28338 on 2009-10-27
I just recently switched over to Ubuntu in the past few days and I've been looking for all the applications I'll need, I have mostly everything installed and running correctly, though I need a few suggestions and help with a couple apps.

FireFox - once Ubuntu 9.10 comes out FireFox will update to the newer with Update Manager?

Movie Player - anyone had any problems with Movie Player not playing certain media or is it pretty well done?

MultiGet - only good looking download manager I could find that has multithreads per download and pausing. Any other good download managers?

Wine - Wine runs Windows programs directly correct? While virtual machines run Windows first and then run the program inside Windows?

DICTIONARY/THESAURUS - I'm still looking for a combination dictionary/thesaurus which I can use without being connected to the net. Suggestions?
-------------------------------------------------------------------------------------------------------
the most important thing I'm having trouble with is my music related programs. I'm OCD about my music collection and I'm having a hard time finding programs to do all the things I need, I'm thinking of just using Windows/iTunes for my music, but I really just want to stick to Ubuntu.

AAC ENCODER - I need a program that can encode MP3s that I download into AAC format at 128bitrate, I also haven't found any programs that play music AND encode.

gtkpod - I mostly was looking into this because of the volume normalization, but I tried it and it didn't work so great. When playing my iPod through headphones it's fine, but if I play through a line in or FM transmitter, certain CDs are extremely loud to the point that I have to turn the volume down by three quarters. Why is that? When the music was transferred to digital I'm assuming it was recorded at extremely high DBs versus most other CDs? Is there a program to peramenantly change all my musics DB levels to a certain level?

rhythmbox - well, I need an audio player, but I was hoping to find one with the AAC encoding and volume normalization, and also ipod integration, rhythmbox does work fine with my 2nd Gen Nano though. I also liked having the cover view in iTunes where you could scroll through your CDs by album artwork.

---

### Post by bds28338 on 2009-10-27
*bump*

---

### Post by oldos2er on 2009-10-27
Install libfaac0 to enable aac. Mplayer should work fine as long as you have the proper video and audio codecs. Most of the codecs are available in the package ubuntu-restricted-extras.

 Which version of Firefox are you interested in? The latest one available on 9.04 is 3.5.3.

---

### Post by bds28338 on 2009-10-28
I'm not particularly interested in any version of FireFox, the one I have installed right now is fine. I just want to know if I leave the update manager to itself, if FireFox will ever update through it.

---

### Post by 3rdalbum on 2009-10-28
> **bds28338 said:**
> I'm not particularly interested in any version of FireFox, the one I have installed right now is fine. I just want to know if I leave the update manager to itself, if FireFox will ever update through it.

Firefox will get security updates, but not major updates. The only time it will get a major new version update is if you have added a PPA that contains it, or if you actually upgrade to a later version of Ubuntu.

Totem Movie Player can't play absolutely everything; you might want to try VLC for those very stubborn files.

Yes, Wine does run Windows programs directly, through some reverse-engineered DLLs that convert Windows system calls into Linux system calls. It's not perfect; far from it. Wine is a last resort, but it can sometimes get you out of a pickle :-)

Sound Converter can convert existing audio files, and I think it can convert to AAC format too. I don't know of any music players on Linux that can do file conversion, but then there are probably a hundred music players on Linux :-)

---

