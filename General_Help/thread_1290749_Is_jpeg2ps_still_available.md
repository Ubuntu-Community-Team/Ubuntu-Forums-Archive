---
title: "Is jpeg2ps still available?"
date: 2009-10-13
forum: General Help
---

### Post by syrex314 on 2009-10-13
I'm trying to convert a jpeg to .eps for including in a LaTeX document. I thought jpeg2ps was the package to get the job done, but apt-get couldn't find a package by that name. What happened? Is it included in another package now?

---

### Post by ramjet_1953 on 2009-10-13
Follow this link:

[COLOR="Blue"]http://www.pdflib.com/download/free-software/jpeg2ps/[/COLOR]

Regards,
Roger :)

---

### Post by KeyserSoze93 on 2009-10-14
Well, you could use imagemagick...

```
apt-get install imagemagick
```

and then

```
convert blah.jpg blah.eps
```

should work.

---

