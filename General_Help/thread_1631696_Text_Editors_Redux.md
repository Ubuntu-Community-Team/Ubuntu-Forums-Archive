---
title: "Text Editors Redux"
date: 2010-11-27
forum: General Help
---

### Post by owlcroft on 2010-11-27
I have Googled extensively, and there are apparently 3,762,481 text editors available for Ubuntu, with around 4,634 testimonials for each.  I am trying to narrow my options for evaluation to some number expressible in a single decimal digit.

Some of my criteria will no doubt be of assistance to those inclined to answer this post.  (My ideal was--and is--the wonderful OS/2 editor **EPM**, which was not only fast and powerful, but infinitely configurable.)

Let's start with gedit as a basis.  It would actually be quite serviceable if only it had two features:

1. Record/playback keystroke sequences.  That is: press key (or key combo) X, press some sequence of keys, up to a large-ish number, then press key/key-combo Y, and the sequence between X and Y is recorded and may be played back at any time by pressing key Z.  This is supremely important when one needs to do the same multi-key operation over and over--I, for one, find its lack in gedit (and other editors at about that level) inexcusable.  (Cream has this feature, but is in other ways a bit off-putting.)

2. "Block" moves: the ability to define, by keypresses, the four corners of an on-screen block (this obviously requires use of monospaced fonts), and then perform operations just on that block: copy, delete, paste (pastes the copied block at the cursor), and so on.  This is not a must-have deal-breaker, but is close.

Otherwise, the more or less standard feature set of gedit and its like.

Any suggestions?

---

### Post by eric3_14159 on 2010-12-24
Unfortunately, while there may be others, the only editor I personally know which can do both of those operations is Emacs.

I love Emacs, however, many people don't enjoy learning the many key combinations, nor the steep learning curve for using many of its more powerful features.

However, if you are willing to learn, you will find it incredibly customizable (the entire editor is written, and can be extended, in a dialect of Lisp). For your two tasks in particular:

1. Typing "Control-x (" starts defining a macro, which means it records all they keys you press (and other commands you might run), until you type "Control-x )", which finishes the macro. You may then execute the macro with "Control-x e". There are also ways to bind the macro to other keys if you need multiple at once.

2. You can "mark" an area, starting the mark by typing "Control-Space", and then navigating elsewhere on the page, whether by the arrow keys, word-jumps, searching, or other Emacs navigation methods. When you are at the end of the block you require, you can run commands such as "Control-w" (cut), "Alt-w" (copy), or "Control-Alt-\" (indent properly). This only gives you two points to define your block with, the beginning and end character, but it still should accomplish what you need.

Good luck!

---

### Post by djeikyb on 2010-12-24
Yeah, I don't anything on the level of Gedit that does what you want. Emacs is an option, I prefer Vim. Based on your dismissal of Cream, I'm guessing you won't be satisfied with either of these. It's definitely worth the effort to learn though. These days I can hardly bear to type a post like this without the convenience of modal text editing.

Anyhow, in Vim, you hit v to put yourself in block select, hjkl are your left-down-up-right directional keys, y copies, p pastes. To do the macro thing you describe, type q to start recording, another letter (a), do what you want, hit q to stop recording. To repeat the operations, type @-a (or whatever letter you picked).

And I just resisted the urge to type colon x to save and quit.

---

### Post by djeikyb on 2010-12-24
Found this: [http://e-texteditor.com/blog/2009/linux-progress](http://e-texteditor.com/blog/2009/linux-progress). In the meantime, you could try running it in wine.

Hrm, I'm not entirely sure which editor you refer to, if the above Textmate isn't correct, then I perhaps IBM's E is what you mean, in which case, have you tried SlickEdit? Or JERED?

[http://www.slickedit.com/products/slickedit/platform-options](http://www.slickedit.com/products/slickedit/platform-options)
[http://texteditors.org/cgi-bin/wiki.pl?JERED](http://texteditors.org/cgi-bin/wiki.pl?JERED)
[http://texteditors.org/cgi-bin/wiki.pl?E](http://texteditors.org/cgi-bin/wiki.pl?E)

---

### Post by HermanAB on 2010-12-24
My tuppence worth:
I use Geany, Gedit, Joe, Nano and Vi (when all else fails).

---

### Post by oldos2er on 2010-12-24
[http://live.gnome.org/Gedit/Plugins](http://live.gnome.org/Gedit/Plugins)

There's a macro plugin; don't know about block editing though.

---

### Post by owlcroft on 2010-12-24
I do not see the gedit macros plugin mentioned.  Is it a separate package requiring Synaptic installation?

Also, I forget another critical need: bookmarking.  I really, really fell it needful to be able to slap a mark at any point in the text with some simple key combo, then junp back to that mark from anywhere else with some other simple combo; and there should be several of those.  (Back in EPM, I had them customized as Alt-# to mark and Ctrl-# to return, where # was any digit from 1 to 9.)

And I'll say that I don't really want the learning curve of the vi/vim family: just something a little better than gedit would suffice (that is, gedit with programmable macro key[s], boomark[s], and block moves, which last I could probably live without if I could get the rest--though being able to rearrange columns is *so* handy.)

---

### Post by owlcroft on 2010-12-24
OK, so I feel stupid.  I was unaware of the extra plugins for gedit available at the gnome site's [**gedit plugins page**]("http://live.gnome.org/Gedit/Plugins").

A couple of the third-party plug-ins there have supplied a reasonably satisfactory [**macros**]("http://code.google.com/p/gedit-macro-plugin") capability, and a slightly lame but tolerable [**multi-bookmarks**]("http://live.gnome.org/Gedit/LineToolsPlugin") capability (via  a plugin that also adds a deal of other useful editing functionality).

With those, though I still lack a block-edit capability, I am much happier with gedit (and have removed Cream, which I used only when I needed macros.)

---

