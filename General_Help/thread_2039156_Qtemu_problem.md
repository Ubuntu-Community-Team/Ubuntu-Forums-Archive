---
title: "Qtemu problem"
date: 2012-08-08
forum: General Help
---

### Post by Statia on 2012-08-08
Any virtual machine I try to start, whether qcow, anyboot image or from iso, results in this error:



```
An error has occurred. This may have been caused by
an incorrect setting. The error is:
Could not find KVM version for this KVM binary, got version acceleration has been left in its default state. Got version -1
```Standard install of qemu from the Ubuntu repositories. Any ideas how to fix this?

---

### Post by Statia on 2012-08-21
Solved. I just use VirtualBox now.
Getting quite sick and tired of well-meaning open source software that will not even work out of the box.

---

### Post by Timmmm3d on 2013-02-09
That isn't "solved"!

The real solution to this idiotic error message, is to go to File->Configure->QEMU Start Command, and change it from "qemu" to "kvm", or maybe "qemu-x86_64".

But anyway it seems like the real problem is that QtEmu was last updated in 2007. And QEMU has obviously changed since then so it doesn't work anyway (complains about not having --disable-kvm option). Bit of a shame, since QtEmu actually has a rather nice UI.

Alternatives are here: [http://wiki.qemu.org/Links#GUI_Front_Ends](http://wiki.qemu.org/Links#GUI_Front_Ends)

I tried aqemu, and it started well but crashed after the setup wizard. I guess you are right about badly written open-source software.

---

