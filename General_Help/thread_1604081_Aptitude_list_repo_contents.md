---
title: "Aptitude list repo contents?"
date: 2010-10-23
forum: General Help
---

### Post by spoovy on 2010-10-23
Is is possible to use aptitude to list contents of a particular repo?  Something like

```
aptitude search --repo-universe | grep prism
```

The --repo option doesn't exist, but it would be exactly what I want.

Cheers

---

### Post by gmargo on 2010-10-23
I don't know of a convenient option like that, but all the files live in /var/lib/apt/lists/ and can be easily grepped.

To list of all packages in universe:
```

cd /var/lib/apt/lists
cat *universe*Packages | grep "^Package: " | sed 's/^Package: //' | sort -u

```

---

### Post by spoovy on 2010-10-24
That'll do!  Thanks

---

