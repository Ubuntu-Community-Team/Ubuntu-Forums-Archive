---
title: "Reduce Unity Icon Size to less than 32"
date: 2011-11-12
forum: General Help
---

### Post by BillyBoa on 2011-11-12
Does anyone know a way to reduce Unity icon size to less than 32b?

---

### Post by Paddy Landau on 2011-11-14
I would also like to know this.

According to the Configuration Editor (gconf), setting:
apps > compiz-1 > plugins > unityshell > screen0 > options > icon_size
may only take values between 32 and 64.

You can try setting it to lower than 32, but I'm nervous to try in case I mess it up!

---

### Post by BillyBoa on 2011-11-14
Thanks a lot! I'll give it a try.

---

### Post by Paddy Landau on 2011-11-14
> **BillyBoa said:**
> Thanks a lot! I'll give it a try.
Let me know what happens...

---

### Post by BillyBoa on 2011-11-15
Nope.

I changed the values to 24, 22 and 16 but it's not that easy. 

The icons changed to the Ubuntu default (monster) size.

The gconfig is like this:

> <?xml version="1.0"?>
<gconf>
	<entry name="icon_size" mtime="1320935307" type="int" value="16"/>
	<entry name="launcher_opacity" mtime="1320935307" type="float" value="0"/>
	<entry name="panel_opacity" mtime="1320935316" type="float" value="0.47859999537467957"/>
</gconf>

---

### Post by Paddy Landau on 2011-11-15
Hmm, it seems that the size limitations are built into Unity. Pity.

---

