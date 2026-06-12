---
title: "Executing multiple commands at the same time and.."
date: 2011-12-15
forum: General Help
---

### Post by the_X_files on 2011-12-15
For example
scriptA agument1; scriptB agument1
scriptA agument2; scriptB agument2
scriptA agument3; scriptB agument3
scriptA agument3; scriptB agument3
....

I want to start all the **scriptA** scripts at the same time and when **scriptA** with argument argumentN finishes I want to execute **scriptB** argumentN.
Is that possible in bash?

---

### Post by gmargo on 2011-12-15
Using subshells: 
```

( scriptA agument1; scriptB agument1 ) &
( scriptA agument2; scriptB agument2 ) &
( scriptA agument3; scriptB agument3 ) &
( scriptA agument3; scriptB agument3 ) &

```Then add a "wait" if you want to wait until every pipeline is finished.

---

### Post by the_X_files on 2011-12-15
Great! That is exactly what I needed. Thank you! :)

---

