---
title: "Is there any way i can stop Ubuntu 9.10 from doing this?(Mouse Issue)"
date: 2009-11-28
forum: General Help
---

### Post by JoeyF on 2009-11-28
It's kind of hard to explain.

When i use my mouse/Tablet pen and lift it up/Move it away, Instead of going to the place i last left it, It goes somewhere else. close to it though. Then i have to put it back where i want it. In other works i can't do something, Move it/leave it and continue where i left off.

It doesn't do it in Virtual Box though, Just in my dual boot.

I had 8.10, Went to 9.04. Still did it. I now have 9.10 and it still does it.

Like if i pause and lift the pen up it doesn't stay where i want it to.

Any idea?

It's really bothering me.

Thanks,

---

### Post by JoeyF on 2009-11-30
It does it on the live CD to.

Basically what i am asking is if there is any way to make the cursor work like it does in Windows.

---

### Post by Favux on 2009-12-01
Hi JoeyF,

What kind of tablet do you have?  If it's a Wacom one maybe what you are asking is to set it in Relative rather than Absolute mode.

---

### Post by JoeyF on 2009-12-03
> **Favux said:**
> Hi JoeyF,

What kind of tablet do you have?  If it's a Wacom one maybe what you are asking is to set it in Relative rather than Absolute mode.

It's a Wacom Bamboo fun. Anyway, I plugged in a normal USB mouse and it doesn't do that. How can i change the mode?

Thanks,

---

### Post by Favux on 2009-12-03
Hi JoeyF,

A couple ways to do it.  Basically you want the xsetwacom command:
```
xsetwacom set stylus mode relative
```
or 'absolute'.  If you have the default Karmic .fdi you'd have to rename stylus to whatever HAL was calling it (xinput --list).  I think it's easier to change the .fdi.  That makes the commands and wacomcpl easier to use.  See explanation, instructions, and modified .fdi in [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").

---

