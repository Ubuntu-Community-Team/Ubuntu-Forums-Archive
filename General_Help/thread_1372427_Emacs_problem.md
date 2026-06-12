---
title: "Emacs problem"
date: 2010-01-04
forum: General Help
---

### Post by theturbanator on 2010-01-04
Hi everyone,

I recently upgraded to Ubuntu 9.10 from 9.04, and now I am facing a problem with Emacs:

Whenever I run Emacs, it works, but I get the following message:

```
(emacs:2861): GLib-WARNING **: g_set_prgname() called multiple times
```I tried uninstalling and reinstalling Emacs and also deleting the .emacs.d directory (I saw a fix for this problem when trying to run Firefox from the command line that involves simply deleting the .mozilla file).  Was it a bad idea to delete the .emacs.d directory? Even after reinstalling Emacs, I do not have that directory any longer.  Is it necessary?  How can I get it back?

And how can I get this correct this problem?

Thank you very much!

---

### Post by trellis2 on 2010-01-05
I had the same error message: (emacs:10708): GLib-WARNING **: g_set_prgname() called multiple times. And it takes a long time for emacs to start up. But most important of all the text font is wayyyyyyyyyy too big.
With Karmic xorg.conf, ~/.Xdefaults or, ~/.Xresources is not available. Right now all I have is conceptual duct tape and bale wire. Wish me luck I'm going in.

---

### Post by trellis2 on 2010-01-05
I think I've solved emacs the "too large font" problem for karmic.

 ```
xfontsel
```

will help as a guide for options available to change emacs fonts. This can be appended to the emacs command in the terminal.

```
emacs -fn "-*-inconsolata-medium-r-*-*-12-*-*-*-*-*-*-*"
```
problem solved. still getting the error message though.

---

