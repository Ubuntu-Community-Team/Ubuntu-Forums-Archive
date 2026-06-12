---
title: "show number of days since january 1 on orage"
date: 2010-01-20
forum: General Help
---

### Post by GOwin on 2010-01-20
I'm using the XFCE desktop and the orage clock applet.

Is there any way I can display the number of days elapsed since 1st of January of the current year?

Can't seem to fine an strftime function for it.

---

### Post by user1397 on 2010-01-20
> **GOwin said:**
> I'm using the XFCE desktop and the orage clock applet.

Is there any way I can display the number of days elapsed since 1st of January of the current year?

Can't seem to fine an strftime function for it.why not just use a calendar?

---

### Post by GOwin on 2010-01-20
> **ubuntuman001 said:**
> why not just use a calendar?

Why, do you see it in your calendar? Please tell me how you did it.

---

### Post by user1397 on 2010-01-21
> **GOwin said:**
> Why, do you see it in your calendar? Please tell me how you did it.
i mean january 1st of this year didn't happen too long ago...like 20 days ago now...

i just use addition/subtraction

---

### Post by GOwin on 2010-01-21
> **ubuntuman001 said:**
> i mean january 1st of this year didn't happen too long ago...like 20 days ago now...

i just use addition/subtraction

good for you! if it isn't so obvious, you wouldn't think I could've done the same noh? wow. simple subtraction. you don't even need addition.
 
anyway, i wrote a script to work around it so I can run it quickly when I run out of fingers to use when subtracting the current date from the first day of the year. i then used notify-send to get desktop notifications, which i later changed to zenity because I get to copy results, too.

still looking for how it could be done in Orage as a tooltip,  if it's doable at all.

---

### Post by iponeverything on 2010-01-21
This will get it from the command line:

```
date +%j
```

---

### Post by GOwin on 2010-01-21
@ iponeverything
excellent! it evens works with orage

---

### Post by user1397 on 2010-01-22
> **GOwin said:**
> good for you! if it isn't so obvious, you wouldn't think I could've done the same noh? wow. simple subtraction. you don't even need addition.
 
anyway, i wrote a script to work around it so I can run it quickly when I run out of fingers to use when subtracting the current date from the first day of the year. i then used notify-send to get desktop notifications, which i later changed to zenity because I get to copy results, too.

still looking for how it could be done in Orage as a tooltip,  if it's doable at all.Ah! Now I see what you meant, sorry for the banal statement I made, I was really confused about your topic, but no more!

Again, I apologize.

---

