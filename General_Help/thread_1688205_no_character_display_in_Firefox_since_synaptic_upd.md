---
title: "no character display in Firefox since synaptic update"
date: 2011-02-15
forum: General Help
---

### Post by louisJ on 2011-02-15
Hi

Firefox (3.6.13 for Ubuntu) does not display text (alphanumerics) on webpages anymore, neither ion pages neither in text fields where I type text...there is blank spaces where there should be text, see the screen capture attached...
This happened after I did the last updates from synaptic (Ubuntu 10.10 64bit up to date).

Any idea on what to do?

Thanks

---

### Post by louisJ on 2011-02-16
up!

---

### Post by louisJ on 2011-02-20
same problem with namoroka  (firefox 3.6.15pre)....
Please help!!!

---

### Post by louisJ on 2011-02-20
ok I found the problem (even if there is no one on this thread::!)

I removed everything in /usr/share/fonts/truetype/
then
fc-cache -f -v 

then firefox is ok

---

