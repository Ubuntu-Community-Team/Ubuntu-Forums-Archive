---
title: "Have msttcorefonts been removed form repositories?"
date: 2009-11-28
forum: General Help
---

### Post by alan_uk on 2009-11-28
Using the Synaptic Package Manager I note that msttcorefonts are no longer available.  I am using Ubuntu 9.10 Can anybody confirm this?

Thanks

Alan

---

### Post by wojox on 2009-11-28
Go here and download [ubuntu-restricted-extras]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by Aearenda on 2009-11-28
It's been renamed to ttf-mscorefonts-installer, which is indeed installed by ubuntu-restricted-extras.

---

### Post by alan_uk on 2009-11-28
Thank you that was helpful including the link 

Alan

---

### Post by Virtual Liberty on 2009-11-28
[msttcorefonts]("http://packages.ubuntu.com/karmic/msttcorefonts") - not sure about Synaptic but it's still there if queried from the command line.

---

### Post by goldsniper on 2009-12-04
try this!

```
sudo gedit /var/lib/dpkg/info/ttf-mscorefonts-installer.postinst

```

change 

....use_mirror=xxxxxxxx (where xxxx is the default mirror to

....use_mirror=jaist

---

