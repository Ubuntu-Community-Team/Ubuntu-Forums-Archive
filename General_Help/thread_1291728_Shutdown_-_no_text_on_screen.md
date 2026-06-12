---
title: "Shutdown - no text on screen"
date: 2009-10-15
forum: General Help
---

### Post by whizzle on 2009-10-15
Hey ya,

When I shutdown via the menus or even from the terminal I can't see any of the text that is displayed on the screen during the shutdown process. This becomes a problem with from the terminal because it list several options and I can't see what they are. Any ideas what's going on?

I'm using Ubuntu 9.04 full upgrades on a Dell laptop e1505. 
Cheers
\w/

---

### Post by P4man on 2009-10-15
? What options? How can you say that when you can't see it lol..?

---

### Post by whizzle on 2009-10-15
well...the text is very garbled, so I can see it's trying to print something to the screen, but it's so extremely garbled. Also the shutdown command apparently ask for input after it "shutsdown" So the system holds and I can see 4 options which highlight when I move the arrow keys. However, I can't read any of the text.

---

### Post by P4man on 2009-10-15
never heard that.. is it still a graphical screen, or a full screen text screen? You could try switching to a full screen terminal (control alt F1) and then type:

```
  sudo shutdown -c now
```

The only thing I can think off that it prompts you for, is saving unsaved docs, but that would happen in a graphical screen and shouldn't be garbled.

---

### Post by whizzle on 2009-10-17
yeah even the shutdown command is all garbled when it shuts down. Sigh....I guess it's not that bad of a problem.

---

