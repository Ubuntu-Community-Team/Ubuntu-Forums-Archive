---
title: "Permissions nightmare"
date: 2011-08-16
forum: General Help
---

### Post by enduser on 2011-08-16
I'm not angry, I'm genuinely wondering.

Why can't I drag and drop a tarball from the desktop to the usr/local folder? It's a 1 second wrist motion, I'm not executing or overwriting. I'm placing a new file. I should not need to open up a terminal and begin pathing by hand. Especially when items frequently are not "findable" by the terminal (despite their path being %100 accurate)

I don't NEED to permanently log in as root, but I did it before and everything worked great.

I just don't WANT to spend ANY time in the terminal because I want GUI control over my system: Root is my ideal setup right?

Is there a way to specifically assign the mouse root permission?

I noticed that the forums "allow root to login" solution is no longer valid (system>login>allow root) isn't in the menu anymore.

How do I login as root permanently (knowing the risks)  (at least long enough to install the stuff graphically the way I want to, and then log back out)

Also, can I delete my home folder and my user account as root without breaking my system?  (They feel like bloat)

Ive tried other distros. But this is my "break it for fun" computer. Ubuntu is the best DE.  I'm trying to permanently migrate away from windows.

Also Celtx should be in synaptic. Between the Ubuntu and Celtx forums you can see many have install issues. It needs to be simplified to just a couple clicks.

---

### Post by gandaran on 2011-08-16
> I just don't WANT to spend ANY time in the terminal because I want GUI control over my system: Root is my ideal setup right?
the terminal with move command would be the easiest and secure way but if you want gui then just open root nautilus, (create a launcher for root nautilus on the applications menu) or type in terminal
```
gksudo nautilus
```

---

### Post by enduser on 2011-08-16
I did that a minute ago, but it just makes the screen blink. For some reason (on this and my previous build) gksudo nautillus doesn't produce any result.

nothing pops up after the blink.

(thank you for your prompt reply though)


**** oh hey that worked. Turns out I'm  a bad typist. No wonder I don't like terminal.  (there is only one l in nautilus :) )

---

