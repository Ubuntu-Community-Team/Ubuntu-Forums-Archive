---
title: "Mozilla-mplayer plugins dosn't work as it should be"
date: 2009-09-13
forum: General Help
---

### Post by gawadelnil2002 on 2009-09-13
Hey guys
           After 3 weeks of using Windows xp I felt that I have to give kubuntu another chance for me.
I downloaded the alternative amd64bit cd and (i used before the normal live cd) , and i installed it
I had alot of problems (like pulseaudio installed, codecs and another) all are solved. but i have one left I don't how to solve it and really I googled alot but with no solution.
Its mplayer plugins it was craching firefox 3 and i solved that by installing firefox 3.5 using this command ( sudo apt-get --no-install-recommends install firefox-3.5 ) but another problem appeared, when i try to listen to radio streaming on that page [http://nogoomfm.blogspot.com/2007/09/nogoom-fm_20.html]("http://nogoomfm.blogspot.com/2007/09/nogoom-fm_20.html") it works great but when I go down or up in the page the sound stop then plays again if I go back to the area contain the player in the web page. 
I don't know maybe its feature in mplayer plugins so no one considered it as a problem before specially I did not find any thread talks about that during my googling

---

### Post by gawadelnil2002 on 2009-09-13
Any help??????????

---

### Post by ajgreeny on 2009-09-13
Try gecko-mediaplayer instead of mozilla-mplayer as your plugin.  I use gnome ubuntu and the mozilla-mplayer always crashed on me in 9.04, taking firefox with it.  The change to the gecko-mediaplayer plugin solved all that.  It may help your problem as well.

---

### Post by gawadelnil2002 on 2009-09-14
> **ajgreeny said:**
> Try gecko-mediaplayer instead of mozilla-mplayer as your plugin.  I use gnome ubuntu and the mozilla-mplayer always crashed on me in 9.04, taking firefox with it.  The change to the gecko-mediaplayer plugin solved all that.  It may help your problem as well.

I'm using kubuntu and if I install gecko-mediaplayer it will install (gconf2 gconf2-common gecko-mediaplayer gnome-mplayer libdiscid0
  libgconf2-4 libglade2-0 libidl0 libmusicbrainz3-6 libneon27-gnutls
  libnotify1 liborbit2 libsexy2 libstartup-notification0 libwnck-common
  libwnck22 libxres1 notification-daemon) all is gnome packages

if any one know good mplayer-firefox plugins he should tell me

---

### Post by gawadelnil2002 on 2009-09-15
Hey I figured out to solve that, it was feature in mplayer plugins just go any video on web using mplayer plugins like this video_ _[http://media.railscasts.com/videos/067_restful_authentication.mov](http://media.railscasts.com/videos/067_restful_authentication.mov) then right click on the video and choose configure and then untick the mark beside (pause video when hidden) ,I was stupid that i didnt discover that

---

