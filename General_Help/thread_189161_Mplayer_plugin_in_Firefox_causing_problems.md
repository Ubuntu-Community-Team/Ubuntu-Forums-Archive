---
title: "Mplayer plugin in Firefox causing problems"
date: 2006-06-04
forum: General Help
---

### Post by sweeper on 2006-06-04
I listen to BBC radio online but Realplayer was causing Firefox to go very slow so I am using Mplayer instead, but now if I try to download an rpm file Mplayer opens and so I cannot download the file in the normal way, any way around this please?

---

### Post by cwmaxson on 2006-06-05
If you go to firefox and type <about:plugins> sorry, the smiley should actually be a colonP in the address bar you should be able to see all of your plugins.  Usually plugins work in the order they appear.  I'm gueesing yours goes something like this:
mplayer...
shockwave or something...
Helix or real or something...
javaish...

I found that simply removing real/helix completely (from synaptic), then reinstalling it changes the order like so:
realish
mplayer
shockwave
java

So you see, the order matters.  There might be a better way to go about it, but I didn't feel like finding out.

Hope that helps.

---

### Post by zba78 on 2006-06-05
Funny but I find that Mplayerplug-in also makes my firefox/swiftfox run very slowly when listening to BBC radio online.

As for the RPM issue, you could right-click on the link to the RPM and select **Save Lin_k_ As...**

---

### Post by sweeper on 2006-06-05
It s Realplayer that causes it to run slow not Mplayer, I removed the realplayer plugins from the Firefox folder but about:plugins shows Realplayer is still there. As you suggest Zba I can just right click for now.

Also I cannot remove realplayer for some reason.

---

