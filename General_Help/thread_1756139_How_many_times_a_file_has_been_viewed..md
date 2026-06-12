---
title: "How many times a file has been viewed."
date: 2011-05-11
forum: General Help
---

### Post by warrior_juggalo on 2011-05-11
I was wondering if there is  any way i can tell now many times a file hqas been clicked on/viewed?

---

### Post by Lars Noodén on 2011-05-12
Not really, but the 'atime' will tell you when it was last read.

```

stat --format '%x' */somepath/somefile*

```

---

### Post by justanotherhack on 2011-05-12
You would need something to "wrap" around the files. For example, something that requires users to use a DAM or just a simple webinterface to access it.

---

