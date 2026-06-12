---
title: "Help with inkscape terminal commands"
date: 2009-09-09
forum: General Help
---

### Post by jonian_g on 2009-09-09
I'm a developer of Humanity icons that are being tested in Ubuntu UNR Karmic and might become default (currently default in latest alpha).

I'm working with multiple svg files and I need some help.
What I want to do is:
1) Open an svg file
2) Vacuum definitions
3) Save as plain svg

I can do that from the terminal for one file:
```
inkscape -f *icon_name.svg* --vacuum-defs -l *icon_name.svg*
```
Does anyone know how I can do that with multiple files.
It's going to save me a lot of time. I can work more on creating icons than optimising filesize.

PS: If this can get more attention in another category, please feel free to move it.

---

### Post by mcduck on 2009-09-09
This should work as long as you have all the .svg files in the same directory:
```
for f in *.svg; do inkscape -f $f --vacuum-defs -l $f; done
```

---

### Post by ecmatter on 2009-09-09
Something like this, maybe?:```

for i in *.svg; do inkscape -f $i.svg --vacuum-defs -l $i.svg

```

---

### Post by ecmatter on 2009-09-09
Go with mcduck.  What I posted was wrong.

---

### Post by jonian_g on 2009-09-09
> **mcduck said:**
> This should work as long as you have all the .svg files in the same directory:
```
for f in *.svg; do inkscape -f $f --vacuum-defs -l $f; done
```

That worked like a charm man! Thanks!

Is there any way to ignore the symliks because it gives errors?

---

