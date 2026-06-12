---
title: "Bash variable and /bin"
date: 2010-03-28
forum: General Help
---

### Post by J V on 2010-03-28
I'm making a script I want to be able to just call (ie, rclick instead of ./rclick) where do I put it?

~/bin?
/bin?
/usr/bin?

Also, how do I pass a variable to the script (rclick 10 will rightclick 10 times) (Found, so simple... $1)

Lastly, can I force it to run on CPU2? CPU1 is completley locked up if I run this on it... Or can I make it use less cpu cycles?

---

### Post by pbrane on 2010-03-28
I put my scripts in ~/bin. You can try using *taskset* to set the proc affinity. I've never used it for scripts. *man taskset* should help.

---

### Post by J V on 2010-03-28
Can I use taskset within the script? 
Taskset while [ bla bla bla ]
rather than call a second one from it?

(Possible for script to set its own affinity? by finding the PID using grep/ps aux)

Something like this?
```
ps -C %0
```

Edit: I've decided to go with cpu cycle reducing... How can I make the script use less cycles? (Its basicly a loop that rightclicks every time, any way to make it wait?)

---

