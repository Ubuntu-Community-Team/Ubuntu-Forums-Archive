---
title: "/tmp as tmpfs disables unity"
date: 2011-07-30
forum: General Help
---

### Post by pbeesley on 2011-07-30
so i've tried doing the whole /tmp as tmpfs thingy and it works!

however it disables unity.

Does anyone know why? :confused:

---

### Post by pbeesley on 2011-08-01
bumpy bump

---

### Post by blind2314 on 2011-08-01
> **pbeesley said:**
> so i've tried doing the whole /tmp as tmpfs thingy and it works!
 
however it disables unity.
 
Does anyone know why? :confused:
 
Possibly because Unity writes cache files to /tmp by default, and when you're using it as a separate mountpoint, it can't anymore. Any reason you're using /tmp, and not making your own mountpoint to use?

---

### Post by pbeesley on 2011-08-01
> **blind2314 said:**
>  Any reason you're using /tmp, and not making your own mountpoint to use?

From following guides :D

I just wanted temporary files to be written to RAM :S quick google didn't turn up anyone else having a problem like this :frown:

---

### Post by pbeesley on 2011-08-02
I'm planning on reinstalling 11.04 at the weekend so I'll try again and see if I have any luck :frown: if not I guess I'll have to live without Unity

---

