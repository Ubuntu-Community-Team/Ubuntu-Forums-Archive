---
title: "What is a &quot;resume device&quot;?"
date: 2009-12-08
forum: General Help
---

### Post by mdurham on 2009-12-08
When booting, I see the message "Waiting for resume device". Does anyone know what a "resume device" is, or what it means?
Cheers, Mike

---

### Post by pebo on 2009-12-08
If you suspend to disk (ie hibernate) the contents of memory are written to hard disk, usually your swap partition. When you reboot the initramfs looks for a resume image there and reloads it into memory. If it doesn't find one, it carries on booting as normal.
That, in a nutshell, is it, as I understand it ;)

---

### Post by mdurham on 2009-12-08
Thanks pebo, that answers it perfectly.
Cheers, Mike

---

