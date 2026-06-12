---
title: "Mouse click loop"
date: 2011-12-24
forum: General Help
---

### Post by pedrom169 on 2011-12-24
I run a script on windows which clicks a place on the screen then waits for a set amount of time then clicks another place in a loop so it continues i want it to stop.

Can this be acheieved on Ubuntu if so could you point me in the right direction? :)

Thank you

---

### Post by WorMzy on 2011-12-24
Have a look at xdotool.

e.g.

```
xdotool mousemove "100" "720"
xdotool click "1"
```

---

### Post by pedrom169 on 2011-12-31
is there any help sheets on how i can turn this into a looping script?

I am looking to swap over to ubuntu but this is the only thing that is stopping me

Thanks

---

### Post by WorMzy on 2011-12-31
Like this?: [https://www.linux.com/learn/tutorials/373609:essentials-of-bash-scripting-using-loops](https://www.linux.com/learn/tutorials/373609:essentials-of-bash-scripting-using-loops)

---

