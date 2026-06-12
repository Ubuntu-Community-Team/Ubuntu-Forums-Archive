---
title: "How to modify a locale file in Ubuntu?"
date: 2011-08-13
forum: General Help
---

### Post by ergys on 2011-08-13
Hi there.
I'm a new user of Ubuntu and I'd like to know is there any way to modify (open and write) a locale file of this system. Of course there is, but I don't know where to start.
I don't like the way the Albanian keyboard layout is. It changes a lot from the English keyboard layout on QWERTY keyboards. While the English one is qwertyuiop[], the Albanian one goes like qwertzuiopç@ - that said, meaning a lot of other changes, like punctuation marks, etc, etc. I mean, the keyboard changes completely.
As an old user of Windows, I managed a long time ago to change firstly the .kbd file, than the .dll file of the Albanian layout, using firsthand the US English keyboard layout. My version of Albanian keyboard layout becomes qwertyuiopëç, leaving all the other tastes the same as in the English layout. This way, I had the same English layout (giving me the possibility to use "w" when writing in English) and the Albanian layout (adding "ë" and "ç", two special letters that Albanian has more than the 26 letters of English, thus writing in Albanian the same time, without changing the keyboard layout). In the rare cases I needed the square brackets "[" and "]", I switched the layout, but I can say I didn't miss those brackets that much.
I'd like to do in Ubuntu the same I did In Windows, but this is a completely new op system I don't know where to start. If anyone could help and give some suggestions, that would be appreciated.

---

### Post by lmarmisa on 2011-08-13
Welcome to the forums.

I think that the Albanian keyboard layout is supported by Ubuntu. You do not have to edit any file manually. You can use a graphical interface for selecting your keyboard layout.

Try System -> Preferences -> Keyboard -> Layouts and add your Albanian keyboard.

---

### Post by ergys on 2011-08-13
> **lmarmisa said:**
> Welcome to the forums.

I think that the Albanian keyboard layout is supported by Ubuntu. You do not have to edit any file manually. You can use a graphical interface for selecting your keyboard layout.

Try System -> Preferences -> Keyboard -> Layouts and add your Albanian keyboard.


Thank you for your reply, but I think you misunderstood me. I have already installed the Albanian keyboard. I don't like the way it's configured. I'd like to reconfigure it the way the English keyboard is, with the minor changes mentioned in my post. That's why I want to know where are the locale files localised and how to change / write them.

---

### Post by knutschr on 2011-08-13
In a terminal, run
```
sudo xkeymaps
```
There you can change your layout.
Save the whole new layout, not just the changes.
At restart, you will have an option to make the changes permanent.

---

### Post by ergys on 2011-08-19
> **knutschr said:**
> In a terminal, run
```
sudo xkeymaps
```There you can change your layout.
Save the whole new layout, not just the changes.
At restart, you will have an option to make the changes permanent.

Thank you, but I tried for 2 days to make the "xkeymaps" work and I failed. No such command - and googling about it gave almost none results. 
But I managed another way, given a suggestion in another site. It's very simple.
Edit the "us" file in usr/share/x11/xkb/symbols with root privileges with a simple text editor, or better go to the terminal and use

sudo gedit /usr/share/x11/xkb/symbols/us

and there you can make any changes you want. I first changed the basic us keyboard layout, but I wasn't satisfied, because I wanted to have a chance to use square brackets, when needed.
So I modified the keys at   name[Group1]= "USA - International (with dead keys)" and now I'm using only the USA International AltGr with Dead Keys as keyboard layout. More than satisfied for my needs.

---

