---
title: "How do I change Parcellite's icon in the top panel?"
date: 2011-10-23
forum: General Help
---

### Post by iosuna86 on 2011-10-23
I guess the title says it all.

The thing is that I am running Ubuntu 11.10 and I have installed the new Faenza icon theme (Ambiance). However, Parcellite's icon is still the default one when I installed it last week. It's a Mario-like icon (a big "P" inside an orange clipboard). It is ugly as hell and it kinds of breaks the style of my top bar.

There is no way to change it via right click --> preferences or something like that.

I even tried changing the gtk-paste.svg in Faenza with a gksu nautilus usr/share/icons/Faenza/actions.... but the default gtk-paste.svg is not even displayed in the top bar. 

Am I missing something? Isn't there an easy way to change an app icon without the need of going through hidden folders? I was thinking of something like a right click on the app or icon, going to preferences and changing the icon for that app.

Thanks in advance!

---

### Post by ajgreeny on 2011-10-23
I don't know if it will work, but in my system there are three versions of the parcellite icon, 
/usr/share/pixmaps/parcellite.png  
/usr/share/pixmaps/parcellite.svg 
/usr/share/pixmaps/parcellite.xpm.  

I can only suggest you find the icon you want to use from ?? and replace the three in that place in your filesystem with your own versions of the same three image types.

Who knows?  It may work.

---

### Post by iosuna86 on 2011-10-27
Thanks for the replay and sorry for the delay. 

I'll try that in a moment and check if it is solved. It seems it can be done that way.

---

### Post by WorMzy on 2011-10-27
That's the way I used to do it. Nowadays I use ClipIt, which respects icon themes, so long as the theme contains a "clipit-trayicon.svg".

---

### Post by iosuna86 on 2011-10-28
@ajgreeny

It worked! Thank you so much!

@WorMzy

Actually Parcellite did work like that until the current release. I remember it used the "gtk-paste.svg" (or something similar) icon. 

I hope they made Ubuntu easier so that you can change the icon by going to the app properties with just a couple of clicks. 

Thanks to you all!

---

