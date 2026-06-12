---
title: "always-on-top above fullscreen"
date: 2009-11-03
forum: General Help
---

### Post by onclouds on 2009-11-03
Hi,

I want to keep my totem video player remain always-on-top even when playing FM10 in fullscreen.. 

Does anyone know how this can be done ?!

tkx in advance

EDIT: running Karmic Koala with Compiz activated and Wine v1.1.32

---

### Post by wrgb2 on 2009-11-03
It should stay on top if you set Always on Top in the window menu (top-left corner, little button) before going into full screen mode.

---

### Post by onclouds on 2009-11-03
> **wrgb2 said:**
> It should stay on top if you set Always on Top in the window menu (top-left corner, little button) before going into full screen mode.

well.. it doesn't =/ 
I always set Totem to always-on-top ++ sticky when viewing videos and if I start a full screen app Totem always goes to background when the full screen app has focus =/

---

### Post by P4man on 2009-11-03
You could try wmctrl to fake a fullscreen.
Have a look at this:
[http://forum.boxee.tv/showthread.php?t=287](http://forum.boxee.tv/showthread.php?t=287)

its for boxee but should work for any app I guess

---

### Post by onclouds on 2009-11-06
> **P4man said:**
> You could try wmctrl to fake a fullscreen.
Have a look at this:
[http://forum.boxee.tv/showthread.php?t=287](http://forum.boxee.tv/showthread.php?t=287)

its for boxee but should work for any app I guess

hmm... I've read this article but it's not what I need..

What I really need is for an application to run in fullscreen and the window manager to put apps that are sticky+above over it!..

I want to have Totem (resized) above the fullscreen app!


any input appreciated!

---

### Post by P4man on 2009-11-06
> **onclouds said:**
> hmm... I've read this article but it's not what I need..

What I really need is for an application to run in fullscreen and the window manager to put apps that are sticky+above over it!..

I want to have Totem (resized) above the fullscreen app!


any input appreciated!

I know and thats why I posted that. Using wcrtl your totem will cover the entire screen without being "fullscreen" allowing other apps on top.

---

### Post by HiImTye on 2009-11-06
are you using compiz? you can try the 'Window Rules' plugin and do something like class=totem

---

### Post by onclouds on 2009-11-06
> **HiImTye said:**
> are you using compiz? you can try the 'Window Rules' plugin and do something like class=totem

will try that and report back ;)

> **P4man said:**
> I know and thats why I posted that. Using wcrtl your totem will cover the entire screen without being "fullscreen" allowing other apps on top.

=S you still don't get it.. Totem is the app that will be above a fullscreen app!.. except, since the other app is in fullscreen mode it overlaps totem's small window...


EDIT: used compizconfig to set Totem as above+sticky and it still doesn't solve the problem with fullscreen applications.. I'm getting pretty desperate here =/

---

### Post by P4man on 2009-11-06
> **onclouds said:**
> 
=S you still don't get it.. Totem is the app that will be above a fullscreen app!.. 

sigh.. I said *should work for **any** app I guess*
So use wmctrl to fake a fullscreen with the *other* app. The idea is exactly the same. 

Or dont try it and keep asking.

---

### Post by AldenIsZen on 2010-10-26
I am just trying to make totem sticky... I tried grabbing it, and I tried using the class=totem in the Compiz Window rules. No dice.

---

