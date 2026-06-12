---
title: "Floating point maths - BASH"
date: 2006-03-31
forum: General Help
---

### Post by jethro10 on 2006-03-31
Hi,
In this (simple) example, a script called from the nautilus shell shows its only working with integer maths. As it returns zero if, say, 5 files are selected.

#!/bin/bash
file_count=$#
curr_position=1
percent_count=$(((curr_position/file_count)*100))
zenity --error --title="Count" --text="your percent is $percent_count"

anyone tell me how to do the percent_count calculation to return a floating point number.

Ta
Jeff

---

### Post by nanotube on 2006-03-31
unfortunately, bash only does math with integers, as this excerpt from the "arithmetic evaluation" section of "man bash" shows:
> Evaluation  is done in fixed-width integers with no check for overflow...
so looks like you are out of luck.
but, here is a "trick" for you if you only want to get an integer percentage (eg 5, 6%, but not 5.3%). change your formula to the following:
```
percent_count=$((curr_position*100/file_count))
```
neat trick, eh? :) multiplying by 100 first, and then dividing, at least gets you the correct rounded percentage, instead of zero.

---

### Post by jethro10 on 2006-03-31
Thanks,
That'll do me Mr Tube (!)

ta
Jeff

---

### Post by nanotube on 2006-03-31
cool. :)

---

