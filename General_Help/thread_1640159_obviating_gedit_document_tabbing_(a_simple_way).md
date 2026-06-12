---
title: "obviating gedit document tabbing (a simple way)"
date: 2010-12-07
forum: General Help
---

### Post by MichaelBurns on 2010-12-07
Apparently, I'm the only one who cares.  But, just in case you are also frustrated by Gedit document tabbing, this may interest you.

Where *I'm* coming from:

I don't like document tabbing (e.g. tabbed browsing) at all.  I first encountered the document-tabbing concept in Firefox, long after I had discovered perhaps the most useful keyboard shortcut of all time: Alt+Tab.  This together with Alt+F4, Bckspc, and the arrow keys form a powerful set of keyboard shortcuts to make quick work of managing documents.  However, this quick work gets stomped by Gedit tabbing, particularly when I want to close one of my text documents and wind up closing all of them (because Alt+F4 closes the entire window containing all of the tabs).

If you like document tabbing (because you like using the mouse perhaps? or maybe you like having an extra key in the shortcut sequence to switch documents?), then we simply disagree, and I hope that we can still be friends.  However, if you come from a similar place as do I, then try (something like) this:

```

System > Preferences > Main Menu :
   Applications >> Accessories >> Text Editor :
      Properties (button) :
         Command (field) : gedit --new-window %U

```
NOTE: This works from *my* **Ubuntu Jaunty** live CD.  I take no responsibility for trying this in other *buntu versions (although if you're using *=K or *=X, then you shouldn't be having this issue anyway).

The simple addition of the **--new-window** option to the gedit command: that's it!  No plugins.  No source hacking.  Gedit will still exhibit a tab (because GNOME wants to remind me that I have psychological problems for disliking tabs), but the tab is now superfluous (harmless).  Each text document will now open from the file browser (Nautilus) in a different window that can now be selected with Alt-Tab and closed with Alt-F4 without worrying about the other open text documents.  Let the window manager (Metacity?) do it's job.

---

