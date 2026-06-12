---
title: "add a url shortcut to unity"
date: 2012-02-04
forum: General Help
---

### Post by djbenny on 2012-02-04
i have a bookmark shortcut on my desktop at the moment, i want it in the unity dash, but i have tried dragging it there but it refuses to go there, unlike the applications which can be dragged around. any ideas?

---

### Post by mc4man on 2012-02-04
Do you mean the "Dash" > what opens from big ubuntu icon or the unity 'launcher' (sidebar

---

### Post by djbenny on 2012-02-04
> **mc4man said:**
> Do you mean the "Dash" > what opens from big ubuntu icon or the unity 'launcher' (sidebar

no i mean the unity sidebar at the edge of the screen, i have put links in there for Chrome, Hedgewars etc. but this shortcut is refusing to go there

---

### Post by mc4man on 2012-02-04
While a url shortcut is a .desktop it's not the correct type to add to the unity launcher

The launcher accepts .desktop's of 
Type=Application
Exec=<a command>

Your 'url launcher' is a .desktop of
Type=Link
Url=<a url>

(open gedit & then drag & drop your launcher onto - you'll see

Additionally the url launcher is seen as a html file so when clicking on it it's opened by whatever app you've set as default for "text/html"

The best way to add a url is to create a quicklist entry for whatever browser you wish that's in your unity sidebar, then it's a right>left click to use.

Do you know how to do that?

(if you create a standalone for the sidebar it can work but likely will only be a launcher, control will go to the browser icon..

---

### Post by djbenny on 2012-02-04
ah, i found in chrome a very simple way of doing it!

[http://shuffleos.com/3644/how-to-pin-websites-to-ubuntu-unity-launcher-as-apps-with-chrome/](http://shuffleos.com/3644/how-to-pin-websites-to-ubuntu-unity-launcher-as-apps-with-chrome/)

---

