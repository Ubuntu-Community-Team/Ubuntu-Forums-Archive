---
title: "Vim run &quot;clear&quot; on exit?"
date: 2011-02-09
forum: General Help
---

### Post by ac90b671 on 2011-02-09
I'd like to have my vim clear the term on exit. Is there a way to edit the .vimrc to run :!clear on exit? Thanks.

---

### Post by DaithiF on 2011-02-09
first a question -- what do you see on screen now when you exit vim ... do you see the contents of the last vim buffer you edited, or do you see the terminal as it was before you invoked vim?

if the former, adding this to your .vimrc should do what you need:
```
au VimLeave * :!clear
```

if the latter then its a little more complicated:
```
set t_te= t_ti=
au VimLeave * :!clear

```

:help xterm-screens for more info

---

### Post by ac90b671 on 2011-02-09
```
au VimLeave * :!clear
```
Just that line works for me. After playing around with it, I noticed in gnome-terminal,vim exits nicely, but it's only in tty that vim exits leaving its frame buffer on screen. That code clears the buffer. Helps me realize I'm out of vim. Thanks for the help.

---

