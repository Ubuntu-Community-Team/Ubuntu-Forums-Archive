---
title: "How to re-install original drivers?"
date: 2006-02-08
forum: General Help
---

### Post by equal on 2006-02-08
I have an Audigy 2 sound card from Creative. It auto-detects and installs no problem on installing Ubuntu. Problem is, I installed OSS, and now it doesn't work. Is there a simple way to make the computer go back to it's original drivers?

---

### Post by nanotube on 2006-02-08
uninstall OSS ?

---

### Post by az on 2006-02-08
Let's say that I lose my head and recompile ndiswrapper.  The, I realise that I didn't really need it and way to revert back to the one that shipps with ubuntu. I would

1.  delete the ndiswrapper.ko module that I compiled myself.
2.  Reinstall the kernel, which will rewrite the modules that originally came with it.

sudo apt-get install --reinstall linux-image-2.6.15-14-k7

(Use whatever versino of the kernel you are running at the moment)

---

