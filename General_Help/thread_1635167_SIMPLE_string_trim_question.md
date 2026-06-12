---
title: "SIMPLE string trim question"
date: 2010-12-01
forum: General Help
---

### Post by powertower1 on 2010-12-01
I have searched and found many ways to do this, but not quite the way I was looking for,  any help would be great...!!


I would like to keep this simple and if possible use a piped command as opposed to an all out complex method.

I have a script that does many things for me, and one of them builds a basic simple system report (I know about lshw, but this is for me to learn as well as be functional)

one place the command is
   ```
 less /proc/cpuinfo | grep "model name"
```

which removes all the cpu info that I do not want and simply gives me 
    model name	: Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GHz
    model name	: Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GHz
    model name	: Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GHz
    model name	: Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GHz
    model name	: Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GHz
    model name	: Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GHz
    model name	: Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GHz
    model name	: Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GHz


*** Several White spaces removed once I posted this, but I can tweak answers as needed later)


I would like to add another pipe to remove the
 "model name	: "  portion.

I do not really want to use the store in a variable first solutions if I can help it.


Thanks to all of the smart, talented and helpful people on Ubuntu forums!!

---

### Post by Slim Odds on 2010-12-01
```
 less /proc/cpuinfo | grep "model name" | sed 's/^.*: //g'
```You could use:```
 less /proc/cpuinfo | grep "model name" | sed 's/^.*: //g' | uniq
```To get only one line....

---

### Post by powertower1 on 2010-12-01
You rock!  thanks!  would you care to explain this answer so I can learn from it?    thanks either way

---

### Post by Slim Odds on 2010-12-01
> **powertower1 said:**
> You rock!  thanks!  would you care to explain this answer so I can learn from it?    thanks either way

sed is a simple little stream editor that comes in handy for these types of things. Your best bet is:```
man sed
```

the basic form 's/search/replace/g'

---

### Post by powertower1 on 2010-12-01
> **Slim Odds said:**
> sed is a simple little stream editor that comes in handy for these types of things. Your best bet is:```
man sed
```

the basic form 's/search/replace/g'

man sed was useful if you understood the regular expression,  [http://www.gnu.org/software/sed/manual/sed.html](http://www.gnu.org/software/sed/manual/sed.html) is where I am now.  thanks for all of your help!

---

### Post by aromo on 2010-12-01
> **Slim Odds said:**
> ```
 less /proc/cpuinfo | grep "model name" | sed 's/^.*: //g'
```You could use:```
 less /proc/cpuinfo | grep "model name" | sed 's/^.*: //g' | uniq
```To get only one line....

Just to improve on powertower1's solution, you may want to run uniq right after the grep, so sed has to process only one line:
```
 less /proc/cpuinfo | grep "model name" | uniq | sed 's/^.*: //g'
```

---

### Post by Slim Odds on 2010-12-01
> **aromo said:**
> Just to improve on powertower1's solution, you may want to run uniq right after the grep, so sed has to process only one line:
```
 less /proc/cpuinfo | grep "model name" | uniq | sed 's/^.*: //g'
```

LOL

True, I had not gotten to the optimization phase yet.... :)

---

### Post by powertower1 on 2010-12-01
You guys are awesome!  thank you so much!

---

