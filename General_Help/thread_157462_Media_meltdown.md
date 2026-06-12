---
title: "Media meltdown"
date: 2006-04-09
forum: General Help
---

### Post by Carandol on 2006-04-09
I'm a new user to Ubuntu, and had got everything working nicely (Breezy Badger), up to the point where I wanted to get DVDs playing. I followed all the instructions on the media players page, and the restricted formats page. At the end of which Totem played a DVD once. After that it loaded, but disappeared again as soon as I asked it to play a DVD. Xine, on the other hand, would play the sound, but the screen was blue. 

Looking at some threads here, I decided to use the Automatix program to install media players.  I then had *lots* of media players, none of which would run at all! They appeared and then disappeared again immediately, before I even *tried* to view anything. 

I then uninstalled everything (to the best of my knowledge and ability, anyway), and started again, re-installing via Automatix. Most of the video players now pop up and disappear as before, except Mplayer, which plays the sound but has a white screen. 

There's probably some log somewhere or other which would tell me what's going on and give me some clues over how to solve this problem, but I don't know linux well enough to know where to look. Any help appreciated.

---

### Post by takayuki on 2006-04-10
hi,

you might want to try this.  i had some video wonkiness that "fixed" itself.


1. go to System > Preferences > MultiMedia Systems Selector, then click the Video tab, then change the Default Sink Output to Custom, then close the window.

2. now try playing a video in totem or vlc. if it works, great. if it doesn't, repeat step one and try SDL or another option.


takayuki

---

### Post by Carandol on 2006-04-12
Well, that *almost* worked! Totem will now play the opening logo of a DVD in full screen, and then crashes. I suppose it's an advance... :-)

---

### Post by scotishhaggis on 2006-04-12
try installing ur grx drivers to that helped for me

---

### Post by takayuki on 2006-04-12
hmmm...  have you tried vlc?  you can download it easity via synaptic:  System > Administration > Synaptic Package Manager

have you tried multiple dvd's or just one?

---

### Post by Carandol on 2006-04-12
[QUOTE=takayuki]hmmm...  have you tried vlc?  you can download it easity via synaptic:  System > Administration > Synaptic Package Manager

have you tried multiple dvd's or just one?[/QUOTE]

I've had a go with VLC, and it *does* play DVDs, but keeps locking up (2-3 times per movie). 

However, I finally got things working properly! I did it by installing Kaffeine, and setting the Player Engine to Kaffeine in the Settings menu. I then selected xine Engine Parameters in the Settings menu, then set the Audio Driver to esd and the Video Driver to xshm. It now works perfectly. I suggest this might be worth trying for others stuggling with DVD playback, since there are more options available in Kaffeine than in the 
Gnome Systems/Preferences/Multimedia Systems Selector option.

---

