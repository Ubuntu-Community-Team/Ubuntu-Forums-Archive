---
title: "How do I create a custom keyboard layout?"
date: 2010-04-19
forum: General Help
---

### Post by josephellengar on 2010-04-19
I'd like to change around my keyboard layout a bit and can't figure out how.  I'd really like to swap f1 and f7, f11 and f2, right alt and escape, backspace and caps lock, and a few of the letter keys.  Is there any easy way to do this?  (It's a confusing story about why I want to swap the f keys)  Gnome, if it matters.

---

### Post by 405jayb on 2010-04-20
I swapped my f keys under System>Preference>keyboard shortcut. If an existing key is not listed there try to create it and set it to disabled.

---

### Post by josephellengar on 2010-04-20
> **405jayb said:**
> I swapped my f keys under System>Preference>keyboard shortcut. If an existing key is not listed there try to create it and set it to disabled.

Thank you.  That worked for those keys, but I still need a way to swap some letter keys and caps lock/escape.  It would be great if anybody knows of an application that could do that.

---

### Post by rnerwein on 2010-04-20
hi
if you are fimiliar with the usage of a terminal you can use in the terminal following commands.
xev  - to figure out the codes of your keyboard.
xmodmap -pke > mymap.txt   to get a ascii file you can edit to your behavior.
xmodmap mymap.txt   - to set the new values ( this is valid for the whole session )

for further information see: man xmodmap

ciao

---

### Post by roberto.tomas on 2010-05-20
> **rnerwein said:**
> 
xev  - to figure out the codes of your keyboard.
xmodmap -pke > mymap.txt   to get a ascii file you can edit to your behavior.
xmodmap mymap.txt   - to set the new values ( this is valid for the whole session )

that seems like it would work very naturally. 

can you say how I can add my custom keyboard layout to the System->Preferences->Keyboards Layouts tab in lucid, so I can select it to always load and be the primary keyboard layout when I log in?

---

### Post by josephellengar on 2010-05-20
> **roberto.tomas said:**
> that seems like it would work very naturally. 

can you say how I can add my custom keyboard layout to the System->Preferences->Keyboards Layouts tab in lucid, so I can select it to always load and be the primary keyboard layout when I log in?

Yeah that would be incredibly useful.

---

### Post by josephellengar on 2010-05-20
Also, I swapped backspace and capslock,but now caps lock is doing double duty as backspace and and caps lock.  It does the backspace, but also turns capslock on and off.  Perhaps that key is hardwired to do what it does, rather than being a software thing?

---

### Post by roberto.tomas on 2010-05-20
> **rossholley said:**
> Also, I swapped backspace and capslock,but now caps lock is doing double duty as backspace and and caps lock.  It does the backspace, but also turns capslock on and off.  Perhaps that key is hardwired to do what it does, rather than being a software thing?

I *think*, if you are following those instructions that say to disable lock, do the swap, then enable swap .. you can just skip that last command for the caps lock key and it will do what you want. The keyboard light will still probably toggle, but the system will ignore it -- at least, if I'm right. The last time I rewrote the caps lock key, I still had a 1024x768 screen :P

edit: I found the answer over the course of the evening today :) and I wrote it up into a howto on the ubuntu wiki: [https://help.ubuntu.com/community/Howto%3A%20Custom%20keyboard%20layout%20definitions]("https://help.ubuntu.com/community/Howto%3A%20Custom%20keyboard%20layout%20definitions")

---

