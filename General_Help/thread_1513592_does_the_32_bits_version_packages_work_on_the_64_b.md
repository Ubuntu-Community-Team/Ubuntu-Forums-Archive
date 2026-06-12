---
title: "does the 32 bits version packages work on the 64 bits edition of ubuntu?"
date: 2010-06-19
forum: General Help
---

### Post by Elie-M on 2010-06-19
okay here's the thing:

when I reformat ubuntu, I use AptonCD to save packages and then restore them without downloading anything over again. what I want to know is:

I have the 32 bits ubuntu installed and then I downloaded the 64 bits version. If i reformat to the 64 bits one, would the DVD saved aptoncd packages from the 32 bits work on the 64 bits installation?

---

### Post by oldos2er on 2010-06-19
Yes, 32-bit software will run on 64-bit Ubuntu, but IMO that would defeat the purpose of running a 64-bit OS.

---

### Post by Elie-M on 2010-06-19
well u're right, but that would mean that every package has an equivalent 64 bits in synaptic ready to be used on the 64 bits ubuntu?

---

### Post by dcstar on 2010-06-20
> **Elie-M said:**
> 
........
I have the 32 bits ubuntu installed and then I downloaded the 64 bits version. If i reformat to the 64 bits one, would the DVD saved aptoncd packages from the 32 bits work on the 64 bits installation?

No. 64-bit software is compiled for that kernel architecture and 32-bit is complied for 32-bit kernels.

There are ways to get some 32-bit packages working on 64-bit (like Adobe Flash) but in general these have issues in comparison to native 64-bit software.

Most packages in repositories are kept as separate 32 and 64-bit versions, if you don't also have the 64-bit version on the APT DVD then they won't be available.

---

### Post by Elie-M on 2010-06-20
okay thx for your input

---

