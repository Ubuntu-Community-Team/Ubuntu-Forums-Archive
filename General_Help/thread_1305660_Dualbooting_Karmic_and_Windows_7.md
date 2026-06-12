---
title: "Dualbooting Karmic and Windows 7"
date: 2009-10-30
forum: General Help
---

### Post by mhh91 on 2009-10-30
Has anyone tried it yet?

I have a win7 on sda1,will grub identify that installation?


I tried installing Arch Linux before and it didn't even recognize the presence of win7 on my Hard Drive :(


thanks in advance ;)

---

### Post by mhh91 on 2009-10-30
Bump

---

### Post by dentharg on 2009-10-30
It will. I've installed Win7 first, then Karmic (then Alpha5) and everything went smoothly.

Otherwise if you run update-grub it should detect windows partition.

---

### Post by mhh91 on 2009-10-30
> **dentharg said:**
> It will. I've installed Win7 first, then Karmic (then Alpha5) and everything went smoothly.

Otherwise if you run update-grub it should detect windows partition.

Thanks a lot,I'll try that now :)

---

### Post by Wiebelhaus on 2009-10-30
> **mhh91 said:**
> Has anyone tried it yet?

I have a win7 on sda1,will grub identify that installation?


I tried installing Arch Linux before and it didn't even recognize the presence of win7 on my Hard Drive :(


thanks in advance ;)

Yes and yes. It works perfectly.

---

### Post by Sub101 on 2009-10-30
I found that on the initial install of karmic Windows 7 is not added to grub, but after updating it is added.

---

