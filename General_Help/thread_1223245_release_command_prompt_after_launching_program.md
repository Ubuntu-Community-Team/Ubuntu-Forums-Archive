---
title: "release command prompt after launching program?"
date: 2009-07-25
forum: General Help
---

### Post by nderic77 on 2009-07-25
Sorry, this is an absolute beginner-type question... what parameter do I use so that I can continue to use the command prompt after launching a program (without exiting said program)?

For example, if I wanted to open a terminal window and then launch gedit to edit a file named readme.txt, the command would be the following:

> gedit readme.txt

The terminal session then appears essentially "locked" until I close the gedit window. What can I type so that after gedit opens, I get back to the command prompt without first closing the gedit window?

Many thanks in advance.

---

### Post by bear24rw on 2009-07-25
try
```
gedit readme.txt &
```

---

### Post by nderic77 on 2009-07-25
That did the trick. Many thanks for the swift reply!

---

### Post by kerry_s on 2009-07-25
you should user alt+f2 for launching programs.

---

### Post by dlmarti on 2009-07-26
agree with the above, use alt-F2
Here is a review on the terminal stuff:
The character & after a command means run the program in background, but when you close the terminal the command will be removed also.

To detach the program from the terminal you would type:
nohup gedit file.txt &

nohup is like no-hang-up, so the terminal can close but the program continues to run.

NOTE: nohup creates a file in the current directory that will contain the output of the program (if any)

---

### Post by lykwydchykyn on 2009-07-26
"&disown" works too, e.g.
```

gedit somefile.txt &disown

```

Same thing as nohup, except it doesn't leave "nohup" files behind everywhere.

---

