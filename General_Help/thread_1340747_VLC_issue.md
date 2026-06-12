---
title: "VLC issue"
date: 2009-11-28
forum: General Help
---

### Post by mattwren88 on 2009-11-28
Recently my VLC player plays audio but the video is absent. It's like the video disappears whenever I try to watch something. How can I bring the video back? It's my favorite player. I already tried uninstalling and an reinstalling it. Any ideas?

---

### Post by andrew.46 on 2009-11-29
Hi mattwren,

> **mattwren88 said:**
> Recently my VLC player plays audio but the video is absent. It's like the video disappears whenever I try to watch something.

I suspect that you need to have a look at the video out settings in vlc:

Tools --> Preferences --> Video --> Output

and select a different video out device.

All the best,

Andrew

---

### Post by Z06Gal on 2009-11-30
I am having the same problem and changing the video settings hasn't resolved it.  I just cannot figure it out.  All my other players work fine but of course the one I like the most doesn't.  Lol.

---

### Post by mc4man on 2009-11-30
Run this to reset vlc back to install defaults and see if you get video. (you may need to set the audio output back to pulse 

```
vlc --reset-config --reset-plugins-cache
```

If still  no good then it's something other than vlc itself

.........................................

( the default qt4 gui settings in 9.10 aren't the best for vlc (though shouldn't prevent video display

To change install this, then found in system ->  preferences

The best gui for vlc is clearlooks, (no default, no gtk
```
sudo apt-get install qt4-qtconfig
```

---

### Post by Z06Gal on 2009-11-30
> **mc4man said:**
> Run this to reset vlc back to install defaults and see if you get video. (you may need to set the audio output back to pulse 

```
vlc --reset-config --reset-plugins-cache
```

If still  no good then it's something other than vlc itself

.........................................

( the default qt4 gui settings in 9.10 aren't the best for vlc (though shouldn't prevent video display

To change install this, then found in system ->  preferences

The best gui for vlc is clearlooks, (no default, no gtk
```
sudo apt-get install qt4-qtconfig
```


This is the oddest thing I've ever seen.  The player audio is great and the frame comes up but the area where the video should be is the desktop background or whatever page I am on when I open it to play something.  It's like it is transparent and I have tried everything I have found on this forum.  It worked prior to my downloading winff, handbrake, and avidemux to convert videos.  Is there a conflict with one of these programs?  My other players work fine - no issues at all.

---

### Post by mc4man on 2009-11-30
Does seem 'odd', like your getting no rendering at all.

> It worked prior...
Offhand can't see any issue there, one's a frontend and the other 2 are somewhat self contained. 

Maybe run vlc verbose and try video, (output will be large

```
vlc -vvv
```
or if easier to read back thru ( find in home folder
```
 vlc -vvv > vlc.log 2>&1
```


What happens if you disable the embedded video in interface?


Edit: do you have Cairo-dock installed?

---

### Post by Z06Gal on 2009-11-30
> **mc4man said:**
> Does seem 'odd', like your getting no rendering at all.


Offhand can't see any issue there, one's a frontend and the other 2 are somewhat self contained. 

Maybe run vlc verbose and try video, (output will be large

```
vlc -vvv
```
or if easier to read back thru ( find in home folder
```
 vlc -vvv > vlc.log 2>&1
```


What happens if you disable the embedded video in interface?


Edit: do you have Cairo-dock installed?


I posted on the other thread but will here too.  Disabling the embedded video fixed it.  I do have the cairo dock installed but had not thought of that.  I have always had the embedded video disabled and don't know what I did to change it but it is fixed now which is the main thing.  Thanks alot. ;)

---

### Post by mc4man on 2009-11-30
The cairo dock can interfere with vlc output, if you ever want the embedded then that can be fixed.

Having separate isn't a big deal anyway, also for vlc 1.0.X  - vlc remembers the last position of the interface so one could position it  in an appropriate place for non full-screen playback.

---

