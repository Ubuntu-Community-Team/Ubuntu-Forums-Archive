---
title: "Conky Irritation"
date: 2012-07-08
forum: General Help
---

### Post by moore.bryan on 2012-07-08
Trying to get conky to obey my max width settings, but no matter what I put in it does whatever it wants to. Halp?

Here's my conkyrc: [http://pastebin.ubuntu.com/1081321/](http://pastebin.ubuntu.com/1081321/)

---

### Post by jmfal on 2012-07-08
What is "doing whatever it wants" ?

Did you copy from somebody else and change the font size,  conky will go by the height/width settings but the font size might cause everything to move around.

---

### Post by moore.bryan on 2012-07-08
> **jmfal said:**
> What is "doing whatever it wants" ?
Despite me setting the max width for the conky window, it "chooses" to be whatever size it wants. Even if I set the allowable width of text, it doesn't obey that setting either.

[quote=jmfal]Did you copy from somebody else and change the font size,  conky will go by the height/width settings but the font size might cause everything to move around.[/QUOTE]
All OC...

---

### Post by jmfal on 2012-07-08
Without seeing your conky I would say that you need to use {goto  xx}

Which will set what you put after that at xx (pixels) from left border of conky, otherwise every thing is set to display from left to right,  and bunched up to the left side of your conky

say you set hwom sda to {goto  90} it will display starting from the 90th pixel and to the right.

Use screenruler, set it to pixel, and you can drag it around and get a good approximation of where you should put {goto xx} 

```
  NAME                    PID       CPU%    MEM%
${color 000080}${top name 1} ${goto 120}${top pid 1} ${goto 170}${top cpu 1} ${goto 220}${top mem 1}
${top name 2} ${goto 120}${top pid 2} ${goto 170}${top cpu 2} ${goto 220}${top mem 2}
${top name 3} ${goto 120}${top pid 3} ${goto 170}${top cpu 3} ${goto 220}${top mem 3}
${top name 4} ${goto 120}${top pid 4} ${goto 170}${top cpu 4} ${goto 220}${top mem 4}
${top name 5} ${goto 120}${top pid 5} ${goto 170}${top cpu 5} ${goto 220}${top mem 5}$color        
```

---

### Post by moore.bryan on 2012-07-08
I don't need a "margin" or an indent on one side of the text, I just don't want the entire conky window to go past a certain pixel.

I've attached a screenshot of my conky right now, with the conkyrc I pastebin-ed.

---

### Post by jmfal on 2012-07-08
OK then try changing lines 17, 18 your gaps are set to zero and that lets conky go to edge of screen and possibly off the screen
try ===gap_x  10
              gap_y  10

---

### Post by stinkeye on 2012-07-08
There is no such setting as..
```
maximum_size
```

Use this to fix the width at 500.
```
minimum_size 500
maximum_width 500
```

May need to  make it bigger to accommodate longer months.

---

### Post by moore.bryan on 2012-07-09
> **stinkeye said:**
> There is no such setting as..
```
maximum_size
```
Thanks for this... I misread the man page.

---

