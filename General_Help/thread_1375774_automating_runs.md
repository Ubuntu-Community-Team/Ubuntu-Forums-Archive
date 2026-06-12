---
title: "automating runs"
date: 2010-01-08
forum: General Help
---

### Post by ub007 on 2010-01-08
I've got a script running, which inturn spawns multiple child processes.
 How can I re-start the script immediately after all the child & parent processes of the first run finishes?

As I'm away for the weekend, I need to automate this.

So I would need some script that does the following
a)keeps checking status & informs when all parent & child processes end.
// that is the main bottle neck for me
b)once this happens,start the script again

Any ideas?

---

### Post by J V on 2010-01-08
Finish off the script with:
```
/path/to/this/script.sh&
```

You shoulden't do this though... infinite loops can be a bitch...

---

