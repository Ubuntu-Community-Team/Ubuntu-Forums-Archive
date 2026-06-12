---
title: "dv2mov help!"
date: 2006-05-18
forum: General Help
---

### Post by Bleppe on 2006-05-18
I've finally got cinelerra working, now i just need dv2mov working. it gives me an error saying > dv2mov: error while loading shared libraries: libquicktime.so.0: cannot open shared object file: No such file or directory but i've got libquicktime :confused: this is very confusing, have i done something wrong?

---

### Post by metapunk on 2006-05-24
I'd say just use Kino as recommended. I got this working by chrooting to 32-bit since I'm runnign AMD64 arch but then it still gave me a segmentation fault.

What you need to do is open up the AVI file and then export it to QuickTime DV format. I guess that only works in the 32bit architecture as well...
but Cinelerra should work with it after the conversion. I'm right now convering a file so I don't know yet.

---

