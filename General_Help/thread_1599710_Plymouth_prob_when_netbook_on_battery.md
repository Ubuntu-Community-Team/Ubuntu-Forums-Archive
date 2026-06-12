---
title: "Plymouth prob when netbook on battery"
date: 2010-10-18
forum: General Help
---

### Post by khaos1 on 2010-10-18
Hi guys. I'm using 10.10 ubuntu @ Aser Aspire one D250..

I had some issues with black screen booting (plymouth) and I fixed them with this:
```

sudo su
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
update-initramfs -u
exit
```

It's fixed and ok when I'm on AC Adapter only. When my laptop booting from battery the problem with black boot screen remains. Why?
Is there another option for graphics or plymouth when the AC Adapter is plugged?

Anyone who has a fix or an idea for that?

Thanks in advance

---

### Post by khaos1 on 2010-10-18
Bump! Any idea for that??

---

### Post by khaos1 on 2010-10-19
Sorry for the bump again...

Anyone??? Thanks in advance

---

