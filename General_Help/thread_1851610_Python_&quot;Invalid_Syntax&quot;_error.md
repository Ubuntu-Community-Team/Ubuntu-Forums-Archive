---
title: "Python &quot;Invalid Syntax&quot; error"
date: 2011-09-28
forum: General Help
---

### Post by pazganl2 on 2011-09-28
Hello, 
I've been learning basic functions of Python, and lately I've been working with the PIL library to manipulate images. I dual-boot 11.04 and Win7, and have python installed in both, and use vim to edit in Ubuntu. When I am coding in Ubuntu, I keep on getting an error message claiming that my program has "invalid syntax," pointing to a line that contains:

img = Image.open("alma.jpg")

which DOES work when I'm in Win 7. I am sure that this syntax is correct. Sorry if I am posting in the wrong thread, but I don't understand why it wouldn't work in Ubuntu since Python is not platform-specific?

Thanks!

---

### Post by ofnuts on 2011-09-28
> **pazganl2 said:**
> Hello, 
I've been learning basic functions of Python, and lately I've been working with the PIL library to manipulate images. I dual-boot 11.04 and Win7, and have python installed in both, and use vim to edit in Ubuntu. When I am coding in Ubuntu, I keep on getting an error message claiming that my program has "invalid syntax," pointing to a line that contains:

img = Image.open("alma.jpg")

which DOES work when I'm in Win 7. I am sure that this syntax is correct. Sorry if I am posting in the wrong thread, but I don't understand why it wouldn't work in Ubuntu since Python is not platform-specific?

Thanks!I suspect a non-visible carriage return at the end of the line.

---

### Post by pazganl2 on 2011-09-28
Thank you for the reply,

but after some deeper investigation I found a syntax error earlier in the code, and I had forgotten that the interpreter doesn't always point to the right spot when an error occurs. After fixing that, it ran fine.

---

