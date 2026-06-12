---
title: "Help finding a good decent media player"
date: 2006-02-28
forum: General Help
---

### Post by sirtigger on 2006-02-28
Hey whats up!

I'm pretty new to ubuntu linux and I am wondering what would be a good all in one media player for playing dvds, flac, ogg, wmvs, etc I was thinking about trying vlc media player?

---

### Post by lnxpwr on 2006-02-28
vlc is a good choise(works on my breezy)......give xine a try too

---

### Post by rohan! on 2006-02-28
I like vlc. Just try a load out until you find what's right for you and then uninstall what you don't want! :)

---

### Post by stalefries on 2006-02-28
Generally, I use a mix of mplayer and Totem+gstreamer. Also, Rhythmbox for music, which also uses gstreamer.

---

### Post by sirtigger on 2006-02-28
hey thanks for the info i think I'll give vlc a go and possibly xine

---

### Post by akniss on 2006-02-28
amaroK for music
xine for video

---

### Post by sirtigger on 2006-02-28
I have tried amarok 1.3 before it was nice

---

### Post by metacoola on 2006-02-28
Nothing has ever worked better for me than VLC, plays everything you need to play, and works on every OS ever

---

### Post by ohzopants on 2006-02-28
I agree with akniss.  Xine is by far the best video player I have ever used.  Pressing up to make video play faster and down to make it go slower should work in every video player.  I just wish they would make a windows version I could install on my desktop.
I have recently switched from rythmbox (which I liked) to amarok, and I love it.

---

### Post by ronmarley1 on 2006-02-28
XMMS for audio, Xine with the Totem front end for DVD, mPlayer plugin for videos imbedded in web pages (Using Firefox).

---

### Post by hugo491 on 2006-03-01
I personally love Mplayer. It works with nearly everything where Totem and Kaffeine (KDE's media player) fail. If you install the proper codecs. ([http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)) then mplayer should bring you the best media experince you could want. That includes streaming media, music, and video on your computer.

---

### Post by speedsix on 2006-03-01
No dvd menu support though unlike Xine.

---

### Post by amosbatto on 2006-03-01
I hate the Xine control panel.  I like Ogle for DVD playback, except that I haven't figured out how to display the DVD controls in Full Screen mode. Anyone know how to do that?

Also remember to enable DMA for DVD playback:

First verify that DMA is turned off:
       $ sudo hdparm /dev/hdc

If using_dma = 0 (off), then enable DMA:
       $ sudo hdparm -d1 /dev/hdc

To enable DMA at bootup, open /etc/hdparm.conf and add the following lines to the end of the file:

        /dev/hdc {
       dma = on
       }

---

