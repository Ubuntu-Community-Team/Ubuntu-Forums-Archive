---
title: "&quot;Could not find kernel image: linux&quot;"
date: 2010-03-17
forum: General Help
---

### Post by JayUK20 on 2010-03-17
I have put UMR on a flash disk and used Ubuntu ImageWriter and it all went fine yet when I try and boot from the pen drive I get stopped at the black syslinx screen and get 

> boot:

I type linux and get

> Could not find kernel image: linux

I do not really want to use unetbootin

---

### Post by JayUK20 on 2010-03-17
I've just tried unetbootin but i still get the same error message.

---

### Post by texpat on 2010-03-17
If you type
```
vmlinuz
```
instead of linux?

It may be looking for the actual file..

---

### Post by JayUK20 on 2010-03-17
I've just tried that but I seem to still be getting the same error message.

---

### Post by JayUK20 on 2010-03-17
Ok here is my vmlinuz.cfg file, not sure if it is intact?

> include menu.cfg
default /syslinux/vesamenu.c32
prompt 0
timeout 00

---

### Post by JayUK20 on 2010-03-17
Has anyone else had this problem, if so how did you fix it?

---

### Post by texpat on 2010-03-17
Sorry JayUK20, it seems I'm out of my depth here.

vmlinuz links to boot/vmlinuz-2.6.. and so on (version number)

My original thought was simply that your UMR or unetbootin was looking for a linux boot image to load, which - according to my logic - would have been just that (vmlinuz linking to the actual bootimage in boot/vmlinuz and so on).

---

