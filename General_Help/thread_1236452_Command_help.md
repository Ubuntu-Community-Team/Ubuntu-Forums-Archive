---
title: "Command help"
date: 2009-08-10
forum: General Help
---

### Post by Psycho.mario on 2009-08-10
[LEFT]I was reading the malicious commands thread, and i saw this command:
[/LEFT]

```
:(){:|:&};:
``` (WARNING, DO NOT RUN!!!!!)

I was just wondering, why does it do what it does? (Spawns processes until the system crashes)

---

### Post by sisco311 on 2009-08-10
It's a recursive function, a [fork bomb]("http://en.wikipedia.org/wiki/Fork_bomb").

---

### Post by asmoore82 on 2009-08-10
to understand, change the : to a string and properly space it out...
it is a function declaration and the function runs another copy
of itself and pipes it to another copy of iteslf

After the function declaration is over, it calls the function to get the ball rolling.

**[COLOR="Red"]_DO NOT RUN THIS_[/COLOR]**
```
forkbomb () {
   forkbomb | forkbomb &
}
**[COLOR="Red"]#[/COLOR]**forkbomb
```
**[COLOR="Red"]_DO NOT RUN THIS_[/COLOR]**

---

### Post by Psycho.mario on 2009-08-10
Found:
```

:()      # define ':' -- whenever we say ':', do this:
{        # beginning of what to do when we say ':'
    :    # load another copy of the ':' function into memory...
    |    # ...and pipe its output to...
    :    # ...another copy of ':' function, which has to be loaded into memory
         # (therefore, ':|:' simply gets two copies of ':' loaded whenever ':' is called)
    &    # disown the functions -- if the first ':' is killed, all of the functions that it has started should NOT be auto-killed
}        # end of what to do when we say ':'
;        # Having defined ':', we should now...
:        # ...call ':', initiating a chain-reaction: each ':' will start two more.

```

Thanks for the help

---

