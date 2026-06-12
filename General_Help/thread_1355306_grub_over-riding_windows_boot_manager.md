---
title: "grub over-riding windows boot manager"
date: 2009-12-14
forum: General Help
---

### Post by garfieldwasacat on 2009-12-14
Hey all,

I have both Ubuntu and Windows 7 installed on two separate partitions and I would like to be able to manually choose which to boot up to on each startup.

But grub is booting directly into Ubuntu.

Is there a way which allows windows boot manager to do the choosing?

Thanks in advance

---

### Post by oldfred on 2009-12-14
Grub boots straight into Ubuntu if it is the only operating system it found. Sometimes grub does not find windows the first time. Was windows working before you installed?

try:
sudo update-grub

---

