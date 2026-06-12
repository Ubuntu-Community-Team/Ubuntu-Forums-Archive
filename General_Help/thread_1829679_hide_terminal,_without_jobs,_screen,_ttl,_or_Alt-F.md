---
title: "hide terminal, without jobs, screen, ttl, or Alt-F2."
date: 2011-08-20
forum: General Help
---

### Post by oldarney on 2011-08-20
Now that Alltray doesn't work, I'm having a really hard time hiding the terminal when it plays Pandora with Pianobarfly. I want to hide it, without putting it to sleep (which kills it) and still be able to get it back.

any ideas?

---

### Post by dave01945 on 2011-08-20
will minimising it not work

---

### Post by cryptotheslow on 2011-08-20
I think I'd be inclined to use screen ([https://help.ubuntu.com/community/Screen](https://help.ubuntu.com/community/Screen)) from one of the other tty's. i.e. Ctrl-Alt-F2 - login - run screen - start up your app in screen - detach from screen - logout on tty.

Should work fine.

You maybe able to just put the process to the background without screen. When it's running in your shell:
Ctrl-Z
bg

I've never used this latter method and I think it requires use of the "disown -h" command if you want to be able to close the shell and leave the process running still. Just something I've heard about rather than tried!

---

### Post by ~!geek!~ on 2011-08-20
Try guake! 
Its a terminal emulator. You can set it to appear n disappear using a hotkey. Has tab support. Doesn't appear in open program list etc..

---

