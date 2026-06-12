---
title: "edit bootgrub so that it won't start by itself"
date: 2006-06-18
forum: General Help
---

### Post by tipi on 2006-06-18
hi there,
is there anyone who can tell me how to edit the /boot/grub/menu.lst
so that ubuntu will not start by itself  a few seconds after turning on the pc.
i want it simply to stop at the boot options,

greetz

heres my /boot/grub/menu.lst

---

### Post by Jucato on 2006-06-18
IIRC, just set the timeout line to 0. basically change this
> timeout		10
to this
> timeout		0

---

### Post by tipi on 2006-06-19
when putting it to "0" it didn't stop at all, so I just put no number there
that did it

thanks for pointing me

greetz

---

