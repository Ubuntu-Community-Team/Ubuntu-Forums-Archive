---
title: "GNU GRUB Start Up Message"
date: 2011-04-24
forum: General Help
---

### Post by Yamipirogoeth on 2011-04-24
The attachment shows my startup screen when loading Ubuntu 10.10. As the screenshot shows, I am using this with a VMware environment.

What I'm trying to find out is if this message is just a result of the VMWare or is there something actually wrong with my Ubuntu installation

---

### Post by decrepit on 2011-04-24
Is it giving you a problem? 
It looks normal to me, except you have a lot of extra kernals.
It's good to have at least 1 extra one, maybe 2, but you shouldn't need anymore.
There's plenty of threads here about cleaning up excess kernels.

---

### Post by kiyop on 2011-04-24
> **Yamipirogoeth said:**
> What I'm trying to find out is if this message is just a result of the VMWare or is there something actually wrong with my Ubuntu installation
I think it is not the result of VMware, but the result of grub2.
If you want these kind of screen not displayed, you can edit /etc/default/grub.

Please refer to:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Yamipirogoeth on 2011-04-26
Ah, thanks both of you, I had no idea that was just extra kernels (still new to linux). But, thanks to Ubuntu Tweak, that issue has been solved.

---

