---
title: "gedit-latex-plugin broken partially"
date: 2011-07-22
forum: General Help
---

### Post by adam2007 on 2011-07-22
very strange bug

after installing and activating the gedit-latex-plugin the latex menu doesn't appear in the menu bar and you can't compile etc (latex->pdf in the tools menu is grayed out).

the menu can be retrieved by doing the following:

edit -> preferences -> plugins -> latex plugin 0.2 -> configure plugin
-> tools -> "latex->pdf" -> properties -> ok

not change anything, and just leaves these menus. the latex menu is back and you can compile etc.

had the same problem with xubuntu 11.04 when i tried it. then it just appeared in ubuntu.

anyone else have this problem? found a solution?

thanks

---

### Post by mikeym on 2011-08-02
Same problem. Thought I would try the gedit LaTeX plugin as people seemed to be saying good things about it. Tried installing it and it is behaving incredibly badly with errors left right and centre and with odd behaviour. Needing to click on *File>New* file for the menu item to appear *File>New LaTeX* that opens a new LaTeX document. 

Asking for a master and refusing to compile to a PDF if the default (None) is selected. Or for the file I'm using now, once selected *LaTeX to PDF* fails to compile even one of the templates. 

Even the compilation process feedback is broken. Selecting *View>Bottom Pane* to show the output from the compilation process shows errors for file "1" and "OSError" which I assume it means line one, and the OSError is from trying to open a compiled PDF that's failed.

Anyway, as far as I'm concerned it's broken. I assume it has something to do with Unity as there are a bunch of gtk errors about the menu when run it from the command line.

---

### Post by mikeym on 2011-08-02
I've made a quick bug report but couldn't be specific as I don't even know how it is supposed to work.

[https://bugs.launchpad.net/ubuntu/+source/gedit-latex-plugin/+bug/819826](https://bugs.launchpad.net/ubuntu/+source/gedit-latex-plugin/+bug/819826)

---

### Post by gorges on 2011-11-16
Hi. I've just installed Xubuntu 11.10 and gedit is working fine, but after installing "gedit-latex-plugin" via synaptics, it doesn't even appears on gedits plugins list.

Hope this get fixed.
Cheers,
Gorges

---

### Post by dannyboytward on 2011-11-26
I just recently upgraded to 11.10, and latex plugin doesn't appear in gEdit's plugins list (like for gorges).

I found this online [http://live.gnome.org/Gedit/LaTeXPlugin](http://live.gnome.org/Gedit/LaTeXPlugin) which says that the latex plugin doesn't work in gEdit v3 (my version is 3.2.1).  Not sure if that site is up to date though.  Is the plugin working for anybody?

---

### Post by andrewcd on 2012-05-24
I was having this problem today after shopping around for a replacement for winefish.  Turns out that the gedit plugin doesn't recognize the file as a latex file unless it has the .tex file extension.  Files that I made in Winefish didn't have any extension, but compiled fine in Winefish.  I renamed the file I was working with to add a .tex extension, so that texmaker could find it (I was also shopping texmaker).  And then tried gedit again, and it worked.

/for posterity
/happy to finally help this forum, instead of just mooch off it

---

