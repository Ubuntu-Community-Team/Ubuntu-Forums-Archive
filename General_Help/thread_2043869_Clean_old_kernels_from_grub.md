---
title: "Clean old kernels from grub"
date: 2012-08-17
forum: General Help
---

### Post by webspider on 2012-08-17
My grub screen has about 20 old kernels listed. How do I clean out some of the oldest?

---

### Post by raja.genupula on 2012-08-17
follow this 
[http://askubuntu.com/questions/176322/removing-old-kernel-entries-in-grub](http://askubuntu.com/questions/176322/removing-old-kernel-entries-in-grub)

---

### Post by Frogs Hair on 2012-08-17
The Ubuntu Tweak janitor is my preferred method, but make sure to get the version for your current Ubuntu Release. [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by QIII on 2012-08-17
Also, many of us keep the kernel just prior to the current one.  It can make recovery easier under some circumstances.

---

### Post by Lars Noodén on 2012-08-17
> **QIII said:**
> Also, many of us keep the kernel just prior to the current one.  It can make recovery easier under some circumstances.

That's a very good policy to have just in case.  

I'm not sure how to use the Software Center to uninstall the old kernels.  But apt-get works fine.  You can get a list of what you have using dpkg.

```

dpkg --get-selections linux-image-*

```

---

### Post by webspider on 2012-08-17
Thanks for the tips.

Cheers

---

