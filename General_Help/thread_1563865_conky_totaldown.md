---
title: "conky totaldown"
date: 2010-08-29
forum: General Help
---

### Post by llawwehttam on 2010-08-29
In conky the variable totaldown displays the total amount downloaded since the last reboot.

Is there a command that can show the same thing that I could put into my bash login script so I can check how much has been downloaded when I ssh into a machine?

---

### Post by squaregoldfish on 2010-08-30
I don't know of a simple command to do this, but the information can be extracted from /proc/self/net/dev, or the output of ifconfig.

Note that this figure will reset occasionally. From the conky manual:

> ...overflows at 4 GB on Linux with         32-bit arch and there doesn't seem to be a way to know how         many times it has already done that before conky has         started.          Steve.

---

### Post by llawwehttam on 2010-08-30
Thanks. i never noticed you could derive it from ifconfig.

Is there any way to manually reset the figure?

---

### Post by squaregoldfish on 2010-08-30
No idea, but my hunch is no.

Steve.

---

### Post by llawwehttam on 2010-08-30
As it resets on a reboot my guess is that it depends on a service so restarting that service may do the trick. 

I'm off to investigate. I'll post back if I find anything.

---

### Post by squaregoldfish on 2010-08-30
Could be it resets when the interface is brought up. In which case you could reset it by ifdown/ifup, but that may not be ideal for an SSH server...

Steve.

---

