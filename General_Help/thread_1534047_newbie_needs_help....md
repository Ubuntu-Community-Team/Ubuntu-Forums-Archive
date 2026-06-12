---
title: "newbie needs help..."
date: 2010-07-18
forum: General Help
---

### Post by jonpete on 2010-07-18
hi there. I am a newbie to linux.. just need help with the water effects for the compiz. Whenever i enable it the screen just darkens up and nothing happens... using it on my netbook MSI Wind U230...

---

### Post by willjammn on 2010-07-19
<Shift>F9 toggles rain on and off.

---

### Post by howefield on 2010-07-19
> **jonpete said:**
> just need help with the water effects for the compiz.

Could be that the graphics card isn't up to it.

What is the output of these terminal commands..

```
lspci | grep VGA
```

```
glxinfo | grep GL_ARB_fragment
```

---

