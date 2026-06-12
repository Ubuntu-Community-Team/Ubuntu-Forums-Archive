---
title: "Clear &quot;tilde key&quot; shortcut"
date: 2012-04-01
forum: General Help
---

### Post by LoganLockwood on 2012-04-01
Hello. :KS

I want to clear the ALT + TILDE-KEY shortcut (that is the key above TAB), but it doesn't appear in the **System Settings - Keyboard - Shortcuts** panel.

Or if it does, I don't recognize it.

I just want the tilde key to be free so that I can use it as a shortcut in World of Warcraft again.

Thank you in advance.

---

### Post by stinkeye on 2012-04-02
alt+tilde is used by compiz in the unity plugin.
Open ccsm , click on Advanced search in the bottom left, tick settings value
and paste **<Alt>grave** in the filter box.

---

### Post by harce on 2012-04-30
I have the same problem. Thanks for the tip, but it's not there...

---

### Post by stinkeye on 2012-04-30
It's no longer a default keybinding in ccsm so you you should be able to use
alt+~ as a keyboard shortcut.

---

### Post by harce on 2012-04-30
it seems it is still a default key binding for unity, maybe not set in ccsm but neither in any other place I've checked (all the relevant ones)

---

### Post by stinkeye on 2012-04-30
Are you using alt+tilde or trying to use just tilde?

---

### Post by shoonsk8 on 2012-07-01
alt+tilde is set as disabled in ubuntu 12.04 but actually it works even though it is supposed to be disabled and it really annoys me a lot.
Because alt+tilde has been switching Japanese and English input and Windows and past ubuntu has been using the short cut. I hope someone fix the bug that is "disable" means it is really "disabled".

---

### Post by 451F on 2012-08-16
Finally, I found solution.
[solution on Ask Ubuntu]("http://askubuntu.com/questions/175696/why-isnt-the-alt-shortcut-working-on-my-international-keyboard").

In general, you need to enable "key to flip throught windows in the switcher" in Ubuntu Unity Plugin on CCSM, map it to Alt+` key and disable this option. Works for me perfectly

---

