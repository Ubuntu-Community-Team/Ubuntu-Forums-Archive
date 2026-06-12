---
title: "Unmet Dependency when upgrade kernel from 2.6.32-23 to 2.6.32-24"
date: 2010-07-24
forum: General Help
---

### Post by cHayanKs on 2010-07-24
Please help me... i have serious problem when try to upgrade the kernel header from 2.6.32-23 to 2.6.32-24... it say unmet depedency. How do i fix that.... please help

---

### Post by neoargon on 2010-07-24
Use an application named "aptitude" to upgrade . Type in terminal aptitude . terminal can be found at applications->accessories . aptitude will tell what is wrong in detail . ```
sudo aptitude install <name off package to be upgraded>

```

You might have enabled a software source(repository) that isn't official . That repository might contain a package that linux kernel depends . that package might have unmet dependencies . That can be the reason . Enable only official repositories . That might solve the issue

Any more help?

---

