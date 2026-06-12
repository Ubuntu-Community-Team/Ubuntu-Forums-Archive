---
title: "Generic Kernal in GRUB Menu??"
date: 2009-09-06
forum: General Help
---

### Post by distortedecho on 2009-09-06
Hi,

Why do I have so many boot options?
I have 2 generics kernals which includes the recovery mode for 3 different kernal versions??

Can someone please explain?

---

### Post by pastalavista on 2009-09-06
When you update to new kernels, the old one is kept in case the new one causes problems. After you've determined the update works OK, you can remove the old kernels with Synaptic. Just search for "linux-image" and remove the older ones. Grub will be updated automatically.

---

### Post by drs305 on 2009-09-06
This will explain it and tell you how you can minimize them:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

In addition, it discusses StartUp-Manager, a GUI grub editor.

---

### Post by distortedecho on 2009-09-08
Thank you guys!

---

