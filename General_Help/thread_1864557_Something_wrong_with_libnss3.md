---
title: "Something wrong with libnss3"
date: 2011-10-19
forum: General Help
---

### Post by PatrickZ on 2011-10-19
The thing is, I have some trouble with my wireless network connection which led me to fiddle about with the libnss3 package. Of course I shouldn't have done that with my lacking expertise... Anyway there's something not right with the libnss3 package now: if I try to reinstall it in synaptic - it is marked as installed - I get "E: Internal Error, No file name for libnss3". 
What to do?

---

### Post by TeoBigusGeekus on 2011-10-19
Try these commands:
```
sudo apt-get install -f
sudo apt-get clean
sudo apt-get update
```

---

### Post by PatrickZ on 2011-10-19
I tried but it synaptic still comes up with the same thing.

---

