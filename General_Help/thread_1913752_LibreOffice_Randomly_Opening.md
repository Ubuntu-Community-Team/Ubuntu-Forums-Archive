---
title: "LibreOffice Randomly Opening"
date: 2012-01-23
forum: General Help
---

### Post by bigoops on 2012-01-23
Hey folks,
Ever since I re-installed Libreoffice yesterday its been randomly (yes, completely random) opening on its own (from what I can tell).

I've deleted my configuration for it just incase it was corrupt (~/.libreoffice/) and I've reinstalled again aswell. 
I've killed the libreoffice processes but it still happens. 
I've checked my MIMES but theres nothing out of the ordinary there.

Please help. ](*,)

---

### Post by dargaud on 2012-01-23
Check the following:
```
crontab -l
ps faux
```

---

### Post by bigoops on 2012-01-23
yeah, I've checked it using ps aux | grep -i office

and theres no libre processes. but it opens up randomly

and I have no crontabs.

---

### Post by bigoops on 2012-01-23
:-? Bump.

Nobody knows anything about this?

---

### Post by castironpants on 2012-02-09
Same problem.

It seems to only open when I open/have open Spotify (the beta) or Epiphany Browser

---

