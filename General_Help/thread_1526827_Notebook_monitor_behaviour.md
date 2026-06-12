---
title: "Notebook monitor behaviour"
date: 2010-07-08
forum: General Help
---

### Post by Jan Dahl on 2010-07-08
Hello,

I've recently purchased a new notebook, to which I sometimes attach an external screen. I don't know if the problems are specific to external VGA screens and non-existant when using DVI, or maybe local to Intel video cards.

The below described situation is on Ubuntu 10.4. I have not tested on other variants nor distributions.

I'll just describe my ideal-use situation and then contrast with the actual-use situation.

Ideal use: Attaching an external monitor
> 
An external monitor is detected.
The external monitor is automatically used to expand the desktop to full monitor resolution.
*Optionally*, the internal monitor can turn of in this state


Actual use: Attaching an external monitor
> 
An external monitor is detected.
Go to System -> Preferences -> Monitors
Turn on the external monitor
Turn off mirroring
Adjust resolution to actually fit the screen
*Optionally*, turn off internal monitor


Even worse, when an external monitor is detached, and I have the internal monitor off, the "monitor setup" is not automatically corrected to new reality. Instead, I have to re-connect the external monitor, re-enable the internal and disable the external before unplugging it. 

For me, this is a major usability issue, and if someone has a solution for this I would be most grateful.

---

### Post by gordintoronto on 2010-07-08
This behavior depends on what notebook you have. On many laptops, a key combination such as Fn-F4 controls monitor usage, sometimes by rotating among internal, external, both. Have you looked at the manual for your computer?

---

### Post by Jan Dahl on 2010-07-13
> **gordintoronto said:**
> This behavior depends on what notebook you have. On many laptops, a key combination such as Fn-F4 controls monitor usage, sometimes by rotating among internal, external, both. Have you looked at the manual for your computer?

Thank you for your answer. My apologies for being so late to answer your question.

There is one such combination, but Ubuntu does not work with any of the "additional" functions of my laptop keys. 

Even so, if I have an external monitor connected and I break the connection, it should detect this event and logically disable the monitor that is no longer connected; as a logical followup to this, if this was the last active monitor, enable "the first" (or all) disabled but detectable monitors.

---

### Post by Jan Dahl on 2010-07-14
<bump>

---

### Post by Jan Dahl on 2010-07-19
This really is a big deal for me :-/

---

