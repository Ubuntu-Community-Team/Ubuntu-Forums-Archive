---
title: "Annoying default setting in emacs"
date: 2009-11-26
forum: General Help
---

### Post by shaggy999 on 2009-11-26
So whenever I hit the BACKSPACE key in emacs ('emacs23-nox' on karmic) it seems to execute the Ctrl-h command for help. This is incredibly annoying whenever I try to delete text and it is a default setting. How do I change this to the behavior of actually deleting a character? I don't recall this being the default behavior in previous versions of emacs on jaunty or previous.

---

### Post by Brandon Williams on 2009-11-27
I'm guessing that the problem is with your terminal emulator. What character is being output when you press the backspace key? Press Ctrl+V and then the backspace key. I expect that it's producing ^H instead of ^?. emacs wants backspace to be ^?. In my terminal emulator (xfce4-terminal), I can change the value output by backspace in the preferences dialog.

---

### Post by shaggy999 on 2009-11-27
Aha! The terminal emulator is the problem. I was running it in 'screen'. I exited out of screen and all of a sudden everything works. I'm going to have to look into my screen settings. Thank you! I'll post back a solution later once I figure it out.

---

### Post by shaggy999 on 2009-11-27
Ok, that wasn't the problem. I'm stupid. It works in a standard xterm but didn't work in guake. In fact there is a setting in the guake preferences to change the backspace key behavior. 	:oops:

---

