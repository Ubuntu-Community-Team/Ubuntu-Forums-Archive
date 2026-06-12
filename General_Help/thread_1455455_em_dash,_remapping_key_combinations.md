---
title: "em dash, remapping key combinations?"
date: 2010-04-16
forum: General Help
---

### Post by jon.reeve on 2010-04-16
Hi, I have this crazy idea to map an em dash to AltGr+Dash, replacing the yen symbol currently produced by that key combination. Is there a way to do that? 

Unless, of course, there is another way to produce an em dash with the US International keyboard? Not including OpenOffice's autocorrect feature.

---

### Post by scottiw2000 on 2010-04-22
Editing X keyboard files is a bit of a pain since there isn't a good GUI program for it at the moment. The closest I've found so far is Keyboard Layout Editor ([http://code.google.com/p/keyboardlayouteditor/](http://code.google.com/p/keyboardlayouteditor/)). It works decently, but still isn't very stable and you need to do some manual file-editing. If you decide to try it, I can help if you run into problems.

The other easy way to produce an em dash (or any other character) in any Ubuntu application is to enter its unicode number directly. 

- type ctrl+shift+u (this will produce an underlined letter u)
- then type the four-digit unicode number for the em-dash (2014)
- then press spacebar

The underlined u will be replaced by whatever character corresponds to the code you entered, in this case an em-dash.

To find the unicode number for a character, look the character up in character map (applications>accessories). When you select the character its unicode number will be listed at the bottom of the window in the form U+0101 (or whatever). Ignore the U+ part. It's the four following digits that you need to use the steps listed above. (an en-dash is 2013).

---

### Post by jon.reeve on 2010-04-26
Thanks, but 1) I am hopeless with source files and things that aren't readily apparent, and so I am totally lost with the gui that you linked to--can't even get it to run. 2) a seven-keystroke shortcut isn't as efficient as I would like. I need to type a lot of em-dashes, and that's just too many keystrokes. What I'd like to do is just press altgr+hyphen. I was hoping this could be done with a single command, like with xmodmap.

---

### Post by jon.reeve on 2010-04-26
So it seems the US-Macintosh keyboard layout has an em dash. It's a bit of a trade-off, though, it seems, since I now have an extra keystroke involved in writing é, but it's better than nothing. —!!

---

### Post by scottiw2000 on 2010-04-27
I think there is at least one gnome utility that will record a macro and then let you assign it to a keystroke. I'm not sure what it's called, but that would be another option. Since it operates at the os level it would work in any window and do exactly what you want.

Or, if you add the "character palette" widget to your gnome panel, you can set up a palette with em-dash. Then a middle-click will insert it into any document. I don't know whether character palette will let you change that key assignment or not.

---

### Post by scottiw2000 on 2010-04-27
By the way, what program are you working in? Openoffice lets you set up character replacement so that if you type a combination of characters (say -m or ---) the program automatically replaces it with the character you assign.

---

