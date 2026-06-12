---
title: "quit to DOS"
date: 2006-06-18
forum: General Help
---

### Post by DirtyJay on 2006-06-18
So...is there a way to run just the basic linux, without GNOME? When I installed Ubuntu, there was an option to install just the basic system.  This meant only having a operating system with just command line function.  Does anyone know if I can do this with my existing Ubuntu?  Yes, I know I can use the terminal, but I feel I will get a better handle on command lines, if I'm forced to.  If GNOME is not available, then one has to learn to navigate with commands.  I am ok with having to install another system of basic ubuntu, but I thought there may be a way to do it with my existing.  In Windoze 98 you can quit and revert to DOS.  Is there anything similar to that for Ubuntu?

Thanks

---

### Post by aysiu on 2006-06-18
Well, do you want to quit, or do you want to uninstall Gnome?

If you just want to quit to the command-line, press Control-Alt-F1.

If you want to uninstall Gnome, try ```
sudo aptitude remove x-window-system-core
```

---

### Post by DirtyJay on 2006-06-18
Thank you very much!
I just wanted to quit to command line, I really like GNOME, but sometimes working with the basics just gives one a better understanding.  I figured out to get back to GNOME is Ctrl+Alt+F7, right? Again, thanks a lot.

---

### Post by aysiu on 2006-06-18
Yes, Control-Alt-F7. I probably should have told you that, but you figured it out on your own. Good on you.

---

### Post by Fred Doolie on 2006-06-19
[QUOTE=aysiu]Yes, Control-Alt-F7. I probably should have told you that, but you figured it out on your own. Good on you.[/QUOTE]

Cool.

What's a "System 76" Computer?

---

### Post by aysiu on 2006-06-19
[QUOTE=Fred Doolie]Cool.

What's a "System 76" Computer?[/QUOTE]
It's built for and preloaded with Ubuntu:
[http://system76.com/](http://system76.com/)

---

