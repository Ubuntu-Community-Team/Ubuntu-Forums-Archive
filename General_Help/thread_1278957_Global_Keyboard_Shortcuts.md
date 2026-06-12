---
title: "Global Keyboard Shortcuts"
date: 2009-09-30
forum: General Help
---

### Post by magnumstyle007 on 2009-09-30
Hello Everyone,

I want to assign a global shortcut for specific character string. For example:  { }.
Since I want to use the same shortcut within different environments (mathematica, text editor, kile, etc.), a global shortcut would be the most elegant solution.

I know how to set custom shortcuts to run a program, but I don't know how to implement this.

Thanks in advance, looking forward to your answers!

---

### Post by magnumstyle007 on 2009-09-30
I looked into the program autokey, but its either veeery slow or not working at all. Any Suggestions?

---

### Post by VCoolio on 2009-09-30
A command to paste where-ever the mouse is seems difficult (I didn't find anything for that), but you can settle down with two keystrokes. First you put what you want in the clipboard and then you just paste it with ctrl+v.

Command for first keybinding (xclip required):
echo "whatever you want pasted" | xclip

For multipe line text:
echo -e "whatever you want pasted \nAnd this on a new line" | xclip

Then paste.

---

### Post by Lekensteyn on 2009-09-30
I'm using Komodo Edit: [http://www.activestate.com/komodo_edit/](http://www.activestate.com/komodo_edit/).
That has an auto-complete feature for { } :)
Also supports many languages.
It might be something for you.

---

### Post by magnumstyle007 on 2009-10-01
Thank you for your help so far.
I settled with **xmacro (**[http://xmacro.sourceforge.net/](http://xmacro.sourceforge.net/)**)** for the moment. I wrote a few lines of code,

KeyStrPress ISO_Level3_Shift
KeyStrPress 7
KeyStrRelease 7
KeyStrPress 0
KeyStrRelease 0
KeyStrRelease ISO_Level3_Shift  

saved them as        brackets.xmacro, 
and , since if I want to use the command via system>>apps>>keyboard shortcuts
I created an additional file   brackest.sh :

#!/bin/sh
sleep 0.1
cat /home/mbauer/scripts/brackets.xmacro |xmacroplay :0.0 

which includes just the shell command.
This works, but the "feeling" is kind of awkward. Since the shortcut really performs the keystrokes, you have to release the hotkeys really fast in order to not interfere with the command. Also it could be faster.

But maybe someone can go from here. 

ps.: I ll have a look into Komodo. Thanks!

---

