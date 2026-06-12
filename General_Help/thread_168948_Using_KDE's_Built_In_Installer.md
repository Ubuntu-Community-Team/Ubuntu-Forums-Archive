---
title: "Using KDE's Built In Installer"
date: 2006-05-01
forum: General Help
---

### Post by chris062689 on 2006-05-01
There is a list of programs that I can install, and I hear it is bad to use this because the dependencies never get removed after the install,  is there a program that manages these flaws?

---

### Post by aysiu on 2006-05-01
*kubuntu-desktop* and *kde* are metapackages, which basically means they're pointers to other, real packages.

If you use Synaptic, Add Applications, or *apt-get* to install either *kubuntu-desktop* or *kde*, you won't be able to easily remove the packages they point to--only the pointers themselves.

If you use *aptitude*, however, it'll keep track of what dependencies (what's being pointed to) get installed along with the metapackage itself (the pointer):

**Do this**:
```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

**Do _not_ do this**:
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

---

### Post by ComplexNumber on 2006-05-01
**[B]> KDE's Built In Installer**
[/B]if you're referring to kpackage, you would be right in thinking that its bad to use it. its hopelessly buggy and unstable and always has been. i tried it in suse a few weeks ago and i tried it at various times using mandrake way back as far as version 7.2 (i think), and its always been unstable and buggy with frequent crashing (where its just exited or siezed up).
you've be better off using something like kyum or something.

---

### Post by aysiu on 2006-05-01
Oh, yeah--that's probably what chris062689 was referring to.

I would always prefer Synaptic and GDebi to Adept and KPackage... and I'm a KDE user!

---

### Post by ComplexNumber on 2006-05-01
[quote=aysiu]Oh, yeah--that's probably what chris062689 was referring to.

I would always prefer Synaptic and GDebi to Adept and KPackage... and I'm a KDE user![/quote]
i personally use Smart, but thats a gtk application. its amongst the best i've ever used.

---

### Post by jeremy on 2006-05-04
I use synaptic in KDE, can't stand adept!

---

