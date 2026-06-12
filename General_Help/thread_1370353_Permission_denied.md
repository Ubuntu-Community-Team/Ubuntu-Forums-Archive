---
title: "Permission denied"
date: 2010-01-02
forum: General Help
---

### Post by anilriazi on 2010-01-02
Dear all
My linux is Kubuntu 9.04, I encountered Permission denied problem when I wanted to install the openscientist source file (osc_batch_source_16.9) in the following order.

1)
cd  OpenScientist/16.9/osc_batch/16.9/obuild

2)
source setup.sh
3)
./sh/build
in this step  Permission denied  message appeared.

would you mind help me to solve this problem

thanks a lot

---

### Post by nothingspecial on 2010-01-02
```
chmod a+x sh/build
```

to make it executable.

---

