---
title: "Openoffice rendering problems"
date: 2009-08-11
forum: General Help
---

### Post by adempewolff on 2009-08-11
I don't know if rendering is the right term technically, but its the only word I can think of to describe this problem:

I love openoffice but have one problem which is enough to make me boot back over to windows for office 2007.  While I am typing (I have noticed this problem in the word processor and spreadsheet) something blocks of text will disappear and/or appear in the wrong place.  This is very easily recreatable as it happens very frequently.  In 30 seconds I was able to generate this screenshot:

[ATTACH]124468[/ATTACH]]

I am able to correct the problem by either selecting the text, drag the window off screen then back on, among other methods.  The corrected text looks like this:

[ATTACH]124469[/ATTACH]

I also have slightly different but similar problems in almost all of the openoffice menus.  Here is a quick example:

[ATTACH]124470[/ATTACH]

Here the bottons are acting up in other menus directories or menu txt will act up.

I don't know if this is a problem with openoffice, compiz, gnome or what but I am sure that it has to have something to do with my settings because I can't imagine everyone who uses openoffice putting up with this bug and not mentioning it.

Any advice on what I could do would be appreciated.  I can supply additional information as requested.  Thanks!

---

### Post by adempewolff on 2009-08-11
Fixed the problem.  It looks like it would be more accurate to call them "redrawing" problems.  I noticed it happened in a few other applications than just openoffice, which led me to suspect my graphics card (NVIDIA Quadro NVS 135m) or compiz.

In fact the problem lies with compiz and certain nvidia graphics cards.

It is solved by going into the compiz config settings manager (system:preferences, or ccsm from a terminal), then to utilities:workarounds and checking "Force synchronization between X and GLX".

Hope this helps for anyone with the same problem.

---

### Post by diazamet on 2009-08-13
Adempewolff: Just a quick thanks.  This was driving me crazy!  You should add '[SOLVED]' to the post title.

---

### Post by adempewolff on 2009-08-13
glad to have helped! I know this bug was driving me crazy as well, it is hard writing papers when everything you've written is playing musical chairs on the screen!

I don't think I can change the thread title.  a moderator would need to do that.  I can add "solved" to the tags for the time being.

---

### Post by mlalkaka on 2009-08-14
Thanks, adempewolff! I've been living with this problem for a while now, and couldn't find the solution. I figured I'd do a Google search for it one more time today, and sure enough, I found your post from just 2 days ago (after choosing "Recent Results"). Talk about coincidence.

---

### Post by vgrisham on 2009-09-09
Thank you adempewolff! I got so mad while using OpenOffice the other day that I seriously considered installing Word through Wine. Thanks for saving me the trouble. Your solution has made OpenOffice usable again.

---

### Post by viniciusandre on 2010-01-24
Man! That's awesome... So simple to solve, and was driving me crazy while typing all my stuff in there.

As I'm on Debian I might say that the problem was reproduced here too.

Thanks.

---

