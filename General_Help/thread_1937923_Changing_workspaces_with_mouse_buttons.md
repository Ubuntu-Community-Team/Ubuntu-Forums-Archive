---
title: "Changing workspaces with mouse buttons?"
date: 2012-03-08
forum: General Help
---

### Post by layers on 2012-03-08
I was wondering if anyone had done it?

---

### Post by lechien73 on 2012-03-08
I've never tried it, but I know you can set it by going into **CompizConfig Settings Manager (ccsm)**, then going to: **Desktop -> Desktop Wall -> Bindings -> Move Within Wall**.

---

### Post by layers on 2012-03-08
thanks. do you know how I can identify the button 1, button 2 and  so forth? I tried setting them but I click and nothing happens...

---

### Post by larrypg on 2012-03-08
hello,

Not sure if you are talking about your scroll wheel or not but I think scroll up is 4 and scroll down is 5 (might be reversed though)

---

### Post by layers on 2012-03-08
> **larrypg said:**
> hello,

Not sure if you are talking about your scroll wheel or not but I think scroll up is 4 and scroll down is 5 (might be reversed though)

yeah, there is

scroll up
scroll down
scroll left
scroll right
scroll downwards (into the mouse)
go back
go forward
and a middle key which i use to open new tabs in chrome, but me thinks its supposed to be a search button
and of course the right and left click

Im trying to change workspaces with the mouse entirely, but would also be happy with Ctrl+mouse button

the nano vx

---

### Post by lechien73 on 2012-03-09
If you open a terminal window and run:

```
xev
```

A small window will pop up, and in the terminal window you'll see lots of codes - which is a list of the events that the X system is receiving.

Move your mouse over the small window and move your scroll wheel, or press mouse buttons. You'll see events appear in the terminal window like the following:

```
ButtonRelease event, serial 36, synthetic NO, window 0x2e00001,
    root 0xb0, subw 0x2e00002, time 68978404, (27,27), root:(818,80),
    state 0x410, button 3, same_screen YES
```

The key here is the "button 3", which corresponds to the right mouse button on my mouse (button 1 is left, 2 middle, etc.)

Using this, you can identify the correct button numbers.

---

