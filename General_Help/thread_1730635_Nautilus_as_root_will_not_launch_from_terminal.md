---
title: "Nautilus as root will not launch from terminal"
date: 2011-04-16
forum: General Help
---

### Post by JohnE1 on 2011-04-16
I get the following error when I try to run Nautilus in a terminal window (regular terminal and root terminal get the same error):

$ gksudo /usr/bin/nautilus
Initializing nautilus-gdu extension
**Eel:ERROR:eel-preferences.c:117:preferences_gconf_value_get_string: assertion failed: (value->type == GCONF_VALUE_STRING)


I have also tried, gksudo 'nautilus --no-desktop', and receive the same error as above.

Any help? Thanks!

---

### Post by ~Plue on 2011-04-16
can you use nautilus as a normal user?
run
```

sudo mv /root/.gconf /root/.gconf-bak
```and try again

---

### Post by JohnE1 on 2011-04-24
> **~Plue said:**
> can you use nautilus as a normal user?
run
```

sudo mv /root/.gconf /root/.gconf-bak
```and try again

Yes, I could run it as a regular user.

After removing the existing .gconf, I was able to run nautilus as root (albeit, still with error messages).

Thanks for your help!

---

### Post by d3v1150m471c on 2011-04-24
when you use `gksudo nautilus`, in a terminal, what's the output?

edit, nvm

---

### Post by wilee-nilee on 2011-04-25
> **d3v1150m471c said:**
> when you use `gksudo nautilus`, in a terminal, what's the output?

edit, nvm

That is the command I use in the terminal or a alt-f2

---

