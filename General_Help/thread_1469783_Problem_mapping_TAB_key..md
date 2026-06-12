---
title: "Problem mapping TAB key."
date: 2010-05-02
forum: General Help
---

### Post by hrharr0 on 2010-05-02
Hi everyone, i need some help.

So, i have a laptop and my tab key broke, (i'm not changing the whole keyboard) so i decided to use de Caps Lock key as the Tab key..

Doing a little search i manage to do it with:
```
xmodmap -e "remove lock = Caps_Lock"
xmodmap -e "keycode 66=Tab"
```

Everything ok so far, the problem is when i want to Switch between windows using the Alt+Tab hotkey. When i have mapped the Caps Lock key working as tab it doesn't work at all.

BUT, if BEFORE i map the Caps Lock key to the Tab key, i set the option *"Move between windows, using popup window"* in the Keyboard Shortcuts to work with "Alt+Caps Lock", the Switch works ONLY with 2 windows, e.g: i have firefox, terminal and vlc opened, i press Alt+Caps Lock and switch from firefox to terminal, if i keep pressing Alt and press Caps Lock again, it wont move at all.

The weird thing is that if i change the Alt+Tab shortcut to something like Alt+a it works perfectly.

You can try changing that shortcut from Alt+Tab to Alt+Caps Lock and see if it works, i believe this is the normal behavior even if you don't map the key...

I use Ubuntu 10.04 but it happened the same exact thing on 9.10.

Ideas, anyone? Thank :)

---

### Post by hrharr0 on 2010-05-03
bump. anyone?

---

