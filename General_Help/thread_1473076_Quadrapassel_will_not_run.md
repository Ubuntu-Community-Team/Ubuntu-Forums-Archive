---
title: "Quadrapassel will not run"
date: 2010-05-04
forum: General Help
---

### Post by denzilla on 2010-05-04
Running Lucid inside Virtualbox 3.1.6 with guest additions installed. Tried with and without effects enabled. Here is the Terminal output:

> OpenGL Warning: glXChooseFBConfigSGIX not implemented by Chromium
Failed to initialise clutter: Unable to find suitable fbconfig for the GLX context

**I won't be creating a Launchpad account to report this bug so someone else will have to if they so desire.**

**Update:** I think the problem might be caused by installing the Virtualbox Guest additions. I download a bunch of new Lucid updates today and Quadrapassel started working. I had to re-install the guest additions because the new kernel updates broke 3D support and after that, QP stopped working with the same error.

---

### Post by cong06 on 2010-06-25
It's not virtualbox, but it seems to be a hardware thing...
I have several machines, and currently I'm having issues with Dell Optiplex gx240

```

Failed to initialise clutter: Unable to find suitable fbconfig for the GLX context

```
Either they work, and no error is thrown, or most games throw this error.

---

### Post by james_xxx on 2010-10-10
Also having this problem.

This machine uses an AGP GeForce FX 5500.
It seems to have GLX enabled in xorg.conf.
This card should be able to handle this game, shouldn't it?

I am still wondering whether or not xorg.conf may need to be tweaked in some other way.

---

### Post by james_xxx on 2010-10-13
bump.

---

### Post by NightwishFan on 2010-10-13
Apparently clutter does not play well with virtualization, and that is what Quadrapassel uses to draw the game.

In virtualbox I get this error:
```
failed to create drawable
failed to initialise clutter: Unable to select the newly created GLX context
```

---

