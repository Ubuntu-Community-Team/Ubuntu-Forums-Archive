---
title: "My Terminals (TTYs) are Gone?!"
date: 2009-07-31
forum: General Help
---

### Post by matey3 on 2009-07-31
Hello All:

I used to could press control-alt and F1 thru F6 and get into my terminal screen.
Now Nothing works!! (Ubuntu 9)
I am inside xdm for good! I can run a terminal from within GUI but...(no good when GUI freezes).
The terminals came in handy when I had problem inside the GUI and wanted to kill a process, now I cannot access the terminal and couple of times I had to hit the reset on my box !! :confused: eek...

Does Anyone know how to get them back?

PS I had setup a key-combo (may be unrelated cuz I used ctrl-alt-windows key)for a diff. language but I delete that and reset all to English, still no go!?

Thank You !

---

### Post by DaithiF on 2009-07-31
Hi,
I suppose you could try switching to one of them using chvt, to narrow down whether its a problem with your keyboard mapping, or a problem with the ttys not actually being there anymore.
```
sudo chvt 1
```
if that works, then i guess it is a problem with your key mappings.  If not, then your ttys have been deallocated.

(I don't have the answer to either problem, but at least it may help you get 1 step closer).

---

### Post by matey3 on 2009-07-31
> **DaithiF said:**
> Hi,
I suppose you could try switching to one of them using chvt, to narrow down whether its a problem with your keyboard mapping, or a problem with the ttys not actually being there anymore.
```
sudo chvt 1
```
if that works, then i guess it is a problem with your key mappings.  If not, then your ttys have been deallocated.

(I don't have the answer to either problem, but at least it may help you get 1 step closer).


Hey That worked! :D

Thank you very much, never heard of that command before..
:)
I guess must be the key mapping problem then?


Thanks again.

---

### Post by matey3 on 2009-07-31
ooops

---

### Post by matey3 on 2009-07-31
Well, I looked into the keyboard shortcuts under Preferences and I manually added TTY1 to it. So that one works, but I keep losing my IP address,(I am using a diff. workstation) so I think I am going back to 8.x.
I have too many problems with 9x, the display is not adjustable to my satisfaction either.(as someone suggested it may already been integrated into HAL which is rather dumb, like integrating a printer into HAL, it aint gonna work)!

Thanks for all the help.

---

