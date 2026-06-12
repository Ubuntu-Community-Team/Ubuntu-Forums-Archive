---
title: "Keyboard Layout"
date: 2010-06-05
forum: General Help
---

### Post by brezi on 2010-06-05
Hey All,

I upgraded from Karmic to Lucid last night, on my headless box that I access via VNC.

I noticed when ever I typed something, the keystrokes were messed up, for example if I type "qwerty" in any text editor I get "c.gvn".

I use a Logitech G-15 keyboard, prior to the upgrade it worked fine. I even made sure the option via "dpkg-reconfigure -plow console-setup" was set to "Logitech G-15"

When I view the keyboard preferences it shows "US 105-Key keyboard (with window keys).

Everything seems ok, but what the keyboard prints out!

Can anyone help me? I don't really feel like reinstalling again :{

- brez

---

### Post by brezi on 2010-06-05
Further to this, I VNC'd into this box from my laptop and my iPhone and I get the same output from keystrokes, so that kinda weighs out the keyboard being the issue.

---

### Post by brezi on 2010-06-08
In case anyone was wondering, I found a 'quick-fix' in some archives

Applications -> systems tools -> configuration editor ;then

desktop -> gnome -> peripherals -> keyboard -> kbd ;

in layouts, edit the value to "abfh" (this is the out put for asdf) close.

System -> Preferences -> Keyboard -> Layouts

Choose your layout of choice, and then click "apply system wide"

Restart your VNC/gnome session and it's fixed, even after rebooting!.

---

