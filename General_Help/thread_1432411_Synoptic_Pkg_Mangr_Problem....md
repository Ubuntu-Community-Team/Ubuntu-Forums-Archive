---
title: "Synoptic Pkg Mangr Problem..."
date: 2010-03-17
forum: General Help
---

### Post by rayj00 on 2010-03-17
Ubuntu 9.10

When I select the Synoptic Package Manager from 
System->Administration, it flashes on the desktop then disappears?

Any idea why?

Thanks,

Ray

---

### Post by stoneage on 2010-03-17
Try running ```
synaptic
``` or ```
sudo synaptic
``` in a terminal and post, or google, the errors, if any.

---

### Post by jmszr on 2010-03-17
rayj00,

I had a similar problem and this was the fix:

```
sudo rm /var/cache/apt/*.bin
```

Hope that helps.

---

### Post by rayj00 on 2010-03-17
Wow.  That worked!

Thanks for the response!!!

Ray

---

