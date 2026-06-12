---
title: "how to close unity-sco"
date: 2012-10-08
forum: General Help
---

### Post by tonysky2008 on 2012-10-08
I use lsof -i:80, and find there are two services are occupy 80 port.
it shows as below:
unity-sco 2123 tt 12u ipv4 18430 0t0  tt.local:32869:alkes.canonical.com:http(ESTABLISHED)
unity-sco 2123 tt 14u ipv4 18431 0t0  tt.local:32870:alkes.canonical.com:http(ESTABLISHED)
if I use kill 2123, then another two processes would be created.
how should I close these two unity-sco.

---

