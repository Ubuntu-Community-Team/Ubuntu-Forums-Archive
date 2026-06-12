---
title: "GRUB shows two Ubuntu installations"
date: 2010-08-21
forum: General Help
---

### Post by teolandon on 2010-08-21
I installed normally Ubuntu in my lenovo laptop, but GRUB shows two installations instead of one. Whatever happens to one of them, happens to the other, except some command-line work. How can I fix this problem?

---

### Post by dv3500ea on 2010-08-21
You can 'fix' this by [removing your old kernels]("http://jaypeeonline.net/tips-tricks/howto-remove-old-ubuntu-kernels/").

---

### Post by mendhak on 2010-08-21
Hi, welcome to UF.  The two installations you're seeing, do they have different version numbers in front of them? They are probably different kernel versions.  Whenever you do an update and there's a new kernel available, that'll get added to your existing Ubuntu installation.  The old kernel won't go away, just in case you have problems with the new one, you can always go back to the old ones from Grub.  

I'm not sure what the problem is, though.  I usually keep 2 or 3 kernels just in case.  If you are happy with your existing kernels, you can always remove them.  Go to Synaptics package manager, look for linux-image.  You should see several installed modules, you can remove the older versions.

After that, run a sudo update-grub.

---

### Post by philinux on 2010-08-21
> **teolandon said:**
> I installed normally Ubuntu in my lenovo laptop, but GRUB shows two installations instead of one. Whatever happens to one of them, happens to the other, except some command-line work. How can I fix this problem?

I tend to leave at lest one old kernel just in case the new one has a bug. When I get to three kernels I remove the oldest. Also don't forget that for each kernel there is the recovery mode that goes with it.

---

### Post by teolandon on 2010-08-21
OK, thanks. I think I'll keep it.
And, philinux, I didn't mean the recovery mode.

---

