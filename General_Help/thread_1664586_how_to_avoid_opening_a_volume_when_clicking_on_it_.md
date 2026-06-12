---
title: "how to avoid opening a volume when clicking on it under places menu?"
date: 2011-01-11
forum: General Help
---

### Post by tanoloco on 2011-01-11
Hello, 

when I click on a volume under places menu I would like only to mount it without opening it on a new nautilus window. I searched on gconf-editor app > nautilus > preferences but I haven't found any option which seems to prevent this behaviour. Any suggestion?

I noticed that cairo-dock does it, so it might be possible.

Thank you for any help

---

### Post by stinkeye on 2011-01-11
--

---

### Post by endotherm on 2011-01-11
> **tanoloco said:**
> Hello, 

when I click on a volume under places menu I would like only to mount it without opening it on a new nautilus window. I searched on gconf-editor app > nautilus > preferences but I haven't found any option which seems to prevent this behaviour. Any suggestion?

I noticed that cairo-dock does it, so it might be possible.

Thank you for any help

probably not easily. I would probably use nautilus-actions to create a rclick mount option and just use it.

the mime application associations for folders specify nautilus as the default appliction to handle folder open commands. that is true if the folder is on the desktop, in /, or in your places menu. as such if you change the behavior of the places menu in this regard (perhaps by handling the event with another app like mount) you would probably lose the ability to open folders in nautilus at all, unless you had already invoked it from alt+f2 or wherever. 
The Cairo dock you mention must not use the mimeapps.lst for reading and storing application associations to it is free to replace it's own functionality without interfering with other uses.

---

### Post by tanoloco on 2011-01-12
mmm .. thank you for the reply.
You are right: it doesn't seem easy. So I posted this idea to Ubuntu Brainstorm

[http://brainstorm.ubuntu.com/idea/26944/](http://brainstorm.ubuntu.com/idea/26944/)

maybe it would be discussed and implemented.

---

