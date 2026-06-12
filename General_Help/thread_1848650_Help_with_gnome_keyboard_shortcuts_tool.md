---
title: "Help with gnome keyboard shortcuts tool"
date: 2011-09-22
forum: General Help
---

### Post by josephellengar on 2011-09-22
Hi. I'm using Gnome 2.32. I don't know if it's just me or what, but it seems like the keyboard shortcuts tool is just obnoxious. Right now I have a shortcut set up: nautilus /home/me/flash. Whenever I try to put a shortcut into this, it always automatically captures the first key I press but ignores the subsequent keys. I am trying to make the shortcut <mod4>+y, but it always captures only <mod4> or tells me that I can't have a shortcut that is just y.

This happens to me every time I try to use the tool. I always have to pound on the keyboard for about half an hour until it finally is willing to capture both keys at once. I don't know why this happens. I don't want to use the metacity or compiz shortcut tool, because I like to keep my shortcuts/settings in the same place. Any advice?

And seriously, I have like 15 shortcuts set up that I use every day, so I have no idea why this is happening.

---

### Post by josephellengar on 2011-09-22
Never mind. I found it. gconf-editor look for the key /desktop/gnome/keybindings

Then you look through those and find the one with your shortcut on it. Works a whole lot better than the stupid keyboard shortcut tool. It really should have a capture key combo ability.

---

