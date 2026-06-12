---
title: "Python help"
date: 2009-10-05
forum: General Help
---

### Post by BluShift on 2009-10-05
Hi all,
 
Writing an e-mail software; I have no idea why this is happening.
 
```
spool=open("mail/%s", "w") % fname
```
 
It's raising a TypeError.
 
fname is defined prior; it's a string, so there should not be any issue.
 
I will update this with the specific error when I get off if necessary (I'm @ work). Til then, does anyone have any ideas?
 
Thanks much!

---

### Post by weemadarthur on 2009-10-05
> **BluShift said:**
> Hi all,
 
Writing an e-mail software; I have no idea why this is happening.
 
```
spool=open("mail/%s", "w") % fname
```It's raising a TypeError.
 
fname is defined prior; it's a string, so there should not be any issue.
 
I will update this with the specific error when I get off if necessary (I'm @ work). Til then, does anyone have any ideas?
 
Thanks much!


Change the code above to 
```
spool=open("mail/%s"  % fname, "w") 
```

---

### Post by BluShift on 2009-10-05
That did it! Thanks so much!

---

