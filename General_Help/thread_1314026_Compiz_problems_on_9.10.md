---
title: "Compiz problems on 9.10"
date: 2009-11-04
forum: General Help
---

### Post by viniciuscarvalho on 2009-11-04
Hello there! When using compiz with extra effects on gnome, most flash based apps lost the onclick feature (youtube being the only one that works) also eclipse is having serious issues.

When I turn off compiz, those issues go away and the click start working again.


Is there anything I could do? I would not want to turn off compiz since I'm already used with the great effects it provides.

Also, does it seems to be a BUG? I could enter a new bug on ppa

Regards

---

### Post by 0cton on 2009-11-04
This is normally an issue with proprietary drivers and not compiz itself.
what videocard do you have?

---

### Post by viniciuscarvalho on 2009-11-04
Radeon 4650HD. 

If it is a driver issue, why it does not happen with compiz turned off?

---

### Post by bedhead75 on 2009-11-04
Are you using a 64-bit system?  Completely removing 32-bit flash, the 32-bit wrapper program, and installing 64-bit flash fixed this for me.

---

### Post by Uncle Spellbinder on 2009-11-04
> **bedhead75 said:**
> Are you using a 64-bit system?  Completely removing 32-bit flash, the 32-bit wrapper program, and installing 64-bit flash fixed this for me.

Also a known issue exists with Flash/Compiz/64bit compatibility. I recently started over and installed Karmic 32-bit on my system. Zero issues with Flash/Compiz/64bit compatibility.

---

### Post by viniciuscarvalho on 2009-11-09
This problem happens not only with flash, but eclipse as well...

I tried to remove the proprietary drivers, change its versions, I guess the bug is this entire distro. They should rename Karmic Koala to Karmic Bug. I believe that "Ubuntu stop making linux looks bad" [http://www.linux-mag.com/cache/7600/1.html](http://www.linux-mag.com/cache/7600/1.html) is really true when you check only this latest distro. I'm switching back to 9.04. Better forget 9.10

---

