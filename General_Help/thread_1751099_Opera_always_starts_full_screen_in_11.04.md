---
title: "Opera always starts full screen in 11.04"
date: 2011-05-06
forum: General Help
---

### Post by schveiguy on 2011-05-06
This seems like an opera issue, but I don't remember this happening before my upgrade to Ubuntu 11.04.

However, whenever I start opera via command line, application menu, or sidebar icon, the app starts in full-screen mode. This is not what I want, because it makes my sidebar hide (I like it to be shown while I'm doing stuff).  There seems to be a -fullscreen option, but not a -nofullscreen option.

Anyone have any ideas?  Is there some setting in opera I can tweak this with?

-Steve

---

### Post by Frogs Hair on 2011-05-06
I use Opera and the first time I opened it in Unity it was maximized , but has not done that since installation. I saw another thread a couple of days ago and I don't know if it was solved . You could try the forum search.

---

### Post by lovinglinux on 2011-05-06
Try deleting the file operaprefs.ini from the opera folder, but make a backup first. This will reset the browser interface settings (and other stuff) and usually fixes those crazy behaviors.

Recently my Opera also started to display some weird behaviors, like collapsing the tab sidebar and not letting me undo it. This wasn't fixed by deleting the prefs file tho.

---

### Post by schveiguy on 2011-05-06
Thanks for the tip, lovinglinux, but it didn't work for me :(  Still opens full screen.

---

### Post by mc4man on 2011-05-06
Do you mean 'fullscreen' or maximized. The latter can be adressed

---

### Post by schveiguy on 2011-05-19
I mean maximized, sorry.  I forget about full screen mode because I only ever use it by accident :)

What I've found (and this is odd) is if I make opera below a certain size (width or height), it opens not maximized.  However, once I exceed this threshold (and I have no idea what that threshold is), it opens maximized.  When I un-maximize, it goes back to the width and height I set.

But I've discovered now, this is not an opera problem, it's an ubuntu problem, because I just tried the same thing with firefox, and opens maximized also!

Any ideas?  I kind of want it to open to be as large as it can be without intruding on the sidebar.

---

### Post by mc4man on 2011-05-19
natty has been set to automaximize any window that opens above 75% of the screen size.
Whether there is any inclination to raise this or remove the function in  an update not sure, probably not that likely.
(at least in natty

This can only be be changed thru a simple source edit and re-build of the unity source - (quite easy, if inclined, ask  - I use 90 % here on a laptop

> I kind of want it to open to be as large as it can be without intruding on the sidebar

If the launcher (sidebar) is set to never hide  then maximized windows should not intrude upon

---

### Post by schveiguy on 2011-05-24
Thanks for the info, that definitely explains it.  I really *really* think they should make this a configuration option, not a binary option.  I'd actually just like to disable it.  If I set my window to be a certain size, then restart it, why would I want it to be maximized?  If I wanted it to be maximized, I'd set it to maximized before starting.  I don't really see the use case for this at all, do you know what it is?

How do you set the launcher to never hide?  In system settings, I have two options:

Show the launcher when the pointer:
  * pushes the left edge of the screen
  * touches the top left corner of the screen

This wouldn't fix my complete problem, because I like to have the min/max/close buttons accessible even if the app is not focused.  But it's better than nothing.  I'm not interested in recompiling unity.

---

### Post by schveiguy on 2011-05-24
> **schveiguy said:**
> 
How do you set the launcher to never hide?

And I found it (should have searched first).  Used the compiz editor.

One thing about unity, I find that the scattered places where you have to edit configurations is not very "unified".

Thanks

---

### Post by msandoy on 2011-05-29
> **mc4man said:**
> natty has been set to automaximize any window that opens above 75% of the screen size.
Whether there is any inclination to raise this or remove the function in  an update not sure, probably not that likely.
(at least in natty

This can only be be changed thru a simple source edit and re-build of the unity source - (quite easy, if inclined, ask  - I use 90 % here on a laptop


If the launcher (sidebar) is set to never hide  then maximized windows should not intrude upon

Hi.
How did you rebuild the source to fix this BUG?
This is by far the most annoying problem I have found yet.

---

