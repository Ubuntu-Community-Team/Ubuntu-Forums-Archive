---
title: "How do I uninstall a compiled version of gimp?"
date: 2010-10-02
forum: General Help
---

### Post by Mr_VeRiTy on 2010-10-02
Hi, I compiled the latest stable version of gimp, but I want to go back to the one in the repositories, how do I uninstall the compiled version?

---

### Post by foxmulder881 on 2010-10-02
Wouldn't this work?

> sudo dpkg --purge gimp

---

### Post by Mr_VeRiTy on 2010-10-02
> **foxmulder881 said:**
> Wouldn't this work?

Not if I compiled it from source.

---

### Post by foxmulder881 on 2010-10-02
Does Synaptic see it?

Also, there should be a README file in the tarball. Check that as it may contain removal instructions.

---

### Post by Mr_VeRiTy on 2010-10-02
> **foxmulder881 said:**
> Does Synaptic see it?

Nope, synaptic only sees things that were installed as packages. I think. But I can't see it anyways.

---

### Post by mc4man on 2010-10-02
If you installed with "sudo make install" then cd back to build dir. and run "sudo make uninstall"

================================================================
if you've removed the build (source) dir. then you can manually remove, unless specified then it would have installed to /usr/local/*
(usr/local/bin, /usr/local/share, ect. ect.

(you could also rebuild the gimp source as before, run a sudo make install followed by a sudo make uninstall

---

### Post by Mr_VeRiTy on 2010-10-02
> **mc4man said:**
> If you installed with "sudo make install" then cd back to build dir. and run "sudo make uninstall"

================================================================
if you've removed the build (source) dir. then you can manually remove, unless specified then it would have installed to /usr/local/*
(usr/local/bin, /usr/local/share, ect. ect.

(you could also rebuild the gimp source as before, run a sudo make install followed by a sudo make uninstall

I still had the source in a folder, so "sudo make uninstall" worked. Thanks :)

---

