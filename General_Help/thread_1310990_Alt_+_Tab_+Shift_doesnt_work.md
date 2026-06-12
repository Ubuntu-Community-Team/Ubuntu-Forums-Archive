---
title: "Alt + Tab +Shift doesnt work"
date: 2009-11-02
forum: General Help
---

### Post by germbo on 2009-11-02
Hi everyone,

the usual window toggle by pressing Alt+Tab works, but it doesnt work backwards with Alt+Shift+Tab. I tried to set in the keyboard shortcuts, but had no effect.

Alt+Ctrl+Shift+Tab and Alt+Ctrl+Tab works but, I want the old Alt+Tab thing again.

How can I change it?

---

### Post by germbo on 2009-11-02
Keep it on top!

---

### Post by robinparriath on 2009-11-10
Here is the solution from [another thread]("http://ubuntuforums.org/showthread.php?t=1311047")

Check the key:
gconf-editor -> apps -> metacity -> global_keybindings -> switch_windows_backward

It is most probably disabled.  It was disabled for me too.

Change it to <Alt><Shift>Tab and alt+shift+tab will work again.

---

### Post by xv1700 on 2009-12-23
Thanks for the info. Mine was disabled by default in Karmic amd64. This seems to me to be a failing in the current distro, where do I go to raise this as a bug?

---

