---
title: "Ctrl+F Constantly Launching: Which Package Controls Ctrl+F?"
date: 2012-06-09
forum: General Help
---

### Post by wyth on 2012-06-09
I need to find out which package manages the ctrl+f function so I can properly file a bug. 

The problem is my desktop is constantly launching the ctrl+f function in whatever application I have open -- Nautilus, Chromium, Gedit, etc. It's as if I'm hitting ctrl+f, but I'm not touching anything. Often it's happening in rapid succession, as if I were hitting ctrl+f repeatedly like some annoying git.

I think the package might be gnome-search-tool, but I'm not positive, since it happens in multiple applications. And I can't file a proper bug unless I know what package I'm filing the bug against.

If anyone else has had this issue, I'd be interested to know how you solved it. I've already ruled out hardware issues.

---

### Post by wyth on 2012-06-22
Gotta bump this -- it's driving me crazy, constant search functions popping up on whatever application I have on top. Dagnabbit, which package controls ctrl+f?

---

### Post by WorMzy on 2012-06-22
No package controls an arbitrary key combination. o_O

Try unplugging your keyboard, then launch an application that displays the behaviour. Does the same thing happen?

---

### Post by wyth on 2012-06-22
Thanks for the reply. When I filed the bug the first time, it was rejected because I didn't link it to a package. All I know is that no matter the application -- Chrome, Nautilus, Liferea, LibreOffice, gPodder, etc. -- the search function randomly and repeatedly launches *as if* I had hit ctrl+f. Since it's the same ctrl+f behavior across all those applications, I figured it had to be a package in Gnome. (I say Gnome and not Unity because the same thing happened in Gnome Shell.)

And yep, I tried taking out my keyboard (it's a laptop), and the behavior persisted. I just used the mouse for a while, browsed around the web and through a document I'm working on, and ctrl+f still launched itself at random. That's what makes me think this is a software issue, and not a hardware issue.

---

### Post by wyth on 2012-06-25
bump... this problem ain't fixing itself...

---

### Post by wyth on 2012-06-25
I've isolated something: This seems to happen after coming out of a blank screen. In fact it immediately happens on whatever application is up front as soon as I reactivate the screen.

---

