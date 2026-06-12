---
title: "WEP key"
date: 2006-02-12
forum: General Help
---

### Post by Disastorm on 2006-02-12
I finally got my broadcom wireless working on my laptop, i can find my signal when i do iwlist scan.  Hiowever, when i goto the properties and put in my WEP key (ascii mode, just type in the 10 digits) it doesnt seem to work.  on dmesg it says like 
adding encryption key 1 failed 
and also
wlan0: no IPV6 routers present
*Oh i got it working, it turns out the WEP key I had was already in hexadecimal format, i thought it was ascii.

---

