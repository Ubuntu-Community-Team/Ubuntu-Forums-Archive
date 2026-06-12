---
title: "differentiating bluetooth mouth states"
date: 2009-08-05
forum: General Help
---

### Post by soumo on 2009-08-05
Hi out there,

does anyone know if there is a way to detect a bluetooth mouse being on WITHOUT/PRIOR TO pairing?

I.e. if I pair my mouse and then turn it off, an
```
hidd --search
``` 
reveals that it is still present.  So I'm guessing that the detected state of the mouse is being stored somewhere and not updated.

On the other hand, 
```
hidd --search
``` 
always turns up no devices found, regardless of on/off/paired!

Basically I need a way to distinguish between ON-paired, ON-unpaired & OFF.

---

