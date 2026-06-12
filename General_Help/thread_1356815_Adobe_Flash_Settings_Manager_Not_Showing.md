---
title: "Adobe Flash Settings Manager Not Showing"
date: 2009-12-16
forum: General Help
---

### Post by miggerish on 2009-12-16
Every time I go to this link, it is not showing the Settings Manager anymore! it just shows a white space where the Flash Settings Manager should be embedded:

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html")

I am using latest version of Ubuntu and Firefox and Flash.

This is what should show up in the empty space:

[IMG]http://i.i.com.com/cnwk.1d/i/bto/20090303/flash-nocookies-cropped.png[/IMG]

I think it is possible that I moved the bar all the way down to "0kb" storage, and so maybe the flash settings manager has no storage space to operate anymore?  But the makers of Adobe Flash Settings Manager couldn't be that inconsiderate, could they?

---

### Post by ean5533 on 2009-12-16
> **miggerish said:**
> But the makers of Adobe Flash Settings Manager couldn't be that inconsiderate, could they?
Adobe's Linux implementation of Flash is a joke. No bug, no matter how stupid, would surprise me.

Are you running 32-bit or 64-bit Ubuntu? If running 64-bit, are you running the 32-bit Flash plugin through a wrapper, or are you using the experimental 64-bit Flash plugin?

---

### Post by miggerish on 2009-12-16
> **ean5533 said:**
> Adobe's Linux implementation of Flash is a joke. No bug, no matter how stupid, would surprise me.

Are you running 32-bit or 64-bit Ubuntu? If running 64-bit, are you running the 32-bit Flash plugin through a wrapper, or are you using the experimental 64-bit Flash plugin?

32-bit

---

### Post by wojox on 2009-12-16
Mine is set to 0 mb ( none ) and it still works. Don't know?

---

### Post by ean5533 on 2009-12-16
> **miggerish said:**
> Every time I go to this link, it is not showing the Settings Manager anymore! it just shows a white space where the Flash Settings Manager should be embedded:

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html")

I am using latest version of Ubuntu and Firefox and Flash.

This is what should show up in the empty space:

[IMG]http://i.i.com.com/cnwk.1d/i/bto/20090303/flash-nocookies-cropped.png[/IMG]

I think it is possible that I moved the bar all the way down to "0kb" storage, and so maybe the flash settings manager has no storage space to operate anymore?  But the makers of Adobe Flash Settings Manager couldn't be that inconsiderate, could they?

I tried it on my 32-bit Ubuntu install and my 64-bit Ubuntu install, and it works from both places. 

I'm really not sure how else to help without being able to reproduce the problem. That's the problem with proprietary technologies like Adobe Flash: they a pain in the *** to work with and support.

---

### Post by atlantique on 2010-03-11
I had exactly this same problem, which miggerish described so well above.

I was able to solve it by opening first the following swf content:


[https://www.macromedia.com/support/flashplayer/sys/settingsmanager2.swf?defaultTab=g_security](https://www.macromedia.com/support/flashplayer/sys/settingsmanager2.swf?defaultTab=g_security)

This swf content will still be blank, however after having loaded it. I was ble to load  the "global security settings" panel at the macromedia.com  site withou
t problems, i.e. it was no longer blank.

I did not discover this. The credit for circumventing Adobe Macromedia nasty, an
noyance belongs to Seb Lee-Delisle's posting at

[http://sebleedelisle.com/2009/12/flash-player-settings-panel-nightmare/](http://sebleedelisle.com/2009/12/flash-player-settings-panel-nightmare/)

---

