---
title: "ANoting CApital LEtter PRoblem"
date: 2010-11-16
forum: General Help
---

### Post by Oded Dwek on 2010-11-16
***HEllo,*** (Hello)
I'm having weird  capital letter problem with linux ubuntu.

WHen ever I press caps lock to write a capital letter (only for the first word) it seems that also the second letter is getting the capital letter, even while the caps lock is off.

It usually happens when I type quick, if I wait ~500ms, the second letter doesn't input as a capital, it happens only at Linux Ubntu (I haven't tried any other linux distributions) and was tested on 3 different keyboards.

I'm not sure if its a bug or a feature (like "automatic capital letter" feature or something like that)

---

### Post by lotharmat on 2010-11-16
Attempting to Reproduce Problem

Failed..

Hmmmm.

---

### Post by WorMzy on 2010-11-16
Does the same thing happen if you use shift?

---

### Post by Oded Dwek on 2010-11-16
no it doesn't happen with shift

---

### Post by 3rdalbum on 2010-11-16
Funnily enough, I've seen threads about this before. It's a "problem" with Xorg as far as anyone can tell, and it happens with all distributions. However, probably nobody can notice it because usually people who've learnt to type quickly have also been taught to use Shift, not Caps Lock. It took me a fair amount of trying to actually reproduce the problem.

I'm not even sure if the Xorg developers know that this happens. They probably type the correct way, with Shift.

File a bug report with Xorg and see what happens; alternatively, change to use the Shift key.

---

