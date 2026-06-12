---
title: "Yahoo Embedded Video"
date: 2006-06-27
forum: General Help
---

### Post by mustang on 2006-06-27
Does yahoo embedded video work for anyone?

Without the MediaPlayerConnectivity extension, mplayer hangs at "Getting Playlist...". If I right click and go to play, it "plays null" and then "stops".

With the extension, I get some failed to open error. 

Here's a test link:

[http://fifaworldcup.yahoo.com/06/en/w/highlights.html](http://fifaworldcup.yahoo.com/06/en/w/highlights.html)

click on "match highlights"

---

### Post by mustang on 2006-06-28
*bump*

---

### Post by dmizer on 2006-06-28
i had this working about a month ago, but it doesn't work now.  not sure why, as i really haven't done any changes to the system other than regular updates.

also, i can't get yahoo news video to play in my fc5 install either.

so now, no yahoo video in either breezy xubuntu, dapper xubuntu, or fc5 gnome.
all using mplayer. i also have a machine i'm playing with right now that has dapper xubuntu and totem, but it can't play yahoo video either ... either using gstreamer or xine.

can anyone get the yahoo imbeded video to work?

---

### Post by srt4play on 2006-06-28
Works fine here..  Ubuntu 6.06 using mozilla mplayer plugin in Firefox.

---

### Post by mustang on 2006-06-29
[QUOTE=srt4play]Works fine here..  Ubuntu 6.06 using mozilla mplayer plugin in Firefox.[/QUOTE]

Very strange. Did you configure any special settings?

---

### Post by detectiveinspekta on 2006-07-07
Works here

BBC world videos doesn't work, opens up 3 mplayers in where 1 player is supposed to go, ifilm doesn't work either except when you change to quicktime video. I'v come across few streaming videos that acually work.

---

### Post by maspiotis on 2006-07-31
I have the same problem, I have the latest version of automatix and gxine and  
can't get yahoo new clips to play or any of their free music videos on launch cast.  

I have 6.06

Thanks
Michael Aspiotis

---

### Post by emperor on 2006-09-01
In the processes up uninstalling blackdown java and installing sun's java5 plugin  I had to delete "~/.mozilla/firefox/pluginreg.dat" to get the libjavaplugin to register. Afterwards I found that Yahoo's Video On-demand" worked with the mplayer-plugin for the first time in awhile. So, you might try it and see if it fixes yours too!  (I am assuming that you already have the w32codecs installed.)

---

### Post by viciouslime on 2006-09-02
> **detectiveinspekta said:**
> Works here

BBC world videos doesn't work, opens up 3 mplayers in where 1 player is supposed to go, ifilm doesn't work either except when you change to quicktime video. I'v come across few streaming videos that acually work.

Ditto. With the BBC videos though, you can right click on the 2nd and 3rd one and select pause, then watch the first. Annoying, but better than nothing...

---

### Post by H.E. Pennypacker on 2006-09-16
Use the following instructions to get Launch working:

Why do all this when you can follow the following instructions:

1.  Install Greasemonkey.
2.  Install [http://www.pooyak.com/p/pklaunch/pklaunch-0.8.1.user.js](http://www.pooyak.com/p/pklaunch/pklaunch-0.8.1.user.js).  Just click on the link, and Greasemonkey will know what to do, and will ask you if you want to install it.  Install it.
3.  Go to Launch.com, and watch any video.

I am telling Yahoo to play nice or people will look for alternatives.  They should be flattered we're using their website.

Thanks go to this website:

[http://buhsnarf.net/wordpress/2006/01/06/howto-play-launchcom-music-videos-in-firefox/](http://buhsnarf.net/wordpress/2006/01/06/howto-play-launchcom-music-videos-in-firefox/)

Note these instructions may only work for certain version of Firefox.  Try anyway.

---

### Post by emperor on 2006-09-18
> **H.E. Pennypacker said:**
> Use the following instructions to get Launch working: ... 

Thanks, Launch now works on all my Dapper's!

---

### Post by jmullagh on 2006-09-19
Fantastic...works great... Thank You!

---

