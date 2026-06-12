---
title: "Nautilus showing folder in open tree view when opened?"
date: 2009-10-18
forum: General Help
---

### Post by sanakan on 2009-10-18
I have a small problem that is still annoying me every day. I've made a command for the windows+E buttons to open nautilus using some of the instructions [on this page]("http://www.merlynx.com/2009/04/24/windowse-opens-nautalis-browser-in-centos/") and it works like a charm!

I have also changed the command for the buttons to

"nautilus /media/certainfolder" and it makes nautilus start by showing a folder different than the default Desktop folder, which i like it to.

**Noooow to my question: **Is there a way to show this chosen start-folder as **open** *in the tree-view on the side as well*? Now it is only marked by default, and the folder contents are to be seen in the right, main window. However, i would like the tree view to be open as well (it would save me some clicking).

If anyone knows the trick i'd be very grateful :-P

---

### Post by P4man on 2009-10-19
Open gconf-editor and browse to apps > nautilus > preferences
Set side_pane_view to "NautilusTreeSidebar" 
(without the apostrophes)

works in karmic

---

