---
title: "Terminal -- bug with text wrapping"
date: 2010-02-18
forum: General Help
---

### Post by Dunhausen on 2010-02-18
So let's say I'm typing commands on the terminal, and have a few lines long enough to be wrapped.

If I navigate back to those commands (with the up key) and try to modify them, the cursor position *as displayed* is not where the cursor actually is.

I.e., if the cursor ^ is positioned
"cd /hon^e"

and I do backspace --> 'm'

it will appear correctly as

"cd /home"

but when I press enter, what will actually happen is
" cd: /honm: No such file or directory"

(that is just an example, as mentioned, this only happens with lines long enough to be wrapped)

It is very annoying not being able to revisit/edit long commands--which are precisely the ones I don't want to retype!

---

### Post by gmargo on 2010-02-18
The terminal prompt is a line editor, not a full screen editor.  Hence you can use the left and right cursor keys (or ^B, ^F) to move horizontally.  But no up/down cursor keys.

This only scratches the surface.  There are many command-line-editing commands and methods. See the **bash** man page under "READLINE", or see the **bash** reference manual on command line editing: [http://www.gnu.org/software/bash/manual/bashref.html#Command-Line-Editing](http://www.gnu.org/software/bash/manual/bashref.html#Command-Line-Editing)

---

