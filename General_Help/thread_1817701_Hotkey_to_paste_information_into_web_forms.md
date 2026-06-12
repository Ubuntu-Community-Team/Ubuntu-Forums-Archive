---
title: "Hotkey to paste information into web forms?"
date: 2011-08-03
forum: General Help
---

### Post by tarahmarie on 2011-08-03
I type my address 20 times a day. 

Imagine that I want to do something like CTRL + TAB + a to fill my address into a web form, or CTRL + TAB + p for my phone number.

How might I do something like that?

---

### Post by Habitual on 2011-08-03
LastPass firefox plug-in.

---

### Post by tarahmarie on 2011-08-03
Awesome, thanks! How about if I want to be able to do that on my box, not just in a browser?

---

### Post by tarahmarie on 2011-08-03
Ah, actually it seems like LastPass is a bit heavy for what I want; I apparently need to create an account, etc.

I just want some sort of running process on my box that pastes my address in with some hotkeys, whether in a browser or elsewhere.

---

### Post by Baniita on 2011-08-03
[https://addons.mozilla.org/en-US/firefox/search/?q=form&cat=all&x=0&y=0](https://addons.mozilla.org/en-US/firefox/search/?q=form&cat=all&x=0&y=0)

:9 Check out those add-ons.

---

### Post by enimeizoo on 2011-08-03
It might not be exactly what you want, but xte or xdotool allow you to simulate a keyboard input. 
```
xdotool type "mysuper@adress.com"
```Binding to a global shortcut using your desktop environment shortcut system or xbindkeys would allow you to use the shortcut in any app, not only a browser, if it is of any use.

If want to use a key sequence as a shortcut, have a look at xbindkeys' guile configuration.
```
xbindkeys -dg 
```
To have an overview.

Hope it helps.

---

### Post by tarahmarie on 2011-08-05
Here's the perfect solution.

[http://www.fsavard.com/flow/2008/06/using-xsel-xbindkeys-and-xmacro-to-insert-common-strings-date-name-etc-in-linux/](http://www.fsavard.com/flow/2008/06/using-xsel-xbindkeys-and-xmacro-to-insert-common-strings-date-name-etc-in-linux/)

Thanks all!

---

