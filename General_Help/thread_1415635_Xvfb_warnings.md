---
title: "Xvfb warnings"
date: 2010-02-25
forum: General Help
---

### Post by asmith20002 on 2010-02-25
Hi.

I have setup Xvfb on my ubuntu 8.04. It is actually running my webserver. I needed a fake X server for some purposes. (I have run 'Xvfb :1 &')
Anyway all is working fine. But for any command that uses Xvfb, I'm getting this warnings over and over:

> 
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/:unscaled, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/:unscaled, removing from list!
Could not init font path element /usr/share/fonts/X11/Type1, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi, removing from list!


How can I fix these warnings?
Thanks for your time

---

### Post by asmith20002 on 2010-02-26
I did: 

```
sudo aptitude install xfonts-100dpi xfonts-75dpi xfonts-scalable xfonts-cyrillic
```and it all warnings got fixed. Except this:

>                               FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.Anyone know how to fix this one?

---

