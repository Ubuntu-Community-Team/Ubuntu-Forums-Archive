---
title: "Reset gnome to default values"
date: 2009-11-16
forum: General Help
---

### Post by andreseso on 2009-11-16
Hello,

I have been using Ubuntu since Edgy having to do several reinstalls due to problems with either X or with Grub with successive upgrades.  I believe my gnome dot files are obsolete as the gnome panel freezes often.  I want to reset gnome to its default state so I will have to delete all the existing configuration.

What do I need to delete?

Love,
Andres

---

### Post by pmlxuser on 2009-11-16
usualy gnome config files are in folders ~/.gnome2* and .gconf and .gconfid

deleting these hidden folders will give you the default configuration after login out and then in

```

rm -r gnome2* gconf gconfd

```

---

