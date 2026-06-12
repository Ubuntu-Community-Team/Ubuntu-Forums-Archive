---
title: "Problems configuring Plymouth"
date: 2010-07-04
forum: General Help
---

### Post by emperortux on 2010-07-04
I tried to switch my Plymouth install from the default Kubuntu splash to Solar.  Now, when I boot up, it shows a low-resolution default Ubuntu splash, with a monospaced-text logo.  On shutdown, Solar displays, but at a very low resolution.  How do I fix this?

---

### Post by emperortux on 2010-07-06
*bump :popcorn:

---

### Post by emperortux on 2010-07-09
Bump :-|

---

### Post by emperortux on 2010-07-10
Never mind, fixed it myself :D
For anyone wondering, the problem was that in my /etc/default/grub file, my vga= mode was set too high for my screen.  All I had to do was set it to 792, which is closer to my screen resolution

---

