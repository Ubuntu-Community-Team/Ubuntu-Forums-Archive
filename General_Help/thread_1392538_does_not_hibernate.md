---
title: "does not hibernate"
date: 2010-01-28
forum: General Help
---

### Post by frriction on 2010-01-28
well i have installed ubuntu karmic 64 bit in my dell studio laptop it is running very smoothly but it does not hibernate upon low battery any one can help with this

---

### Post by rnerwein on 2010-01-28
hi
just a question - is your ram same size or bigger than your swap partition.
type: free on a commandline to figure it out (or post the output )
ciao

---

### Post by frriction on 2010-01-28
my ram is about 4gig and swap is about 1.5 gig

---

### Post by audiomick on 2010-01-28
That is why your hibernate wont work. Hibernate writes the contents of RAM to the swap partition, so the swap space has to be as big as RAM for it to work.

---

### Post by frriction on 2010-01-28
but when i hibernate manually it does why is so??????

---

### Post by audiomick on 2010-01-28
> **frriction said:**
> but when i hibernate manually it does why is so??????

Oh... Sorry, that is beyond me.
I hope someone else can help.

---

### Post by frriction on 2010-01-28
> **audiomick said:**
> Oh... Sorry, that is beyond me.
I hope someone else can help.

 Thank you anyway for suggestions

---

