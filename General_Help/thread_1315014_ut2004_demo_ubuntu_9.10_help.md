---
title: "ut2004 demo ubuntu 9.10 help"
date: 2009-11-04
forum: General Help
---

### Post by JigglyWiggly_ on 2009-11-04
So I installed the ut2004 demo, it installed fine, however I can't play it. When I do ./ut2004-bin I get:
```
erro r while loading shared libraries: libstdc++.so.5: cannot open shared object file: NO such file or directory
```

So then I assumed I just didn't have the gcc compiler, which I was right I didn't
sudo apt-get install build-essential, ok that went fine...
same error though, so then I looked at the synaptic package manager and typed libstdc++ and I found a lot of them but they are all 6.4.x, I need an old version.

Any ideas?

---

