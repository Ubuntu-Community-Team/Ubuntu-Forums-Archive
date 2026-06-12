---
title: "need help with conky ${if_match}"
date: 2010-10-15
forum: General Help
---

### Post by matt.rebo. on 2010-10-15
hi, im trying to make ${if_match} work with ${totaldown ppp0} hopefully some of you conky experts can help.

im just trying to get a correct return for something like

```
${if_match ${totaldown ppp0} >5M}${color green}${else}${color black}${endif}=
```

so that if true for the session i can flag it as green and onwards, problem is thinks everything is true even if "${totaldown ppp0}" returns something like "3.2K", i know that when the value increases it's expresses as something like "1.68M" etc

ive tried

```
${if_match "${totaldown ppp0"} >"5M"}
and
${if_match "${totaldown ppp0"} >"5.00M"}

```

but still returns everything as true! TIA for any tips or tricks you can offer.

---

### Post by matt.rebo. on 2010-10-15
fixed and marked as solved!

---

