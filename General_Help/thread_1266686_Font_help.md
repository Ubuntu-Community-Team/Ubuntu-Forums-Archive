---
title: "Font help"
date: 2009-09-14
forum: General Help
---

### Post by Lyerae on 2009-09-14
How do I install fonts for GIMP?
Thanks for any help.

---

### Post by blackened on 2009-09-14
GIMP uses your regular system fonts. To install a new font on your system you can use two methods: the repos, from which there are a few extra packages, msttcorefonts to name one; or download font files from the web and place them in either /usr/share/fonts (for global use) or ~/.fonts (for single-user). Restart the GIMP and they should be available.

---

### Post by ecmatter on 2009-09-14
After adding fonts to ~/.fonts, you'll need to run the following command to make them  available in gimp (or any other program):

```

sudo fc-cache -fv

```

---

### Post by Lyerae on 2009-09-15
Thanks!

---

### Post by mcduck on 2009-09-15
> **ecmatter said:**
> After adding fonts to ~/.fonts, you'll need to run the following command to make them  available in gimp (or any other program):

```

sudo fc-cache -fv

```

Actually I've never had to do that, the new fonts have always worked simply bu dropping them into ~/.fonts.

Some programs may require logging out and back again before the now fonts are recognized.

---

### Post by blackened on 2009-09-15
> **mcduck said:**
> Actually I've never had to do that, the new fonts have always worked simply bu dropping them into ~/.fonts.

Some programs may require logging out and back again before the now fonts are recognized.

Aye, same here. I don't remember ever having had to refresh the font cache.

---

