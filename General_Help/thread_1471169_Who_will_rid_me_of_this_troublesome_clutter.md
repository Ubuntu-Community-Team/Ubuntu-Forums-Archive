---
title: "Who will rid me of this troublesome clutter?"
date: 2010-05-03
forum: General Help
---

### Post by Scunnered on 2010-05-03
I have installed Lucid and in the main am reasonably happy with my lot. 

However as I have little or no inclination to use the offerings :

	[I]Set up Chat, Set up Mail & Set up Broadcast account nor all the 
	items allied to the user name on the panel[/I]

I would like to remove these as they are needless clutter.  

I note from the article in Linux Format that a number of items on the panel are clubbed. &#8220;***This being done to save space on this valuable piece of screen real estate&#8221;.  ***

 This no doubt is why when I initially removed the envelope from the panel that I lost the sound icon which I use constantly.  Similarly attempting to remove the square adjacent to the user name caused it and the logout button to disappear into space.  If space is at a premium is the day needed when displaying date and time.  Even I in my dotage normally manage to remember what day it is !

If the sound and logout icons were not linked then the space saving would be made.

Is there any way that the clutter be removed as it does nothing for the &#8220;*valuable piece of screen real estate*&#8221;

---

### Post by stinkeye on 2010-05-03
Remove the Indicator Applet and add
gnome-volume-control-applet
to startup applications.
Will display in Notification Area like karmic.

or

remove the packages 
*indicator-messages*
*indicator-me*
```
sudo apt-get remove indicator-messages indicator-me
```

and you will be left with just the volume icon in the
Indicator Applet

---

### Post by Scunnered on 2010-05-03
**stinkeye**

Many thanks for your reply.

Everything worked a treat. I am now able to easily move the logout button so that I dont keep closing the wrong item.

---

