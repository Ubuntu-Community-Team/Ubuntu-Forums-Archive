---
title: "Key combinations"
date: 2009-11-24
forum: General Help
---

### Post by TryHarder on 2009-11-24
Hey everyone, I'd like to know how can I cancel annoying Shift+backspace key combination (simply logout me). In Preferences->Keyboard shortcuts i haven't found something useful. Is there some file that I can edit to get rid of this trouble (sure it is, just where to find it). 
I'm using Thinkpad T400 laptop and ubuntu 9.10 karmic if it matters.
Thanks.

---

### Post by Giblet5 on 2009-11-24
So create a keyboard shortcut to kill X.

Ctrl-Alt-Backspace is the usual shortcut for that and can be enabled via System -> Prefs -> Keyboard -> Layout -> Layout Options...

"killall X" will do it, as a command.

That might leave your running apps in a twisted state if you use one that doesn't handle a brutal shutdown gracefully, but it's your computer.

---

### Post by TryHarder on 2009-11-26
Actually I found a solution:
[HTML]xmodmap -e "keycode  22 = BackSpace"[/HTML]

Just need to make it autorun every startup of system. Thanks anyway.

---

