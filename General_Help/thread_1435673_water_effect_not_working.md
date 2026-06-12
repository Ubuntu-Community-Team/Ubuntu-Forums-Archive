---
title: "water effect not working"
date: 2010-03-21
forum: General Help
---

### Post by mastergoomba on 2010-03-21
i installed compiz-fusion and activated the water effect. when i use the keystrokes to initiate it or toggle the rain, nothing happens. i've tried to find information on how to fix it to no avail. help?

---

### Post by megahost on 2010-03-21
it didn't work for me for a while until they came out with an Ubuntu driver for my video card

---

### Post by mastergoomba on 2010-03-21
the drivers for my graphics card are already installed. all of the other effects work, just not the water effect.

---

### Post by mastergoomba on 2010-03-24
anyone? i miss my raining monitor...

---

### Post by howefield on 2010-03-26
> **mastergoomba said:**
> i installed compiz-fusion and activated the water effect. when i use the keystrokes to initiate it or toggle the rain, nothing happens. i've tried to find information on how to fix it to no avail. help?

Not all graphics cards work with the water effect.

What is the output of these terminal commands..

```
lspci | grep VGA
```

```
glxinfo | grep GL_ARB_fragment
```

---

### Post by mastergoomba on 2010-03-27
> **howefield said:**
> Not all graphics cards work with the water effect.

What is the output of these terminal commands..

```
lspci | grep VGA
```

```
glxinfo | grep GL_ARB_fragment
```
this is what i get from the first code:

gearmouse@autumnalis:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)


and this is what i get from the second code:

gearmouse@autumnalis:~$ glxinfo | grep GL_ARB_fragment
gearmouse@autumnalis:

---

### Post by howefield on 2010-03-29
> **mastergoomba said:**
> and this is what i get from the second code:

gearmouse@autumnalis:~$ glxinfo | grep GL_ARB_fragment
gearmouse@autumnalis:

As I understand it, no output means you won't be able to use the water feature.

---

### Post by mastergoomba on 2010-03-29
awwww.....sad face....

---

