---
title: "Running processes from a terminal window"
date: 2009-09-29
forum: General Help
---

### Post by Volt9000 on 2009-09-29
When I run a process from a terminal window, even if I send the process to run in the background, when I exit from the terminal the process terminates. For example, if I run Songbird

```

./songbird &

```

in the background, all is well, but as soon as I type "exit", Songbird closes along with the terminal window. Is there any way to avoid this, besides the obvious of not exiting out of the console?

---

### Post by Johnny B on 2009-09-29
try
> nohup ./songbird

---

### Post by Volt9000 on 2009-09-30
Thanks, but for some reason the programs don't close anymore. :confused:

I think this is since I rebooted; not sure what changed.

Thanks anyways.

---

### Post by Volt9000 on 2009-10-02
Ok I figured out what's going on.

If I run a program from a terminal window, then close the terminal window by clicking the [X], then the program will close. If I exit the terminal window by typing "exit", the program remains.

I tried the former with nohup as Johnny B suggested, and it worked! Thanks!

---

