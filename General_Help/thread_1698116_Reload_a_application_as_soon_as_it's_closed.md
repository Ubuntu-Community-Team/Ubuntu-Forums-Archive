---
title: "Reload a application as soon as it's closed?"
date: 2011-03-01
forum: General Help
---

### Post by ojdon on 2011-03-01
Hi there, so I gave OnBoard, the pre-installed on screen keyboard a try earlier on, my only issue is that I keep pressing the "cross" to quit the application because it's a habit. I was wondering if there was a way to keep reloading it once it's been closed? Since then it saves me from constantly having to load it back up in the applications menu tab.

Thanks!

---

### Post by stinkeye on 2011-03-01
If your using compiz you can add it to 
**Non closable windows** in the window rules plugin of ccsm.
Use...```
class=Onboard
```


If you want to close onboard use
```
pkill onboard
```

---

### Post by ojdon on 2011-03-02
I'll take a look at that option today, though is there a non-compiz method of reloading onBoard each time it closes?

---

### Post by WorMzy on 2011-03-02
Put this into a script:

```
#!/bin/bash
while true; do
  onboard
done
```

I don't use onboard, so I can't say whether this will work or not. It may cause your computer to open up hundreds of onboard windows before crashing your PC. So don't try it if you have an important document (like an essay or something) open.

---

### Post by ojdon on 2011-03-02
Anyway of breaking the loop if it does open hundreds of onBoards?

---

### Post by mcduck on 2011-03-02
> **ojdon said:**
> Anyway of breaking the loop if it does open hundreds of onBoards?

Kill the script. "killall nameofthesript.sh". Or try it from a terminal first, so closing the terminal or hitting Ctrl-c will kill the script.

Anyway, it *shouldn't* open more than one instance of onBoard at a time, as the next step in a script is executed only after the previous one has completed. So the script would loop to start only when onBoard has closed.

(if you changed the command for onBoard in the script into "onboard &" to execute it in the background you *would* get lots and lots of onBoard instances, as executing the command in background would allow the script to progress to next command without having to wait for the previous one to complete)

---

