---
title: "Can't remove &quot;linux-backports-modules-nouveau-2.6.32-14-generic&quot;"
date: 2010-09-08
forum: General Help
---

### Post by emarkay on 2010-09-08
"linux-backports-modules-nouveau-2.6.32-14-generic"  is "stuck" on my laptop.
It's a "Not Installed (residual config)" and when I try to I get "E:linux-backports-modules-nouveau-2.6.32-14-generic: subprocess installed post-removal script returned error exit status 1"

Any ideas?

Thanks!

---

### Post by gmargo on 2010-09-08
The post-removal script name is
[B]/var/lib/dpkg/info/linux-backports-modules-nouveau-2.6.32-14-generic.postrm
[/B]
Take a look at that script.  If it's not clear what part is failing then rename it and try again. I assume you're not running the 2.6.32-14 kernel.

---

### Post by emarkay on 2010-09-11
No I am not - rename what, the file itself?

---

### Post by gmargo on 2010-09-11
You could just delete the file or move it elsewhere or rename it in place, just so it is not found by the uninstall procedure.

---

### Post by KegHead on 2010-09-11
Hi!

Could you delete via Tweak?

KegHead

---

### Post by emarkay on 2010-09-17
You mean "Ubuntu Tweak"  I don't have that installed.  


Will try the renaming later this week when I get back to that particular machine.  
Won't that still leave the file in place - and "threaded" to things?

---

