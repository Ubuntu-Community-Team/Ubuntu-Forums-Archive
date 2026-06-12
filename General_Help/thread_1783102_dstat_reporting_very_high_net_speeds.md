---
title: "dstat reporting very high net speeds"
date: 2011-06-15
forum: General Help
---

### Post by Lazaruss on 2011-06-15
I have indicator-sysmonitor installed which runs a script to display my network speeds. I apparantly average 4096MiB/s, which really would be nice, but somehow I doubt it. The problem is coming from dstat, which reads speeds of 12GiB/s. I'm not sure whether this is a bug, or just an issue with my setup, any help?

```
samuel@samuel-Lenovo-B560:~$ dstat --net
-net/total-
 recv  send
   0     0 
  12G   12G
8192M 8192M
4096M 4096M
  12G   12G
8192M 8192M
4096M 4096M
  16G   16G
8192M 8192M
4096M 4096M
  12G   12G
8192M 8192M
4096M 4096M
  12G   12G
8192M 8192M
4096M 4096M
  12G   12G
  12G   12G
4096M 4096M
4096M 4096M
  12G   12G
```

---

