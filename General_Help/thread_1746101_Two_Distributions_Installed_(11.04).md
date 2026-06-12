---
title: "Two Distributions Installed (11.04) ?"
date: 2011-05-01
forum: General Help
---

### Post by A4orce84 on 2011-05-01
Hey Guys,

Just got done upgrading my Ubuntu from 10.10 to 11.04 and I oddly enough have 2 Ubuntu 11.04 distributions installed:

1. 2.6.35-22 (in the previous linux versions window in Grub)

2. 2.6.38-8  (Main Grub Menu)


Not sure why my system was installed with 2? I thought it would be the most recent one?

Any ideas?

Thanks.

--Asif

---

### Post by idoitprone on 2011-05-01
it just probably only just one distro, but the upgrade did not uninstall the kernel of the previous version

---

### Post by A4orce84 on 2011-05-01
That would make sense if the previous version was still 10.10, but they are both 11.04 versions ?

---

### Post by idoitprone on 2011-05-01
Yes and no. Both kernels boot to the same system so they can both be consider Natty kernels. But, your previous kernel maybe incompatible with you new and recent version of ubuntu. It is compiled to work with Maverick, so there is no guarantee of a random issue that may pop up.

---

### Post by A4orce84 on 2011-05-01
Is it possible to make the "maverck version" the default and available in the main grub OS loader screen?

Thanks again! =)

---

### Post by idoitprone on 2011-05-01
Did you ever try
```
sudo update-grub
```

it might bring the new kernel to the top

or
 try to delete the old kernel through the synaptic. Becareful, an os without a kernel will bring you headaches 

[http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/](http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/)

then ```
sudo update-grub
```

---

