---
title: "Ubuntu 8.10 assistant-qt4 does not exist"
date: 2009-11-13
forum: General Help
---

### Post by AkiraBergman on 2009-11-13
Hello all,

I installed CLAM (C++ Library for Audio and Music) in 8.10 since the deb packages not yet available for 9.04 or 9.10. I get the following error when I press the help buttons in the Qt-Designer panel;

"The binary '/usr/bin/assistant-qt4' does not exist."

The package libqt4-assistant is installed already. I saw some relevant bugs mentioned in the net but they seem to have been resolved.

Please help.

---

### Post by AkiraBergman on 2009-11-15
While the libqt4-assistant was installed, the package qt4-designer was not installed. After installing it with the Synaptic the fault disappeared.

---

### Post by Alnico on 2010-05-24
I have 10.04 with qt4-doc & qt4-designer installed, but still the error unfortunately.

---

### Post by Wolf-Ekkehard on 2010-08-22
Alnico,

Have you ever been able to resolve this?  I am having the same issue on a DELL laptop with a freshly upgraded 10.04

---

### Post by AkiraBergman on 2010-08-22
The problem was resolved in 8-10 after installing the package qt4-designer. I have not tried CLAM with 10-04.

---

### Post by Wolf-Ekkehard on 2010-08-22
Yup - should not have upgraded.  Kdevelop is still in the "unsupported" repository.  Linguist is also missing.  Maybe I should check out the good people at KDE - they surely have got one of everything...

---

