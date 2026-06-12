---
title: "Move openbox window buttons to the left?"
date: 2010-07-27
forum: General Help
---

### Post by kut77less on 2010-07-27
Is there a way to move openbox window buttons to the left (like in Lucid)?

---

### Post by Deiz on 2010-07-27
Yes. Edit ~/.config/openbox/rc.xml and change <titleLayout>'s value to something like IMCNDL.

You can also do this with obconf. IMC = Iconify, Maximize, Close.

---

### Post by kut77less on 2010-07-27
It worked. Thanks! But I used CIML, so that the order of the windows would be Close, minimize,max

---

### Post by malspa on 2010-07-29
Thanks, Deiz -- didn't realize it would be simple.  Also, using obconf works for this in LXDE as well.

---

### Post by Svento on 2010-12-07
Is it possible setting it to auto-undecorate maximized windows? My interset in OpenBox exclusively has to do with a wish to hide the titelbar. I can make it work on every window, undecorating them one-by-one, but only until I close them.

Also, I'd like to have the titel centered in the unmaximized windows. Only because I'm used to have it in the middle...

---

