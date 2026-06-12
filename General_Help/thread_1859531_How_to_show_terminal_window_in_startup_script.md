---
title: "How to show terminal window in startup script?"
date: 2011-10-14
forum: General Help
---

### Post by n00b512 on 2011-10-14
I made a startup script that displays some useful information in a terminal window.  I put a link into my rc5.d folder.  I know it is running properly because it outputs a file, only I can't see the terminal window.  I'm guessing there is some simple elegant way to tell init to run the script in the foreground only I haven't been able to find out how.

---

### Post by effenberg0x0 on 2011-10-14
```
DISPLAY=:0.0 /usr/bin/gnome-terminal
```

This will launch a terminal window in the GUI from the command line. Is it what you want?

Regards,
Effenberg

---

### Post by n00b512 on 2011-10-18
That looks right.  I even got it to work once.  I created a simple test  script with the terminal command just as you wrote, env, and touch, to  show whether it ran at all.  The terminal window came up right before  log in and stayed up after I logged in, which was nice.

Thinking all was well I deleted the test script and its links and put  the terminal line into my regular script, only no terminal window.   What's more odd is that when I recreated the test script it no longer  brought up the terminal window though other commands run.  In fact I've  tried creating half a dozen different test scripts at various points in  the run order, S20, S80, S99, none will bring up the terminal.  I even  tried putting the teminal command into rc.local but still nothing.

I haven't the foggiest idea why it would work once and never again.

---

