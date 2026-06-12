---
title: "Two minor problems with conky calendar"
date: 2012-05-06
forum: General Help
---

### Post by Bulettenschmied on 2012-05-06
Hi there,

I need advice to fix some blemish with my conky calendar.
First of all: The calendar-script looks like this

```
${voffset 3}${font courier:style=bold:size=9}${execpi 300 DJS=`date +%_d`; cal -h | sed '1d' | sed s/"$DJS"'\b'/'${color FF6600}'"$DJS"'$color'/}$font
```

It's working fine, no question about that. But there are two little things I'd like to change and somehow it doesn't work out the way I want it to.

1. The week in this calendar starts with Sunday, which is a fine day to start with, but I want it to be Monday. So somewhere I read that changing the code from "cal -h" to "cal -m" should fix this. But it doesn't. The only thing that changes is the fact, that the calendar disappears. So much for Monday.

2. My calendar sits on the left side of my conky. But in order to go along with all the other stuff, I want it to be centered, which looks better.
As I am a total noob concerning Lua (or what code this is written in) I figured, that the tags "goto" have something to do with horizontal alignment. So I added a nice "${goto 25}" to the code. 
Which indeed results in a transfer to the right - but also a coloring of all days after today instead of just today's day.

Any advice about these topics?

Best regards

---

### Post by Aestarita on 2012-10-20
For changing you week first day to monday simply change cal -h to  cal -m.
A little bit lat but I hope it helps

---

