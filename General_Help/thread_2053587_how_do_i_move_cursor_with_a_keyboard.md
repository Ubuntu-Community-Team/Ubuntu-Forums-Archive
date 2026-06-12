---
title: "how do i move cursor with a keyboard?"
date: 2012-09-05
forum: General Help
---

### Post by Kaiyal on 2012-09-05
ive looked for lots of threads on this but i do not have a keypad nor a numlock key on my keyboard.

im looking for any way, either setting or other program that i can use/download to customize my keys in some way to make the arrow keys on my keyboard move the cursor on my screen.

---

### Post by pqwoerituytrueiwoq on 2012-09-05
look in your mouse/accessibility preferences
if you want something more powerful look at xdotool and combine it with hot keys

---

### Post by Kaiyal on 2012-09-05
> **pqwoerituytrueiwoq said:**
> look in your mouse/accessibility preferences
if you want something more powerful look at xdotool and combine it with hot keys

already tried, no idea how to use it, doesnt pop up as an icon nor does any command ive tried or looked up allow me to use it in the terminal.

---

### Post by pqwoerituytrueiwoq on 2012-09-05
down 5px and left 5px
```
xdotool mousemove_relative 5 5
```
up 5px and left 5px
```
xdotool mousemove_relative 5 -5
```

---

### Post by Kaiyal on 2012-09-05
how does that help me move the cursor with my keyboard? not a terminal window

---

### Post by pqwoerituytrueiwoq on 2012-09-07
set the command as a keyboard shortcut

---

