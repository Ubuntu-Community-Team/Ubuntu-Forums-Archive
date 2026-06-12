---
title: "Open am emacs window on another computer through ssh -X without consuming a terminal"
date: 2010-07-21
forum: General Help
---

### Post by Zorgoth on 2010-07-21
What the title says:

I need to access another computer, and the only window I need open is emacs.  It

If I run, for example

echo emacs | ssh -X me@remote_computer

this allows me to run emacs and when emacs closes, I get my terminal back, but while emacs is running I can't use the terminal.

If I run

echo emacs | ssh -X me@remote_computer &

I don't get to type in my password.

So I am wondering if there is a nice, quick way to open an ssh shell, type in my password, and then get back to the same old terminal, or a way to do it with Alt-F2 and a box to type my password in or something.

The command "screen" works but I am hoping to get something more like just one command.

I'd be fine with writing a script for it if someone could give me a pointer or two.

---

