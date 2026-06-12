---
title: "Truecrypt refuses to unmount external hard-drive at first attempt"
date: 2012-04-17
forum: General Help
---

### Post by na5h on 2012-04-17
Hi, I've recently started to get the following error message in Truecrypt when I try to unmount my external hard-drive: 
"Directory not empty: /media/truecrypt1".

It only happens the first time I click on the "dismount" button, though. If I click the "dismount" (or "dismount all") button again, it unmounts the hard-drive just like it should.

Not really a big problem since it just makes me click the "dismount" button twice instead of once...but I haven't had this problem on my other Ubuntu computer (and it used to work just fine on this one as well). 
Any ideas? I'm sure it's an easy fix...

---

### Post by na5h on 2012-04-17
I just solved the problem myself! Truecrypt mounts its volumes as "truecrypt1", "truecrypt2", etc. and for some weird reason there was a folder left inside /media named truecrypt1 containing an empty folder even after the external hard-drive was unmounted. 

I deleted the folder using "gksudo nautilus" and now it works like a charm!

---

