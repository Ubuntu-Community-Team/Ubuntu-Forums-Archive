---
title: "/etc/X11/xorg.conf EMPTY"
date: 2009-10-29
forum: General Help
---

### Post by m00se3724 on 2009-10-29
I just installed 9.10 and I need to add screen resolutions since I'm running parallels on my mac, but /etc/X11/xorg.conf is empty. Am I missing something?

---

### Post by m00se3724 on 2009-10-29
anyone else having this issue?

---

### Post by philinux on 2009-10-29
The default is empty. Or not to have an xorg.conf at all.

Have you got a backup of your previous xorg.conf. You only need the relevant bits.

---

### Post by m00se3724 on 2009-10-29
Is the default empty starting with 9.10? I have my old one somewhere, thanks.

---

### Post by philinux on 2009-10-29
> **sanduskm said:**
> Is the default empty starting with 9.10? I have my old one somewhere, thanks.

It started with 9.04 being minimalist and now as it is.

---

### Post by cpedrezuela on 2009-10-30
Hi All,
 
Just want to confirm again, the xorg.conf is empty by default in 9.10?
 
I was going to change some setting for my mouse, its been shaking and sticking to the edge like in 9.04.
 
How can I go about this issue? Thanks.
 
Christopher

---

### Post by ianc on 2009-10-30
Even though it's empty by default xorg.conf should still be read if it does exist. Try creating the file with the settings you need & see if it works.

---

