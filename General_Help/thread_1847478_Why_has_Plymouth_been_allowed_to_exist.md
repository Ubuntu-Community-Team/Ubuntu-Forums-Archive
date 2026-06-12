---
title: "Why has Plymouth been allowed to exist?"
date: 2011-09-20
forum: General Help
---

### Post by Shibblet on 2011-09-20
I have distro-hopped quite a bit, and have settled (for now) with Fedora.  One continuous bug I have found in many different distros is Plymouth.

This "graphical" boot screen causes improper display settings with Ubuntu, and when you drop your proprietary Nvidia drivers into Fedora, it causes your computer to not boot.

This is a consistent issue across distributions.

So my question is, why do distro's still use it?

---

### Post by IWantFroyo on 2011-09-20
Because it's pretty. Besides, it works for most people. If you don't like it, you can turn it off (as far as I know- I've never needed a reason to).

---

### Post by WorMzy on 2011-09-20
I believe that it needs KMS to work correctly, and propriety drivers don't support KMS.

Use KMS-capable drivers for your graphics card, and plymouth will (probably) work fine.

Otherwise, like IWantFroyo suggested, just don't use plymouth. Remove it, or just remove the "splash" argument from grub's kernel line arguments. Whatever floats your boat.

---

