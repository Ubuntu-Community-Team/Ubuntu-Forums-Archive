---
title: "No windows media player plug-in with gecko?"
date: 2009-08-20
forum: General Help
---

### Post by Truckerpunk on 2009-08-20
I had Gecko-mediaplayer installed and everything concerning media playback in firefox worked like a charm, but yesterday it stopped playing windows media player files. So I checked my installed plug-ins in firefox, and the windows media player plug-in for gecko was missing...? I tried to completely remove gecko-mediaplayer through synaptic, abd reinstalling it multiple times but it never installs the windows media plug-in. I have the other ones (DivX, Quicktime and Realplayer plugins) installed with gecko, but just not the windows media player plugin. What could be wrong here?

---

### Post by NESFreak on 2009-08-21
wow dude your posts are all over the forum. take it easy.

Anyway to fix it just remove/rename  ~/.mozilla/firefox/*.default/pluginreg.dat

(and restart firefox)

---

### Post by Truckerpunk on 2009-08-27
Sorry for multi-posting... (I know 3 posts)... But I really like the Gecko-mediaplayer, it's the only player I found that actually works flawlessly with every other plug-in and media-type. 

Your solution worked perfectly!! Thanks a bunch. It keep on doing it, so your help is really appreciated. ( I think it often after I install updates, but I'm not sure). Anyways, this works great, and I'm sure I'll return to this post again and again until I remberhow to fix it. 

Thanks again mate.

---

### Post by NESFreak on 2009-08-29
So are you saying it breaks every time a firefox plugin updates? or only whenever a new version of firefox is installed?

because if it breaks after one update id forgive it the piece of software (which it actually did once, after a firefox update through the ubuntu update manager). But if it would happen to often i'd pay extra attention to whatever might be causing it and post a bug on the projects site:

[http://code.google.com/p/gecko-mediaplayer/issues/list](http://code.google.com/p/gecko-mediaplayer/issues/list)

Anyway great to hear it's at least a partial solution for you.

---

### Post by Truckerpunk on 2009-08-30
Yeah mate. I'll keep an extra eye on when the problem happens, and if it seem as if it's after some updates I'll submit ti to the Gecko-admins. It doesn't seem as if it's just after firefox updates... But I'll have to check for sure. Anyways thanks a bunch.. Really helped me out here.

---

### Post by Truckerpunk on 2009-09-29
I've narrowed down what causes the plug-in problem. It seems as if every time Novell Moonligt updates, the plug-ins for gecko gets messed up. Hope tihs helps others with this problem.

---

