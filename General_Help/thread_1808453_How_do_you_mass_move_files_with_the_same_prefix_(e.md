---
title: "How do you mass move files with the same prefix (ex., prefix_numbers), in terminal?"
date: 2011-07-20
forum: General Help
---

### Post by fertileneutrino on 2011-07-20
i have a bunch of files that share the same prefix but then change after an underscore. example is

qpid_ac1
qpid_ac2

etc.

is there something i can tag onto the end of "qpid_" that will effectively grab all the like files when moving them to another directory? maybe '*' or something similar?

thanks,

fertileneutrino

---

### Post by karlson on 2011-07-20
> **fertileneutrino said:**
> i have a bunch of files that share the same prefix but then change after an underscore. example is

qpid_ac1
qpid_ac2

etc.

is there something i can tag onto the end of "qpid_" that will effectively grab all the like files when moving them to another directory? maybe '*' or something similar?

thanks,

fertileneutrino

If the files in the same directory then:

```

mv qpid_* <target>

```

---

### Post by fertileneutrino on 2011-07-20
thanks! solved!

---

### Post by alphaamanitin on 2011-07-20
Please mark your thread solved.  I believe it is in the thread tools section.

AlphaA

---

