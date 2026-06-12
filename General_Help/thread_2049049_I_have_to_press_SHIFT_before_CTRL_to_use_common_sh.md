---
title: "I have to press SHIFT before CTRL to use common shortcuts"
date: 2012-08-27
forum: General Help
---

### Post by dekaru on 2012-08-27
After performing a clean install of Ubuntu 64b on my Gateway laptop, I discovered that some basic shortcuts no longer work as they used to.

For example, pressing CTRL + SHIFT + LEFT/RIGHT (selecting text until whitespace) or CTRL + SHIFT + TAB (go backwards one tab on Chrome/Firefox) or even CONTROL + SHIFT + V (pasting text on a terminal) doesn't work anymore.

What's weird, though, is that if I change the order and press first SHIFT + CTRL + LEFT, all shortcuts work correctly :/

Other shortcuts such as ALT + TAB (application switcher) and its respective ALT + SHIFT + TAB work regardless of the order they were pressed, as they're supposed to. Even CTRL+SHIFT+UP (or any combination of it) which I bound to VolUp works as it should.

I already checked for shortcuts bindings to the CTRL+SHIFT combination, but couldn't find any. 

Any ideas or how I could check what's blocking up my other CTRL+SHIFT shortcuts?


**Update:** I just realized this only happens with the left shift (SHIFT_L). I checked out my Keyboard layout and as I pressed the right ctrl+shift it works as expected, but on the left side I always have to press shift first, otherwise it doesn't get recognized.

---

### Post by dekaru on 2012-08-27
So apparently I DID have a keyboard shortcut set ... :lolflag: look in System Settings -> Keyboard -> Shortcuts ... and look WELL! :P

While doing some research, I found that the same behavior was found on a bug on launchpad that hasn't yet been marked as fixed:

[https://bugs.launchpad.net/xorg-server/+bug/36812?comments=all](https://bugs.launchpad.net/xorg-server/+bug/36812?comments=all)

However, I could fix this simply by disabling that shortcut.

---

