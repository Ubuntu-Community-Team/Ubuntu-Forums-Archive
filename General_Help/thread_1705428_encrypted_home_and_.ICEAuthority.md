---
title: "encrypted home and .ICEAuthority"
date: 2011-03-12
forum: General Help
---

### Post by nogoodnamesleft on 2011-03-12
Hi

On login to graphical shell I get an error, cannot access .ICEAuthority.

Clicking OK makes it go away and the desktop starts as normal.

I have noticed the file is present and I am the owner but chmod mode is 600.

I've tried to chmod 644 and it can't while i'm logged in (even at console) and with sudo.

I've tried to boot from grub , select repair , and load a root shell

However I have an encrypted home directory ... !

Can anyone help me to fix this?

Thanks!

---

### Post by nogoodnamesleft on 2011-03-17
fixed, marked as solved.

i had the wrong encryption package installed. duh!

---

