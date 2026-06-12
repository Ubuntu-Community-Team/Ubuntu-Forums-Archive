---
title: "Some observations about directory naming"
date: 2010-12-12
forum: General Help
---

### Post by sofasurfer on 2010-12-12
I gave a directory the name of "file". I then did a "cd /home/daryl/file" which placed me in "file". I then renamed the directory to "file test". When I do an "ls/home/daryl" the directory "file test" shows up. But when I do a "cd /home/daryl/file test" I get a "No such file or directory".

Why are we allowed to name a directory with 2 seperated words and the directory can be listed with 2 seperated words but those 2 seperated words are not recognized as a legitimate name when doing a "cd"?

Another question is, can I add a "memo" or "note" to a directory name without having the memo be recognized as part of the name? In other words, I name a directory "important-stuff" but I want to include a memo that changes the name to "important-stuff (do not put dumb stuff in this directory)". Can I do something like this in such a way that I can "cd" to the directory by only typing "important-stuff"?

In other words I need some directory naming rules.

---

### Post by 3rdalbum on 2010-12-13
1. When using cd, put quotes around the folder path if there are spaces.

2. Symbolic links for the short name, linked to the folder with its full name. Make a link to your "Important Stuff (note)" folder, called simply "Important Stuff".

---

### Post by StephenDavison on 2010-12-13
A good place to start would be the man pages for sh (dash), bash, or whatever shell you're using.  Therein will be explained all the rules for the shell's grammar, and how to deal with special characters including white space.

Can't help you with the memo thing.  I'd just go with giving the directories meaning names like important-stuff and dumb-stuff.  Nautilus has a notes field for file and folder properties, but I've never used it and wouldn't know how to display those notes from a terminal.

---

### Post by sofasurfer on 2010-12-13
Quotes!!
Thats great. I have never seen mention of that. Works great.

But still looking for a way to give a directory a meaningful or discriptive name without having to type the whole thing to get to it.

Thanks.

---

