---
title: "GTK+ Programming by Peter Wright"
date: 2011-06-17
forum: General Help
---

### Post by linux_trojan on 2011-06-17
A few years ago I bought the book GTK+ Programming by Peter Wright.  Back then everything worked fine.  But now I cant compile any programms.  I use

$ gcc -Wall -o intro intro.c `gtk-config --cflags --libs`

I get tons of errors, like "No command gtk-config found"

Have things changed that much?

---

### Post by linux_trojan on 2011-06-17
Any ideas on how I can get these programs running again?

---

### Post by WorMzy on 2011-06-17
Use pkg-config, not gtk-config. If that was just a typo and you don't have pkg-config, you can install it by running this command:
```
sudo apt-get install pkg-config
```

Also, you need to specify which libraries you're trying to find.

e.g.
```
gcc -Wall -o intro intro.c `pkg-config --cflags --libs gtk+-2.0`
```

---

### Post by ohadcn on 2011-06-17
try
sudo apt-get install libgts-bin
this pakage contain the gtk-config command

---

### Post by WorMzy on 2011-06-17
> **ohadcn said:**
> try
sudo apt-get install libgts-bin
this pakage contain the gtk-config command

It contains gts-config, not gtk-config. gtk-config doesn't exist in any Ubuntu package.

---

