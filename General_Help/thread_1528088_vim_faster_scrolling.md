---
title: "vim faster scrolling"
date: 2010-07-10
forum: General Help
---

### Post by l3ecl on 2010-07-10
when i press the k or j buttons, vim scrolls down one line, but lets say i want it to scroll 3 lines to make it faster, how do i do this?

what code do i add under my vimrc file?

---

### Post by blueridgedog on 2010-07-10
You can scroll several thousand lines in a few seconds with ctrl-F or ctrl-B (scroll one page forward or back).  You can also enter a number of lines to move up or down, then press enter (1000 ENTER, -500 ENTER).

---

### Post by DaithiF on 2010-07-10
you can prefix most commands by a number in vim to execute that command multiple times.  so 5j will move down 5 lines, 5k back up 5, etc.

Ctrl-F, Ctrl-B are also very useful, as mentioned by previous poster.

you could also make the j, k keys scroll by more than one line at a time if you really wanted to.  As an example, put this in your .vimrc
```
function MultiScroll(OnOff)
if a:OnOff == 1
  noremap j 5j
  noremap k 5k
else
  noremap j j
  noremap k k
endif
endfunction 

map \j :call MultiScroll(1)<RETURN>
map \k :call MultiScroll(0)<RETURN>

```
then \j puts you into 'MultiScroll' mode where you go up / down 5 lines at a time rather than 1.  \k puts you back into normal 1-line at a time mode.  Maybe useful when scanning quickly up/down through a file.

---

