---
title: "Ports in use"
date: 2010-08-03
forum: General Help
---

### Post by ivanp on 2010-08-03
I've a JBoss AS installed in my ubuntu 10. It was working some days ago, but since updated the box with synaptic requests, I can't start the server. Every port it tries to open will complain it is in use. But a netstat shows th port is no in use:

```
netstat -na | grep 8083
```

I don't have any firewall installed. Any ideas on how to solve this?

---

