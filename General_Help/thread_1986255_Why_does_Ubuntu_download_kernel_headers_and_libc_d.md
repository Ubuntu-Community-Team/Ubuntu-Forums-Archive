---
title: "Why does Ubuntu download kernel headers and libc dev libraries"
date: 2012-05-24
forum: General Help
---

### Post by rthorpe on 2012-05-24
I recently upgraded to Xubuntu 12.04. Since then there have been updates almost every day. The update manager has upgraded the kernel and kernel headers several times. I has upgraded a lot of stuff that I don't use. I have no idea why I have the kernel headers and libc development stuff installed. But, I must have a dependency on it somewhere.

How can I slim down the amount of stuff I have that needs regular updating?

---

### Post by vandorjw on 2012-05-24
In software updates, you can opt for security updates only.
You can also set it to only download stable updates. (disable testing)

^^^This is what I remember from when I used ubuntu 8.10

I dont know how to do this in 12.04 (yet)
I also dont know if this is recommended.
Finally, I believe testing repo's are disabled by default.

---

### Post by Paqman on 2012-05-24
> **rthorpe said:**
> 
How can I slim down the amount of stuff I have that needs regular updating?

If you're not using something, you can just uninstall it. Nobody needs *everything* that's in the default install.

Apart from that, open up Software Sources and take a look at your options. Make sure stuff like proposed and backports are disabled. You can set it to simply install security updates automatically, then you could if you want just ignore any other updates it offers.

---

### Post by rai4shu2 on 2012-05-24
> **rthorpe said:**
> I recently upgraded to Xubuntu 12.04. Since then there have been updates almost every day. The update manager has upgraded the kernel and kernel headers several times.

There were two upgrades for the month of May. You just happened to pick the perfect time to get both of them.

---

### Post by rthorpe on 2012-05-25
Thanks everyone, that helped a lot.

---

### Post by matt_symes on 2012-05-25
Hi

DKMS, if you use proprietary drivers, requires the headers.

Kind regards

---

