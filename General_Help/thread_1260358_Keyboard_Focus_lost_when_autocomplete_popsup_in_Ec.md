---
title: "Keyboard Focus lost when autocomplete popsup in Eclipse IDE"
date: 2009-09-07
forum: General Help
---

### Post by omarello on 2009-09-07
Hello all,

I'm trying to find out if this was asked before, but it seems that no one ran into this issue in here.

My problem is with the Eclipse IDE, whenever the Code completion little window pops up (or if it is invioked by Ctrl+Space) I have the opportunity to enter one letter and then as soon as the little popup disappears, the window loses focus (or at least that's what i think) and it doesn't register any keystroked any more, and I cant type anything into the editor.

I have found this topic 

[http://ubuntuforums.org/showthread.php?t=836370&page=2]("http://ubuntuforums.org/showthread.php?t=836370&page=2")

and i figured that it might be related cause I experience this problem as well.

I am using 8.04 and eclipse galileo.

Also can anyone confirm that this is resolved in 9.04 or 9.10

Thank you for the help.

---

### Post by jekewa on 2010-01-26
I can confirm this is still happening in 9.10 in Eclipse and other applications.

The problem seems to be that the focus is not returned to the window that had a focus when the window that gains the focus disappears, whether this is a pop-up or some alert box or something.

In Eclipse, in particular since that's the issue you brought up, you can work around this by alt-tabbing to another window and back, or ctrl-tab or clicking on a different view or menu and then back on your editor (which of course risks moving your cursor or popping-up another window).

---

