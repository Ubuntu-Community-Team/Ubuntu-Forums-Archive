---
title: "Firefox Keeps Freezing"
date: 2010-05-11
forum: General Help
---

### Post by Mike_IronFist on 2010-05-11
I don't know what caused it, maybe an update, but Firefox won't stop freezing on me. I open it up, it slows down very quickly, and then fades to gray. I still have Chromium for "browser emergencies" like this one, but any idea on how to get my browser of choice working again?

---

### Post by Mike_IronFist on 2010-05-11
Ah. I found the problem by firing up a terminal and running
```
firefox -safe-mode
```
And I used that to disable all the add-ons. Turns out the "bindwood" add-on that Ubuntu One installs to sync bookmarks with Firefox was breaking Firefox for me.

I've removed the package "xul-ext-bindwood" (no quotes) and everything's fine now!

---

### Post by jschille on 2010-05-13
Hey there, I am having the same problem but not quite sure how to follow what you did...
All I have done so far is typed in the terminal 
```

firefox -safe-mode

```and it opened up firefox

edit: didn't fix it for me =/

---

