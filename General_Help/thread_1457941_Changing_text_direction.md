---
title: "Changing text direction?"
date: 2010-04-19
forum: General Help
---

### Post by twanchic on 2010-04-19
:confused: I can't seem to find anywhere that allows me to change the direction in which text is displayed/entered. I'm trying to change from "left to right, top to bottom" to "top to bottom, left to right". 

I've been searching for a solution but I'm stumped.

---

### Post by viralmeme on 2010-04-19
> **twanchic said:**
> :confused: I can't seem to find anywhere that allows me to change the direction in which text is displayed/entered. I'm trying to change from "left to right, top to bottom" to "top to bottom, left to right". 

I've been searching for a solution but I'm stumped.
Entered in what, an application, a web form, or something else, give us a clue ...

---

### Post by twanchic on 2010-04-19
Oh sorry!

When entering text into gedit or any kind of text editor. I just want the text direction to be changed. I know it has to be something simple.

---

### Post by twanchic on 2010-04-19
Since this might be really confusing what I'm asking:

I'm trying to change the text orientation in which text is displayed when I enter it. I want to have something like gedit, vim, whatever, when I type in text, instead of it going left to right, top to bottom, it goes top to bottom, left to right. Think Chinese or Japanese type style, except still with Latin characters.

---

### Post by iponeverything on 2010-04-19
Install emacs!

Then do:

emacs -nw somefile

in emacs type 
Esc-x and type in picture-mode

Ctl-x s to save and exit.

To change directions see:

[http://www.gnu.org/software/emacs/manual/html_node/emacs/Insert-in-Picture.html#Insert-in-Picture](http://www.gnu.org/software/emacs/manual/html_node/emacs/Insert-in-Picture.html#Insert-in-Picture)

from the above link:
C-c <
C-c <LEFT>
    Move left after insertion (picture-movement-left).
C-c >
C-c <RIGHT>
    Move right after insertion (picture-movement-right).
C-c ^
C-c <UP>
    Move up after insertion (picture-movement-up).
C-c .
C-c <DOWN>
    Move down after insertion (picture-movement-down).
C-c `
C-c <HOME>
    Move up and left (&#8220;northwest&#8221;) after insertion (picture-movement-nw).
C-c '
C-c <prior>
    Move up and right (&#8220;northeast&#8221;) after insertion (picture-movement-ne).
C-c /
C-c <END>
    Move down and left (&#8220;southwest&#8221;) after insertion
    (picture-movement-sw).
C-c \
C-c <next>
    Move down and right (&#8220;southeast&#8221;) after insertion
    (picture-movement-se).

---

### Post by twanchic on 2010-04-19
Mad props thank you!

---

