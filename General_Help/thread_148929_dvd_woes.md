---
title: "dvd woes"
date: 2006-03-22
forum: General Help
---

### Post by chocolatetoothpaste on 2006-03-22
I am in need of some help.  I want to watch a movie on my computer, but nothing seems to work. Ogle pretends to open the dvd, then kills.  Totem, well it is worthless.  Mplayer gave me troubles too.  I searched the forums, and it seems like no one has had this problem.  Help someone.

---

### Post by chocolatetoothpaste on 2006-03-23
I got the dvd playback to work now, but my screen is really small.  Even when I switch to fullscreen, it just turns all the screen black, and leaves a little box in the middle for  the movies.  I am using mplayer by the way.  Anyone else had this?

---

### Post by rattking on 2006-03-23
what -vo are you using for mplayer? 
i find -vo xv to be the best for my nvidia card
mplayer -vo help 
for a full list of video out's compiled into your mplayer
try a few and see if that helps
if it does then make it default in 
~/.mplayer/config 
vo=whatever

ps for dvd menus I usually use vlc

---

### Post by trent dillman on 2006-03-23
The best player I've found for dvds is xine, using libdvdcss (shhh, don't tell anyone my box is 'illegal' :-D)

---

### Post by taurus on 2006-03-23
Or run this from a terminal
```

echo "zoom=yes" >> ~/.mplayer/config

```

---

### Post by charleyramm on 2006-03-23
I just spent an hour or so trying to get DVD playback working on my box. I had installed mPlayer, gXine and all sorts of crap. Then I installed Ogle, and I finally got a sensible error message. The problem was, I didn't have libdvdcss. I ran ```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
``` Now my gigantic  collection of DVD Movie players all work perfectly. What a pain in the bum!

---

