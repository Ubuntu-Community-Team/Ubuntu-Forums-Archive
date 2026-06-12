---
title: "Octave-3.0.1 Terminal Window"
date: 2009-07-30
forum: General Help
---

### Post by Nugget_Mon on 2009-07-30
I am looking for help with two things:
#1
I have created a Terminal Profile for Octave that I would like to use whenever Octave is launched. Even for multiple instances.

#2
How do I set up the "less" pager to open in a new terminal window (or new tab) when called. For example if I am formating an output string and I want to call up 
octave 3:>>doc sprintf();
I want the results output to the pager in a new terminal. 
However if I do something simple like 
octave 4:>> help dot
it could be in the same open window.
So far I have been just using two or more terminal windows, but it is not very fluid.

---

### Post by jpkotta on 2009-08-01
I am completely unfamiliar with Gnome Terminal.  This will pop up a new (rxvt) terminal with an octave help command in less:
```

cmd_template = "rxvt -e sh -c 'octave --interactive --eval \"help %s\" | less'";
cmd = sprintf(cmd_template, "dot");
system(cmd, 0, "async");

```
You will probably want to put that in a function.  You will probably also want to make sure the DISPLAY environment variable is set, and fall back on the normal help function if it isn't.

---

### Post by Nugget_Mon on 2009-08-12
Thank you, that'll do nicely.

---

