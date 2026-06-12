---
title: "Firefox 3.0.12 not compiled with --enable-system-cairo?"
date: 2009-07-23
forum: General Help
---

### Post by steppres on 2009-07-23
I just upgraded Firefox 3 to version 3.0.12 and noticed my fonts are a bit messed up now.I checked out about:buildconfig and noticed --enable-system-cairo wasn't in the build options, so FF3 seems to just use the default gnome settings and not fontconfig.

Any ideas how I can change this without recompiling? Why is --enable-system-cairo turned off anyway?

---

### Post by kpkeerthi on 2009-07-23
Thats bad. Please [file a bug report]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+filebug").

---

### Post by lovinglinux on 2009-07-23
Thanks for the tip.

---

### Post by kpkeerthi on 2009-07-24
lovinglinux,
Are you the maintainer of this package?

---

### Post by anarchyinc on 2009-07-24
Firefox is up to 3.5.1 why not just get that?

---

### Post by lovinglinux on 2009-07-24
> **kpkeerthi said:**
> lovinglinux,
Are you the maintainer of this package?

Nope. I just compile it for myself. I should rephrase my previous post :)

---

### Post by kpkeerthi on 2009-07-24
> **lovinglinux said:**
> Nope. I just compile it for myself. I should rephrase my previous post :)

:) ok.. I was about to ask you to update the package in the repository.

---

### Post by kpkeerthi on 2009-07-24
> **anarchyinc said:**
> Firefox is up to 3.5.1 why not just get that?

because it still renders the fonts ugly.

---

### Post by kpkeerthi on 2009-07-24
Just upgraded to 3.0.12. Fonts are fine for me.

---

