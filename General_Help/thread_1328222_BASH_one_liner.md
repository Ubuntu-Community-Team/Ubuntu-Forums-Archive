---
title: "BASH one liner ?"
date: 2009-11-16
forum: General Help
---

### Post by Barriehie on 2009-11-16
How can I use ls -r | tail -n x as the first argument to mv *arg0* dirpath?

TIA,
Barrie

---

### Post by lloyd_b on 2009-11-16
> **Barriehie said:**
> How can I use ls -r | tail -n x as the first argument to mv *arg0* dirpath?

TIA,
Barrie

Use a read loop```
ls -r | tail -n 10 | while read FILE; do mv $FILE /home/user/somedir; done
```Not sure if there's a simpler way to do this, but this one should work...

Lloyd B.

Edit: Okay, so there *is* a simpler way, using the 'xargs' command:```
ls -r | tail -n 10 | xargs mv -t /home/user/somedir
```produces the desired result as well.

---

### Post by Barriehie on 2009-11-16
Thank you Lloyd!  The second option with xargs was exactly what I was looking for.  I also found this:

```

 while read file; do ls "$file"; done <<< "$(ls -1lt | tail -n 11)"

```

Barrie

---

