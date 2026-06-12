---
title: "Intel video card drivers"
date: 2010-03-22
forum: General Help
---

### Post by Mr_VeRiTy on 2010-03-22
Hi, I'm trying to use google sketchup under WINE, following instructions [here ]("http://ronnietucker.co.uk/blog/2010/03/03/how-to-install-google-sketchup-7-with-wine-in-ubuntu/") but when i started it it told me "sketchup was unable to initialize openGL ! Please make sure you have installed the correct drivers for your graphics card. error choosepixelformat failed." how do i update my video card.

p.s sorry if this is in wrong catagory

---

### Post by _h_ on 2010-03-22
Would be nice if you told us what Intel card you have, may help people who want to help you. :)

Also please post the output of:

```
glxinfo | grep rendering
```

It should say direct rendering: YES.

---

### Post by Mr_VeRiTy on 2010-03-22
the output of 
glxinfo | grep rendering  [FONT=Arial]was "direct rendering: Yes"
 also, how do you check what intel card i have? i'm new to ubuntu[/FONT].

---

### Post by _h_ on 2010-03-22
> **Mr_VeRiTy said:**
> [FONT=Arial]also, how do you check what intel card i have? i'm new to ubuntu[/FONT].

Ok you have DRI capabilities.

Run the command **lspci** in terminal and post the output from the line saying VGA compatible controller.

---

### Post by Mr_VeRiTy on 2010-03-22
the output from lspci was 
"00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)"

---

