---
title: "Keyboard shortcut to printing some text"
date: 2011-07-01
forum: General Help
---

### Post by sandric on 2011-07-01
Hi. I was wondering, is there some tool to program shortcut, say ALT+Z to otput "<%="?
I got Logicech wave keyboard, and on windows it has manufactors program for programing this stuff, but under nix it is not ported, such as drivers too.
Thanks

---

### Post by eric3_14159 on 2011-07-24
Assuming you are running GNOME, there is a "Keyboard Shortcuts" program, which you can usually get to from System -> Preferences. If you scroll to the bottom, there is a section for "custom commands", where you can add your own, and set the key combinations you want to activate them. The best way to use it is to make a directory for scripts which will do what you want, usually $HOME/bin, and make them be activated by the shortcuts.

Outputting text to the window which currently has focus is actually a problem of its own, and unfortunately not one I know how to solve. I will let you know if I run across it, and if anyone else knows how, please do chime in.

EDIT: Wow, just an hour later. The program is "xdotool", which is in the repositories. If you write a script which will execute "xdotool type 'hello'", and bind it to a keyboard shortcut, then your computer will act as if you typed "hello" in whatever window has focus when you activate it. Hopefully this should do what you want. Good luck!

---

