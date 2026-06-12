---
title: "Update Manager"
date: 2010-09-25
forum: General Help
---

### Post by KajuNM on 2010-09-25
**[SOLVED]** When I try to update the latest from Update Manager I get this message:

Please insert the disk labeled:
Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)
in drive /cdrom/

I'm running 9.10. I don't know why I'm getting this message, does anyone here know why this is happening?

---

### Post by 3rdalbum on 2010-09-25
You have an Ubuntu 10.04 disc listed in your software sources. You can remove it from the Software Sources program.

---

### Post by jmszr on 2010-09-25
KajuNM,

Try going to System > Administration > Software Sources > Third-Party Software > and uncheckmark the line at the top that says something like: cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted . I'm not sure of the exact wording as I'm running 8.04.

Try un-marking that line and then reloading the Software Sources.

Hope that helps.

---

### Post by KajuNM on 2010-09-25
3rdalblum & jmszr

Thanks for yor suggestions they worked.

---

