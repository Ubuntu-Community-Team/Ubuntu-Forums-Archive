---
title: "Clock applet date format"
date: 2010-04-28
forum: General Help
---

### Post by The Maxx on 2010-04-28
[LEFT]Hi, I'm sorry if this has been asked before but I could find nothing on it. I want to change the date format for the clock in the upper right corner of the screen so that instead of reading [Wed 28 Apr, 11:51 AM] I will say [Wed 11:51 AM]. If anyone can tell me what I have to do to change it, it would be much appreciated.[/LEFT]

---

### Post by wojox on 2010-04-28
Sure go to Alt+F2 type in gconf-editor

Go down to apps/panel/applet/clock_screen0/prefs

Change format to custom

In custom format put this %a %H:%M

---

### Post by The Maxx on 2010-04-28
:) Thanks! easy enough. One thing though, what would I have to enter to get it to display AM or PM?

---

### Post by wojox on 2010-04-28
Try adding a %p to the end.

---

### Post by sisco311 on 2010-04-28
> **The Maxx said:**
> :) Thanks! easy enough. One thing though, what would I have to enter to get it to display AM or PM?

 for a list of format options open a terminal (Applications -> Accessories -> Terminal) and run:
```

man date | less +/"FORMAT controls"

```
use the arrow keys to scroll down/up the page, press q to quit.

---

### Post by The Maxx on 2010-04-28
> **wojox said:**
> Try adding a %p to the end.
Ah, that worked thanks!
> **sisco311 said:**
> for a list of format options open a terminal (Applications -> Accessories -> Terminal) and run:
```

man date | less +/"FORMAT controls"

```use the arrow keys to scroll down/up the page, press q to quit.

Oh, cool thanks I was just looking for something like that.

---

### Post by leomeloxp on 2010-12-07
Hi there,

I'm not sure if I should be posting it in here, sorry if it's wrong.

I have a question, how can I set the calendar below the Clock on panel to start its weeks on Sunday? I looked around the settings and manual but couldn't find it. I just found how to eliminate the week numbers.

If anyone can help me, thanks =]

---

