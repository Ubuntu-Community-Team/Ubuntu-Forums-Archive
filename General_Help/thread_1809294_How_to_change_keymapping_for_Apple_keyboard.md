---
title: "How to change keymapping for Apple keyboard"
date: 2011-07-21
forum: General Help
---

### Post by just1fix on 2011-07-21
Tried to search for the solution of this particular problem, but haven't found any clear explanations how to do it.
I have Ubuntu 10.04 (Netbook Remix) installed on Asus EeePC 1000. Sometimes I use Apple Wired Aluminum keyboard for comfortable typing. There is no problem for me with netbook's keyboard, but i want to change the keys for the Apple one.
For example: make F1-F12 keys really work like F-keys, not control keys; make Fn key to work like Insert key, and swap Cmd/Alt keys.
So, the main question - is it possible to change the layout of apple keyboard without changing the behavior of netbook keyboard?
If not, then maybe there are some "switchers" that can constantly change mappings from one to another and back?
And, at last, if there is no such tools, then what is the easiest way to do it manually?

P.S. The question is about X, but if there's some solution for console also it would be great!

---

### Post by enimeizoo on 2011-07-21
Well, to remap keys you can use loadkeys (console) or xmodmap ( X ). I'm not sure how to bind a layout to a keyboard, though. But it gives you a command to change layout, so you can bind it to a keyboard shortcut or something. You could even have it being executed when you plug or unplug the apple keyboard.

On a higher level, you got your desktop environment's keyboard layout configuration, which could be easier to configure if it offers the options you want. Since I haven't used gnome last year, and never usd unity, I'm not sure it will allow you what you want. But the kde interface for that is quite nice. It allows you to setup layouts and change them in a nice GUI, and allows you to bind shortcuts to change.

Hope it helps!

---

