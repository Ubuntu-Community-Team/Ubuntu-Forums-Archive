---
title: "change keyboard layout in the Terminal"
date: 2011-06-19
forum: General Help
---

### Post by cccc on 2011-06-19
hi

I have Ubuntu Natty installed and I'm using German keyboard layout. 
If I try to change using CTRL-ALT-F1 into terminal then I have US keyboard instead of German.
Howto change keyboard layout in the Terminal?

---

### Post by cccc on 2011-06-19
I've tried to change using:```

# dpkg-reconfigure console-data

```but now get very strange things, for example CTRL-ALT-F1 doesn't work anymore and mouse disappears.

---

### Post by prodigy_ on 2011-06-19
The right commands in your case would be **setxkbmap de** for graphical terminal and **sudo loadkeys de** for text (CTRL-ALT-Fx) console.

---

### Post by sojakob on 2012-11-21
> **prodigy_ said:**
> The right commands in your case would be **setxkbmap de** for graphical terminal and **sudo loadkeys de** for text (CTRL-ALT-Fx) console.

Thank you Prodigy_! I suppose i have the same problem cccc describes. At least setxkbmap [layout] does the trick for me.

But how can one sustain the xkb setting across reboots?
I can run setxkb in one terminal, then start another and realise that the change in xkb settings are sustained. But after reboot i will have to set the keymap once again...

---

### Post by wildmanne39 on 2012-11-21
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

