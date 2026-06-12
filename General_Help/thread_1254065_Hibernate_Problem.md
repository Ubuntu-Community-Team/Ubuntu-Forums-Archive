---
title: "Hibernate Problem"
date: 2009-08-30
forum: General Help
---

### Post by Vishnu V on 2009-08-30
Hibernate option is not working properly.It just fades the screen then it restarts my system. Pls help me to solve this

---

### Post by uylug on 2009-08-30
A friend of mine had the same issue. It was solved after downloading the updates. Just thought I'd mention.

---

### Post by JC Cheloven on 2009-08-30
In order to hibernate, it is recommended to have twice as swap as your ram memory.
Do you have that?

---

### Post by Vishnu V on 2009-08-30
i have 
1GB ram
1.91GB swap 
Is this sufficient to hibernate ?

---

### Post by JC Cheloven on 2009-08-31
> **Vishnu V said:**
> i have 
1GB ram
1.91GB swap 
Is this sufficient to hibernate ?
It should be, actually. The general recommendation is 1.5~2 times your ram.
Some systems don't hibernate well, depending on their hardware (acpi compliance and related problems, see [here]("https://help.ubuntu.com/community/PowerManagement/Overview")). Perhaps it's the case :(

Many posts are in this forums about hibernation. I'd suggest you to do a search. Also posting your system specs could help someone to give you more hints. I don't hibernate, so I'm not an expert on this matter, sorry.

BTW, with a system as jaunty on ext4, which is up and running in 35sec, I don't miss hibernation ;-)

---

