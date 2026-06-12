---
title: "grub - boot choices increasing!"
date: 2010-12-28
forum: General Help
---

### Post by madeinwales on 2010-12-28
ubuntu 10.10 dual booting with xp. everything works fine but my bootup choices of ubuntu 10.10 or ubuntu recovery mode have now trebled i.e are repeated three times on boot list, with windows still as one choice at the bottom of the list. 
is this normal? is something wrong and do i need to do anything?
as i say all still works as it should. any clarification greatly appreciated.

---

### Post by tredegar on 2010-12-28
They are just older versions of the kernel, which is sometimes updated.

You can delete them with your package manager, or leave them. They are harmless.

Most people like to keep at least one "fallback" kernel.

---

### Post by madeinwales on 2010-12-28
> **tredegar said:**
> They are just older versions of the kernel, which is sometimes updated.

You can delete them with your package manager, or leave them. They are harmless.

Most people like to keep at least one "fallback" kernel.
thanks for the quick response, so is the newest version on the top of the list i.e is the default boot the newest?

---

### Post by Bucky Ball on 2010-12-28
Yes. Just check by reading the kernel number at the end of the line. You have the current kernel and its recovery kernel underneath. Then the last kernel and its recovery, and so on ...

You only really need the first four (the current kernel and its recovery plus the last working kernel and its recovery).

---

