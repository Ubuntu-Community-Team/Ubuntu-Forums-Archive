---
title: "emacs noob help"
date: 2010-05-02
forum: General Help
---

### Post by Max Destruction on 2010-05-02
hey ..

when i start emacs and enter to the shell (ALT+X shell) i seem to get into this other mode where its all binary or something and standard commands like 'cd Desktop' are not recognised. You can see my problem by looking at this screenshot. I think the problem relates to the 'm' that is prefixing my username. i do knot know what that m is about, actually. 

[IMG]http://i872.photobucket.com/albums/ab282/sornrize2night/emacswtf.png[/IMG]

---

### Post by WorMzy on 2010-05-02
What are you trying to do? It looks like you're treating emacs as a terminal, when it's actually a text editor. If you want a terminal, look in Applications -> Accessories -> Terminal.

The output you're getting there *is* actually the output of ls, but with what looks like special formatting tags.

---

### Post by lykwydchykyn on 2010-05-02
OP is in an emacs shell buffer, which is like a terminal. Only not quite.

The "m" and the other code junk you see around your username are just the codes that your shell would normally interpret as colors or other formatting marks.  Emacs shell buffers don't interpret those, so you see garbage instead.

As for cd not working, looks like you aren't in your home directory.  Try to cd to the full path, or type "pwd" to verify.  Looks like you're in /.

Finally, while there isn't an Emacs shell mode I'm completely happy with, you might try "eshell" (M-x eshell) or "terminal" (M-x terminal) instead of the default shell buffer.  They both have their good and bad points, but eshell at least interprets formatting codes so the prompt looks right.

---

### Post by Max Destruction on 2010-05-02
ahhh i see. ok thanks, back on track now.

/how do i mark this thread as solved?

---

