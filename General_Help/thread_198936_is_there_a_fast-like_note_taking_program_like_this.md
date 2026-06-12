---
title: "is there a fast-like note taking program like this..."
date: 2006-06-18
forum: General Help
---

### Post by Patrick-Ruff on 2006-06-18
hey all, I was wondering if there was a note taking program like KeyNote for Windows (which was a GPL from sourceforge) I want a note taking program in which I could simply use the shortcut keys CTRL + ALT + Z to open up instantly, keynote only used up about 300kb of ram, and it was really light-weight and nice for a note taking program, I need this kind of oraganization in linux, I'm not using deskets or anything like that, anyone know any such programs?

---

### Post by Shay Stephens on 2006-06-18
[QUOTE=Patrick-Ruff]hey all, I was wondering if there was a note taking program like KeyNote for Windows (which was a GPL from sourceforge) I want a note taking program in which I could simply use the shortcut keys CTRL + ALT + Z to open up instantly, keynote only used up about 300kb of ram, and it was really light-weight and nice for a note taking program, I need this kind of oraganization in linux, I'm not using deskets or anything like that, anyone know any such programs?[/QUOTE]

I know it doesn't have all the bells you are probably looking for, but gedit looks like keynote (kind of).

But have you tried running keynote under wine?

---

### Post by Patrick-Ruff on 2006-06-18
keynote would look like crap unless it had all the gnome icons and all that stuff, so, I'de rather not run it under wine. and gedit isatn the kind of note-taking thing I'm looking for, the note taking thing I'm looking for has a base file, when it loads that base file is loaded with it, and all the notes you took are in that base file. unlike gedit, it keynote saves everything into 1 file, a literal note taking program.

---

### Post by aysiu on 2006-06-18
How about *kjots*?

---

### Post by Patrick-Ruff on 2006-06-18
I'll test it right now.

---

### Post by Patrick-Ruff on 2006-06-18
wtf, it wants me to download a bunch of stuff... is this a KDE app? it wants me to download 23MB worth of files, and I'm on dialup...

---

### Post by aysiu on 2006-06-18
Yeah, anything with *k* in front of the name is usually a KDE application.

---

### Post by Patrick-Ruff on 2006-06-18
ugh, well its gonna have to wait, I'm on dialup...

---

### Post by aysiu on 2006-06-18
What about *gjots2*?

---

### Post by Patrick-Ruff on 2006-06-18
I need one in which I would be able to assign a shortcut key where it would automatically pop up....

---

### Post by aysiu on 2006-06-18
You can assign a shortcut key for any command you want.

Press Alt-F2 and type ```
gconf-editor
``` and go to Apps > Metacity

In Keybinding Commands, select Command_1 and make it ```
gjots2
``` or whatever the command is.

In Global Keybindings, select Command_1 and make it the keyboard shortcut you want... <Control><Shift>j or whatever.

---

### Post by trash on 2006-06-18
Tomboy was ok but i haven't tried it sine Hoary.

---

### Post by NoWhereMan on 2006-06-18
maybe you may want to look at **zim**
but the version in the repos looks a little buggy

bye

---

### Post by 5-HT on 2006-06-18
Personally, I would just make up a little script that calls vim to open a certain file for me and assign a keyboard shortcut for the script.
That way you get a flexible and powerful text-editor with a small footprint that will open up a specific file at the press of a key combination.
As an additional bonus, the program should already be installed!

---

### Post by Patrick-Ruff on 2006-06-18
well I got gjots2 working fine :D, I love the tree system :). thanks again aysiu.

---

### Post by aysiu on 2006-06-18
By the way, I found *kjots* through a Synaptic Package Manager search by Name and Description for the word *notetaking*. When you said you didn't want a KDE application, I just searched for *gjots* just to see if it existed (on the off-chance it might).

Guess I was lucky. Glad it worked for you.

---

### Post by rshel on 2006-07-27
have you tried either freemind or tiddlywiki?  the both are platform independent, intuitive, and relatively small

---

