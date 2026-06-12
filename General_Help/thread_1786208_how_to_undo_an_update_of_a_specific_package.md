---
title: "how to undo an update of a specific package?"
date: 2011-06-19
forum: General Help
---

### Post by John Krow on 2011-06-19
If one accepts an update of a specific package via apt and decides the update isn't desired, what does one do?
In other words, what is the most sensible and relatively easy way to rol-back to the previous version of that specific package without affecting anything else (dependencies aside of course).

I want to do this with a recent adobe plug in.

---

### Post by Enigmapond on 2011-06-19
One would simply go to Synaptic, search for the package and then at the top under the Packages tab, "Force Version" and install the version one wants. One may have to uninstall the current version, I'm not certain. I hope this helps.

Cheers!

---

### Post by John Krow on 2011-06-19
Thanks very much for the speedy  and helpful answer. 

> I hope this helps
It did, but not quite there yet! I thought the closed nature of this software might make thing more complex, and lo! Force version's greyed out for the package in question, which is 
adobe-flashplugin, v10.3.181.26-0lucid1

On the dependency list i notice the line 'replaces: flashplugin'. The package flashplugin-installer v10.3.181.26ubuntu0.10.04.1 is not currently installed. 
Should i try completely removing adobe-flashplugin and installing  flashplugin-installer either in it's current or previous version (which is available via the 'Force Version' item on the menu).

Thanks again, this is the kind of beginners information one really ought to know isn't it?

---

### Post by Enigmapond on 2011-06-19
I also had flash issues. Adobe is making this increasingly difficult. One of our members, lovinglinux, also a Firefox dev, came up with the Flash-Aid add-on to FF which solved all my issues, system wide. It runs a script that will scan your system and uninstall and install whatever will work best and effect it for all browsers. I would attempt this option prior as it's the easiest.
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

Cheers!

---

### Post by John Krow on 2011-06-19
That's great I'll give it a go though i might do as I suggested in #3 first. The easiest method isn't always the best (though this sounds good), and I do enjoy the whole getting your hands dirty, learning by breaking and fixing routine that's meant to be part of the ethos.  Should never have accepted that update, I usually use aptitude to update and I did get a security warning with this adobe update, quite rightly.

The only problem I've noticed with it is that I watch YouTube in the HTMl5 beta, on FF, and since this update I occasionally get a message within the video area claiming my browser doesn't recognise any of the available video formats, seconds before loading the video. I haven't noticed if this only applies to videos in the HTML5 beta, but i assume it's been put in place to annoy HTML5 users, or at least patronise them...

Hey thanks again enigmapond, good one.

---

### Post by Enigmapond on 2011-06-19
No problem. I, too, like to roll in the mud but I had quite enough when that plugin came along. I hope it helps you as well. Good Luck.

Cheers!

---

