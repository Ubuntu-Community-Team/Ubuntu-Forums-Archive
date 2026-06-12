---
title: "Ubuntu icon"
date: 2009-11-21
forum: General Help
---

### Post by jacobs444 on 2009-11-21
Does anyone know how to change the ubuntu icon that shows at boot before the xsplash brown theme? i like my systems to look custom, and the icon is driving me crazy. Any help verily appreciated. using 9.10 karmic

---

### Post by jacobs444 on 2009-11-21
nobody?

---

### Post by emigrant on 2009-11-21
you mean you want to change the gdm?
it seems uncustomizable in karmic.

---

### Post by jacobs444 on 2009-11-21
No not the gdm, i have hacked that into submission. I want to change the white ubuntu icon that shows for five or so seconds before gdm shows.

---

### Post by jacobs444 on 2009-11-22
anybody got a fix for this?

---

### Post by fluffman86 on 2009-11-22
I believe that is controlled by /boot/vmlinuz*  Maybe you can find something on hacking that.

---

### Post by jacobs444 on 2009-11-23
The fix, and what was confusing me is that karmic still uses usplash to do the ubuntu icon, i got the ubuntu-usplash-theme sources then recompiled them with my own icons. I also simply colorized the throbber in the /usr/share/images/xsplash directory and changed the icons in that folder to my taste. Thank god, no more ugly brown. 

if anyone needs a more in depth for the new usplash and xsplash, then message me.

---

