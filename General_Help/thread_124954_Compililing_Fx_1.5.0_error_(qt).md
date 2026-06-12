---
title: "Compililing Fx 1.5.0 error (qt)"
date: 2006-02-02
forum: General Help
---

### Post by [Nirvana] on 2006-02-02
I am trying to compile Firefox with this .mozconfig file:
```
. $topsrcdir/browser/config/mozconfig
mk_add_options MOZ_CO_PROJECT=browser
ac_add_options --enable-application=browser
ac_add_options --with-distribution-id=UnofficialKubuntu.
ac_add_options --enable-svg
ac_add_options --enable-canvas
ac_add_options --disable-debug
mk_add_options MOZ_OBJDIR=./objdir
ac_add_options --enable-default-toolkit=q
```

I want it to be built with the QT toolkit as I am on Kubuntu (KDE- and I know I will get a lot of errors). I not get an error at the configure stage, where it says: 
```

checking Qt - version >= 3.2.0... no
configure: error: Qt Mozilla requires at least version 3.2.0 of Qt
```

What package do I need. I read this page: [http://developer.mozilla.org/en/docs/Linux_Build_Prerequisites](http://developer.mozilla.org/en/docs/Linux_Build_Prerequisites)  but I'd have to say it wasn't much help.

---

### Post by mlomker on 2006-02-02
Have you installed **kde-devel**?  It includes a number of qt devel packages.

---

### Post by [Nirvana] on 2006-02-04
I have the standard kde-devel pkg already, but do I need the one kde-devel-extras?

I'll try it now

---

