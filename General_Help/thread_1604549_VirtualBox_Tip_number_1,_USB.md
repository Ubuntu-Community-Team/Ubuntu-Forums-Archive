---
title: "VirtualBox Tip number 1, USB"
date: 2010-10-24
forum: General Help
---

### Post by coldraven on 2010-10-24
After installing VirtualBox, add yourself to the Vboxusers group in System -> Administration -> Users and Groups.
Then re-boot your computer!
Otherwise you will spend hours (like me) wondering why your USB devices are not available in your guest VM.
I just did a complete install on a new, larger hard drive and had forgotten this simple fact. Doh!

---

### Post by tbplayer on 2010-10-24
What if there is no Vboxusers group?

---

### Post by tbplayer on 2010-10-25
> **tbplayer said:**
> What if there is no Vboxusers group?

Nevermind, I discovered the problem. I had installed the OSE version of Virtualbox, which does not support USB. I downloaded and installed the PUEL version and now I have a Vboxusers group.

---

