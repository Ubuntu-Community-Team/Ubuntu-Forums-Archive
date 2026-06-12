---
title: "unity launch bar always on top"
date: 2011-11-01
forum: General Help
---

### Post by Cozze on 2011-11-01
I would like to have the launch bar always on top, even when a program is open. Anyone an idea?

---

### Post by ~!geek!~ on 2011-11-01
> **Cozze said:**
> I would like to have the launch bar always on top, even when a program is open. Anyone an idea?

 Open CCSM (install it if you don't have already)-> select ubuntu unity Plugin -> in Behaviour tab change Hide launcher option to Never...

---

### Post by mjuhasz on 2011-11-01
You can also do it in gconf-editor, set the value '0' to this key:
/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode

---

### Post by Cozze on 2011-11-01
Tx mjuhasz, that was an easy one:popcorn:

---

