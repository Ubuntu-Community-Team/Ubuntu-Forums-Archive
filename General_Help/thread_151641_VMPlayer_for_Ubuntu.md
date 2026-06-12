---
title: "VMPlayer for Ubuntu?"
date: 2006-03-28
forum: General Help
---

### Post by nikolajn on 2006-03-28
Does anyone know if there is an Ubuntu/Debian reporsitory for the VMWare Player? The install process requiring extra compilers, etc. is too challenging for an average user like me. 

I've searched these forums and Google in vain.

Thx in advance. 

/n

---

### Post by Ubuntuud on 2006-03-28
How do you mean, extra compilers? It installed without any dificulties for me...

---

### Post by nikolajn on 2006-03-28
[QUOTE=Ubuntuud]How do you mean, extra compilers? It installed without any dificulties for me...[/QUOTE]
I get the same error message when installing [as in this thread]("http://ubuntuforums.org/showthread.php?t=119434").

What I hoped is that someone had packaged it rally nice so it was easy to install with apt-get.

/n

---

### Post by Yagisan on 2006-03-28
[QUOTE=nikolajn]What I hoped is that someone had packaged it rally nice so it was easy to install with apt-get.[/QUOTE]Not likely to happen unless it is freely redistributable in it's license. If so, then you need to convince a motu it is a good idea, or hope a forum user will package it.

---

### Post by pauljwells on 2006-03-28
Edit...

Make sure that you have the correct headers for your kernel. Type uname -r to see what your running kernel is and then look for an exact match in s/kynaptic. You also need 'build-essential' for the compiler. I've always found the VMWare installers to be about as easy to use as is possible for something that is really quite complex.

As a footnote, you will find that if you upgrade your kernel, VMPlayer will probably break and you'll have to reinstall each time. Keep trying, it is an insanely useful app and well worth the effort!

---

### Post by nikolajn on 2006-03-28
Thanks. This did the trick in combination with the step-by-step at [http://torrez.us/myubuntu/](http://torrez.us/myubuntu/)

Thanks for the help! :)

/n

---

