---
title: "SCIM problem"
date: 2009-10-10
forum: General Help
---

### Post by lgjsheron on 2009-10-10
I'm using ubuntu 9.04. I don't no how is starts. But it starts automatically when i open a new application or at the start-up of ubuntu. It's annoying, when i type in English it change the keyboard layout and type some other language. Is any one know to to disable or fix this thing.

---

### Post by Irihapeti on 2009-10-11
Scim gets triggered by pressing ctrl-space, which is easy enough to do accidentally.

If you don't want to use Scim at all, you can turn it off by doing the following command in a terminal:

```
im-switch -z (your locale) -s none
```

DON'T use sudo for this, or you get an error message.

To check what your locale is, do this in a terminal:
```
locale | grep LANG=
```

and you should see something that looks like
```
LANG=en_NZ.UTF-8
```

The bit after the "=" is your locale. Unless you live in New Zealand, yours will probably be different from mine.

---

