---
title: "Need help whenever someone can offer it."
date: 2012-09-02
forum: General Help
---

### Post by Duckking man on 2012-09-02
So, I recently wiped my HDD on my netbook and installed Ubuntu 12.04 LTS 32-bit version, haven't regreted any of it.  Anyways, I went into the keyboard through system settings and mapped my volume controls to F10-F12.  I also wanted to map VLC media player to control+v so I could easily bring it up (I already have it on the left list thing, I just wanted a key-binding as well).  Do I need to write a script that opens it and make that file the command?  I also have Config Editor if that helps.  Also, can someone tell me what the values that you need to enter in Config Editor are?  Lastly, if a script is needed, does anyone have a script where I can just alter it to access VLC laying around?

---

### Post by opensshd on 2012-09-02
You should be able to make a custom shortcut in settings - keyboard as well.

---

### Post by HermanAB on 2012-09-02
Control-v is the paste command.  Maybe try Alt-v instead.

---

### Post by Duckking man on 2012-09-02
My main issue is that I don't know what to put in the command field in system settings or the value field in gconf-editor.  I put in vlc and it doesn't work, it also doesn't work with /usr/bin/vlc.  If someone could tell me what I need to put in there, it would really help.  I do thank the other two posters though.

---

### Post by opensshd on 2012-09-04
I simple put vlc in both fields, then clicked on the shortcut to the right where it should say disabled, entered new shortcut key combo, and worked for me.

When you click on 'disabled' it should change to say "new accelerator"

That's when you enter the key combination of your choice for vlc. After you press your desired shortcut, you should see it updated to what you pressed.

---

### Post by Duckking man on 2012-09-05
Thanks.  I put vlc in both fields and it worked.  My guess is because vlc is its name in /usr/bin.  I'll be sure to try those names first, whenever I try to make a shortcut.

---

### Post by opensshd on 2012-09-09
Yah any command in your path will work there.

---

