---
title: "Using the filename in Nautilus 'Open With...' commands"
date: 2006-02-20
forum: General Help
---

### Post by jnoreiko on 2006-02-20
I'm trying to add a new action to the 'Open With...' list in Nautilus.
Looking at the 'custom command' section, how do I refer to the particular file in that?

Eg, I want to add an action 
```
gnome-terminal -e "more (file)"
```

I tried $1 like in shell scripts and that didn't work.

---

### Post by dcstar on 2006-02-20
[QUOTE=jnoreiko]I'm trying to add a new action to the 'Open With...' list in Nautilus.
Looking at the 'custom command' section, how do I refer to the particular file in that?

Eg, I want to add an action 
```
gnome-terminal -e "more (file)"
```

I tried $1 like in shell scripts and that didn't work.[/QUOTE]
I believe that %U is a URL list, %f a single file, this list should explain the rest:

[http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html)

---

### Post by jnoreiko on 2006-02-20
It works.
Thanks! :)

---

