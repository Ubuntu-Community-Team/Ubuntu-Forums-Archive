---
title: "Remember window positions and sizes."
date: 2009-10-29
forum: General Help
---

### Post by t.rei on 2009-10-29
Hello.

I am well aware of the decision not to let window-managers be responsible for something like "remember position and size of an application." and "Applications are the ones that should remember their properties.".  That was a couple of years ago, I think.

Kwin on kde 3.5 was the last "system" that worked like it was supposed to regarding this as far as I can tell. But nowadays neither gnome not kde, be it metacity, compiz or kwin, provide such a feature.

The applications seem to "not give a ...". :( 

So. How do I enable this?

I am not talking about "he or she should implement it." How do I turn this on, implement it for compiz or who needs to get bugged so: kwrite, konsole, kontact, gedit, firefox, chatwindows, and all the other programs behave the way I (and maybe some other folks, too) want them to. *g*

One thing: is there a funcionality in the compiz or kwin or kde system that works like.
WindowPlacementSystem->Remember("Konsole", Pos, Geometry)
WindowPlacementSystem->Recall("Konsole").Pos / .Geometry

Or is something to assist the application writers not yet existent? 
Best thing would probably be if it was completely desktop independant, so it would work even if desktop-managers are switched. Probably - since this is "per user" a simple plain-text-db in ~. 

Hm, sounds so simple I need to check if a compiz plugin exists (currently I am using kde4.3 and compiz).

If anyone can provide any pointers, I'd be happy to listen.
I'm this *shows about a millimeter with thumb and index-finger* far away from a perfect desktop. ;)

---

### Post by tlacuache on 2009-10-29
You could check out "Devil's Pie," which I believe will do this for you.

See [http://burtonini.com/blog/computers/devilspie/](http://burtonini.com/blog/computers/devilspie/) or [http://ubuntuforums.org/showthread.php?t=75749t](http://ubuntuforums.org/showthread.php?t=75749t) for more information.

I haven't used it myself, but I've read that it will do all sorts of window-matching stuff, remember positions, desktops, etc.

---

### Post by t.rei on 2009-10-29
That seems to be a workaround. Still testing. However I do not want to have my windows positions fixed. I want to be able to move them around and close them and reopen them where they were.

So I guess I need to get to where the windows are closed and save the position and size and then get to where they are opened and recall this.

But thanks.

---

