---
title: "Android remote for rhythmbox"
date: 2011-01-10
forum: General Help
---

### Post by pieman711 on 2011-01-10
I've installed this banshee remote on my htc desire HD phone (android 2.2.1) ([http://www.dartmouth.edu/~nstamato/android.html](http://www.dartmouth.edu/~nstamato/android.html)) from the marketplace and a python script ([http://www.navarin.de/projects/rbox/](http://www.navarin.de/projects/rbox/)) to run a server on my ubuntu netbook remix 10.10 so that I play/pause/skip etc from my phone. So far so good but there was a couple more things I can't get working...
Because the phone app is designed for banshee it has a feature that lets you search the library but you have to copy the banshee.db file to the phones sdcard. What is the rythembox alternative and will I be able to get it to work? 
Also do you think it will be able to get it to work over bluetooth (so far it is working though the wifi)

Thanks in advance

---

### Post by dabbi2000 on 2011-01-22
Same here, been spending days looking for some Android/Linux combination to control music in my home, Sonos style. Been amazed how little interest the linux community has in this.

---

### Post by earthpigg on 2011-04-22
seen uremotedesktop? [http://www.guatedroid.com/?p=46](http://www.guatedroid.com/?p=46)

it isn't designed for any specific media app, just sends generic 'play', 'next track', etc, commands.

i can't speak for everything, but it works great in rhythmbox and the default ubuntu movie player.

---

### Post by pieman711 on 2011-04-29
I was using Uremotedroid for a while. It was good but now I've changed to banshee and am using the banshee remote from above. It seems good so far.

---

### Post by pieman711 on 2011-05-15
I've ben using banshee remote for a while now and it's really good with banshee (which I'm using on my desktop and notebook at the moment) I particularly like the feature that lets you choose the songs from your library to play rather than just skipping forward or back. 
For that feature to work properly you need an updated banshee.db on your phone. I was thinking about a simple script to copy it across if it gets changed maybe using dropbox to get it on my phone. 
Something along the lines of "if the banshee.db in my ~/ is newer than banshe.db in dropbox then... cp" and something similar on the phone end. 
Is there a way of using BASH to tell if one file has been modified more recently than another? Or am I going about this completly the wrong way?
Any suggestions would be appreciated!

---

### Post by earthpigg on 2011-05-15
> **pieman711 said:**
> I've ben using banshee remote for a while now and it's really good with banshee (which I'm using on my desktop and notebook at the moment) I particularly like the feature that lets you choose the songs from your library to play rather than just skipping forward or back. 
For that feature to work properly you need an updated banshee.db on your phone. I was thinking about a simple script to copy it across if it gets changed maybe using dropbox to get it on my phone. 
Something along the lines of "if the banshee.db in my ~/ is newer than banshe.db in dropbox then... cp" and something similar on the phone end. 
Is there a way of using BASH to tell if one file has been modified more recently than another? Or am I going about this completly the wrong way?
Any suggestions would be appreciated!

rsync :)

```
man rsync
```

i can't offer up an exact sample command, because that is one of those commands wherein a typo could be a very bad thing and i've only used the command a few times.

edit: here ya go [http://www.thegeekstuff.com/2010/09/rsync-command-examples/](http://www.thegeekstuff.com/2010/09/rsync-command-examples/)

---

### Post by pieman711 on 2011-05-15
Cheers. I'll get stuck in and see how I get on.

---

### Post by pieman711 on 2011-05-17
A qucik update for anyone using banshee remote...
There is a really nifty app called rsync back up for android. You have to know a bit about what you're doing (or at least be willing to learn) as it's not straight forward to set up.
It means now I can update the banshee.db file on my phone with just one click.

I've also set up a folder to back up the photos and videos on my phone to my harddrive, again with one click. Cheers for the pointer earthpigg.

--EDIT

The most recent update to Banshee remote and the plugin to banshee now supports syncing of the .db file through the app.

---

### Post by kanorhu on 2011-07-24
best android rhythmbox remote control:
[http://www.joaomak.net/projetos/rhythmote](http://www.joaomak.net/projetos/rhythmote)
just a plugin in rhythmbox, accessed via http from your android or anything else

---

### Post by nastradamus on 2011-12-05
You can try this [App (Rhythmbox remote)]("https://market.android.com/details?id=rhythmbox.view") from the market :popcorn:

---

