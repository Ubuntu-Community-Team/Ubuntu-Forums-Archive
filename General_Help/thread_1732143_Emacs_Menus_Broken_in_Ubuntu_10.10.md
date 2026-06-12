---
title: "Emacs Menus Broken in Ubuntu 10.10"
date: 2011-04-17
forum: General Help
---

### Post by Pantheraleo on 2011-04-17
Some of the emacs menus seem to be broken in Ubuntu 10.10. This is a problem using emacs 23 as well as emacs-snapshot. I found an old thread stating that this had been fixed in emacs-snapshot, but it appears that it is broken again. Here's a list of the problems:


[LIST]
[*]Buffers menu only shows Scratch and Messages. And they don't actually navigate the Scratch or Messages buffer.
[*]When editing a Lisp file, the Lisp menu is is empty. In other words, clicking on it produces a menu that has nothing in it.
[*]If SLIME is installed, the same thing occurs when clicking on the SLIME menu. It is empty.
[/LIST]
If I start emacs with the -Q option, the Lisp and SLIME menus work correctly, but the Buffers menu still doesn't. The fact that -Q partially fixes it seems to suggest it is some kind of problem with the default emacs configuration in Ubuntu. I've tried uninstalling all other modules and renaming my .emacs file to something else, but it doesn't resolve the problem. However, because of this, I can be sure it is nothing I am loading, or no setting I have in .emacs that is causing it.

Can anyone else confirm this problem? And does anyone have any suggested solutions?

Thanks!

---

### Post by Port 80 on 2011-04-17
Pantheraleo,

There is a another thread called "upgrade" where Mebburke ran into problems after upgrading to 10.04.  I myself, have had problems (see response below). You are not alone -- but i don't have a solution yet.


Meburke:

I did not have that problem after the upgrade, and I have to research before I can offer even a useless answer. I too had something show up that was not there before: When I start emacs in the virtual terminal, I get the 'xemacs' with this error:


** (emacs:9327): CRITICAL **: murrine_style_draw_box: assertion `height >= -1' failed** (emacs:9327): CRITICAL **: murrine_style_draw_box: assertion `height >= -1' failed


Emacs still functions, but it disturbs me. Of course, I don't get that if I use the -nw option.

I think that there was a library change in 10.04 that causes the bug.

---

### Post by delaossa on 2011-05-09
Dear Pantheraleo and others,
I exactly have your same problem with the buffers menu.
When I open emacs from the terminal with the name of the file to be edited as an argument:
> emacs file &

That file does appear in the buffer's menu, but any other that I open from that emacs session doesn't. That seems to indicate that new opened files are not added to the emacs buffers menu.

I have tried to install older versions of emacs-snapshot package, but it doesn't fix the problem.
On the other hand, emacs-snapshot always worked well before and since some update in ubuntu 10.10 I am experience this annoying behavior.

Any ideas?

---

