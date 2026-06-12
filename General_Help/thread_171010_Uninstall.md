---
title: "Uninstall"
date: 2006-05-05
forum: General Help
---

### Post by sinkxdie on 2006-05-05
I like**d** Gnome, but now it's not "sleek" enough for me.
So I installed KDE, it's very good and I like it, but one problem...

I have about 100MB's space left after I installed KDE, and am wondering how would I be able to uninstall Gnome, but keep configuration settings if I ever decide to use it again.

Thanks.

---

### Post by hw-tph on 2006-05-05
I am actually not sure if this will work properly, but try aptitude instead of apt-get or synaptic. **sudo aptitude remove ubuntu-desktop** should remove all the Gnome desktop applications while your settings, stored in dotfiles in your home directory, remain untouched.

I know this works if you installed kubuntu-desktop using aptitude but, like I mentioned, I am not sure it works if ubuntu-desktop was installed by default (or by other means like apt-get or synaptic).

Håkan

---

