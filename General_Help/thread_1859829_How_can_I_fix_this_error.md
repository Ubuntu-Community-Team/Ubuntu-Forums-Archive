---
title: "How can I fix this error"
date: 2011-10-14
forum: General Help
---

### Post by nguyenabcd on 2011-10-14
I want to install liblinear. The first step I type make. It is oK, but the second step I get the follow error.
How can I fix it?

---

### Post by squaregoldfish on 2011-10-14
It looks like your build environment isn't set up properly, as you don't have a g++ compiler installed. Have you installed the build-essential package? This should put in most, if not all, of the bits you need.

Steve.

---

### Post by mixmastamyk on 2011-10-14
```

sudo apt-get install build-essential

```

---

### Post by nguyenabcd on 2011-10-15
Thank. 
I installed build -essential and obtain tow executable file. But I still get error: 
```

ERROR: Init file not found (/home/nguyen/.train//train.ini).

```

What can I do next

---

