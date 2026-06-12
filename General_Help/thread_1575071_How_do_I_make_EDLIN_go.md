---
title: "How do I make EDLIN go ?"
date: 2010-09-15
forum: General Help
---

### Post by Gordonisnz on 2010-09-15
Hi, 

[http://sourceforge.net/projects/freedos-edlin/](http://sourceforge.net/projects/freedos-edlin/) >> Downloaded.

I've maked, Installed, Compiled & whatever else i need to do.. & nothing seems to work..

is there a dummies guide to putting 'Edlin' on My Linux machine & able to edit files with edlin ?

EG :-  right-click, Open file with >> Edlin  :)  (happy editor...) 

(ubuntu 10 something)

Ps, i do see a 'kitty' subfolder - But no pics of cute cats.

---

### Post by Gordonisnz on 2010-09-15
Ps, all I want is something that does *nix newlines

---

### Post by The Cog on 2010-09-15
My understanding is that edlin was a particularly difficult to use text editor for DOS. It looks from your link that freedos-edlin can also be compiled for posix systems. But it is a command-line editor, not a GUI one. Assuming you have compiled it for Linux, you should be able to use it from the command line. Open a command prompt and enter the command:
edlin filename
replacing "filename" with the name of the file you want to edit.

> Ps, all I want is something that does *nix newlines
Not sure what that means. If you're looking for a GUI editor that handles different line ending types, I suggest geany (it's in the repositories). The line ending type (Win/Unix/Mac) is in the document properties menu.

---

