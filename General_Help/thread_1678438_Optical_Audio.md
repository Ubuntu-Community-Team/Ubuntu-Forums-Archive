---
title: "Optical Audio?"
date: 2011-01-30
forum: General Help
---

### Post by megzaz on 2011-01-30
Hi,

Is it possible to use the optical output on my computer using ubuntu and how you would go about doing so without the original drivers? The sound preferences menu doesn't seem to find it...

Thanks,
Megan

---

### Post by [Snc] on 2011-01-30
> **megzaz said:**
> Hi,

Is it possible to use the optical output on my computer using ubuntu and how you would go about doing so without the original drivers? The sound preferences menu doesn't seem to find it...

Thanks,
Megan

What sound card have you got?

---

### Post by airtacable on 2011-01-30
Hey Megan,

I had loads of trouble with this, so you're not alone. Assuming your drivers and everything else is ok, throw alsamixer into the terminal and use the arrow keys to go across to the optical out. Then use "m" to switch it on off.

Note: if you have more than one sound card, you'll need to select the right one first.

ATB,

airtacable

---

